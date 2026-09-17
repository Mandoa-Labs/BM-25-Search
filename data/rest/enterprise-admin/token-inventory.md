# REST API endpoints for enterprise credential inventory

Use the REST API to list, inspect, and export credentials associated with your enterprise.

> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## List enterprise token inventory

```
GET /enterprises/{enterprise}/credentials
```

Lists an enterprise's credential inventory: both credentials currently authorized to access the enterprise and credentials owned by enterprise members that have no current enterprise authorization. Covers personal access tokens (classic and fine-grained), OAuth App and GitHub App user tokens, SSH keys, GitHub App installations, and federated credentials, assembled on demand from the canonical sources. Results are paginated with an opaque cursor via the Link header; there is no total count.
You must be an enterprise owner (or hold a role with the "View enterprise credentials" permission) to use this endpoint.
OAuth app tokens and personal access tokens (classic) require the read:enterprise scope to access this endpoint.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`after`** (string)
  A cursor, as given in the Link header, for the next page of results.

- **`token_types`** (string)
  A comma-separated list of credential types to filter by.

- **`authorization_state`** (string)
  Filter by enterprise-access status.
  Can be one of: `currently_authorized`, `member_owned_only`

- **`owner`** (string)
  Filter to credentials owned by this user, given as a login.

- **`organization`** (string)
  Filter to credentials authorized to this organization in the enterprise, given as a login.

- **`application`** (string)
  Filter to credentials for this application, given as a GitHub App slug or an OAuth App client id.

### HTTP response status codes

- **200** - OK

- **404** - Resource not found

- **422** - Validation failed

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/credentials
```

**Response schema (Status: 200):**

Array of `Enterprise Token Inventory Item`:
  * `inventory_id`: required, string
  * `credential_id`: integer or null
  * `hashed_token`: string or null
  * `fingerprint`: string or null
  * `item_type`: required, string, enum: `credential`, `token_issuer_principal`
  * `credential_type`: required, string, enum: `classic_pat`, `oauth_app_user_token`, `github_app_user_token`, `fine_grained_pat`, `ssh_key`, `github_app_installation`, `federated_jti`
  * `display_name`: string or null
  * `owner`: object or null:
    * `id`: integer
    * `login`: string
    * `name`: string or null
  * `owner_type`: string or null, enum: `user`, `oauth_application`, `github_app`, `null`
  * `application`: object or null:
    * `id`: integer
    * `name`: string or null
  * `credential_state`: required, string, enum: `active`, `expired`, `revoked`, `deleted`
  * `authorization_state`: required, string, enum: `currently_authorized`, `member_owned_only`
  * `effective_access_state`: required, string, enum: `effective`, `not_effective`, `unknown`
  * `state_reason`: string or null
  * `created_at`: string or null, format: date-time
  * `last_used_at`: string or null, format: date-time
  * `expires_at`: string or null, format: date-time
  * `next_expires_at`: string or null, format: date-time
  * `credential_instance_count`: integer or null
  * `enterprise_authorized`: required, boolean
  * `authorization_count`: required, integer
  * `authorized_organizations`: required, array of objects:
    * `id`: integer
    * `login`: string
  * `age_days`: integer or null
  * `never_expires`: boolean
  * `past_expiration_policy`: boolean or null
  * `past_expiration_policy_basis`: string or null, enum: `enforced_limit`, `proposed_baseline`, `null`
  * `expiry_unknown`: boolean
  * `scopes`: array of string or null
  * `permissions`: object or null, additional properties: string
  * `repository_selection`: string or null, enum: `all`, `subset`, `none`, `null`

## Create an enterprise token inventory export

```
POST /enterprises/{enterprise}/credentials/exports
```

Starts an asynchronous CSV export of the enterprise token inventory and returns an opaque export id to poll. Limited to a small number of exports per enterprise per day.
The generated file is UTF-8 CSV with a header row, using RFC 4180 field quoting and escaping and LF (\n) line endings. Timestamps are ISO-8601 in UTC (for example, 2026-09-15T12:00:00Z). An empty cell means the value is null or unknown, never false. Multi-value cells join their entries with ;  — this includes scopes and permissions, where each permission is encoded as a resource:action pair (for example, contents:write; issues:read). The file has one row per (credential, authorizing organization); the credential columns repeat while organization_id and organization vary, and a credential with no organization grant appears once with empty organization columns. authorization_count is the credential's total number of organization authorizations across the enterprise, plus one when enterprise_authorized is true, independent of any filters applied to the export. credential_id is a raw source-table id that can collide across credential types, so it is unique only together with credential_type, and only for the types that populate it (classic and fine-grained PATs, OAuth and GitHub App user tokens); SSH keys are keyed by fingerprint, while GitHub App installations and federated JTIs have no unique per-row column. owner_type (user, oauth_application, or github_app) disambiguates the id space of owner_id. expiry_status is expires, never, or unknown — unknown marks a credential whose expiration could not be determined, so a blank expires_at is never mistaken for one that never expires.
You must be an enterprise owner (or hold a role with the "View enterprise credentials" permission) to use this endpoint.
OAuth app tokens and personal access tokens (classic) require the read:enterprise scope to access this endpoint.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

#### Body parameters

- **`token_types`** (array of strings)
  The credential types to include.

- **`authorization_state`** (string)
  Filter by enterprise-access status.
  Can be one of: `currently_authorized`, `member_owned_only`

- **`owner`** (string)
  Filter to credentials owned by this user, given as a login.

- **`organization`** (string)
  Filter to credentials authorized to this organization in the enterprise, given as a login.

- **`application`** (string)
  Filter to credentials for this application, given as a GitHub App slug or an OAuth App client id.

### HTTP response status codes

- **202** - Accepted

- **404** - Resource not found

- **422** - Validation failed

- **429** - Too many requests

- **500** - Internal error, for example the export job could not be enqueued.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/enterprises/ENTERPRISE/credentials/exports \
  -d '{
  "owner": "octocat"
}'
```

**Response schema (Status: 202):**

* `export_id`: required, string
* `status`: required, string, enum: `pending`, `queued`, `started`, `success`, `error`
* `as_of`: string or null

## Get an enterprise token inventory export

```
GET /enterprises/{enterprise}/credentials/exports/{export_id}
```

Returns the status of an enterprise token inventory export. Once the export is ready this redirects to a short-lived URL to download the CSV.
You must be an enterprise owner (or hold a role with the "View enterprise credentials" permission) to use this endpoint.
OAuth app tokens and personal access tokens (classic) require the read:enterprise scope to access this endpoint.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

- **`export_id`** (string) (required)
  The opaque id of the export, as returned when it was created.

### HTTP response status codes

- **200** - OK

- **302** - The export is ready; redirects to a short-lived download URL.

- **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/credentials/exports/EXPORT_ID
```

**Response schema (Status: 200):**

Same response schema as [Create an enterprise token inventory export](#create-an-enterprise-token-inventory-export).

## Get an enterprise token inventory item

```
GET /enterprises/{enterprise}/credentials/{inventory_id}
```

Returns a single credential from the enterprise token inventory. Use the opaque inventory_id returned by the list endpoint for the same enterprise.
You must be an enterprise owner (or hold a role with the "View enterprise credentials" permission) to use this endpoint.
OAuth app tokens and personal access tokens (classic) require the read:enterprise scope to access this endpoint.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

- **`inventory_id`** (string) (required)
  The opaque inventory_id returned by the list endpoint for this enterprise. Pass it unchanged. Its value can differ for the same credential between responses.

### HTTP response status codes

- **200** - OK

- **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/credentials/INVENTORY_ID
```

**Response schema (Status: 200):**

* `inventory_id`: required, string
* `credential_id`: integer or null
* `hashed_token`: string or null
* `fingerprint`: string or null
* `item_type`: required, string, enum: `credential`, `token_issuer_principal`
* `credential_type`: required, string, enum: `classic_pat`, `oauth_app_user_token`, `github_app_user_token`, `fine_grained_pat`, `ssh_key`, `github_app_installation`, `federated_jti`
* `display_name`: string or null
* `owner`: object or null:
  * `id`: integer
  * `login`: string
  * `name`: string or null
* `owner_type`: string or null, enum: `user`, `oauth_application`, `github_app`, `null`
* `application`: object or null:
  * `id`: integer
  * `name`: string or null
* `credential_state`: required, string, enum: `active`, `expired`, `revoked`, `deleted`
* `authorization_state`: required, string, enum: `currently_authorized`, `member_owned_only`
* `effective_access_state`: required, string, enum: `effective`, `not_effective`, `unknown`
* `state_reason`: string or null
* `created_at`: string or null, format: date-time
* `last_used_at`: string or null, format: date-time
* `expires_at`: string or null, format: date-time
* `next_expires_at`: string or null, format: date-time
* `credential_instance_count`: integer or null
* `enterprise_authorized`: required, boolean
* `authorization_count`: required, integer
* `authorized_organizations`: required, array of objects:
  * `id`: integer
  * `login`: string
* `age_days`: integer or null
* `never_expires`: boolean
* `past_expiration_policy`: boolean or null
* `past_expiration_policy_basis`: string or null, enum: `enforced_limit`, `proposed_baseline`, `null`
* `expiry_unknown`: boolean
* `scopes`: array of string or null
* `permissions`: object or null, additional properties: string
* `repository_selection`: string or null, enum: `all`, `subset`, `none`, `null`