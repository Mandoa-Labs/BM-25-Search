# REST API endpoints for Copilot feature policy management

Use the REST API to manage Copilot feature policies for an organization.

> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## Get feature policies for an organization

```
GET /orgs/{org}/copilot/feature-policies
```

Note

This endpoint is in public preview and is subject to change.

Use this endpoint to retrieve the Copilot default availability policy for new features and
clients for an organization.
The enterprise default is used when the enterprise has set one. Otherwise, the organization's
own default is used, and an organization that has not enabled a default is reported as
disabled. For more information, see
About default availability.
Organization owners can use this endpoint.
OAuth app tokens and personal access tokens (classic) need the admin:org or repo scope to use this endpoint.
Organization SAML authorization and OAuth app access restrictions also apply.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

### HTTP response status codes

- **200** - OK

- **401** - Requires authentication

- **403** - Forbidden

- **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/copilot/feature-policies
```

**Response schema (Status: 200):**

* `default_availability`: required, object:
  * `policy_state`: required, string, enum: `enabled`, `disabled`
  * `editable`: required, boolean

## Update feature policies for an organization

```
PATCH /orgs/{org}/copilot/feature-policies
```

Note

This endpoint is in public preview and is subject to change.

Use this endpoint to update the Copilot default availability policy for new features and
clients for an organization.
An organization can only set its own default while its enterprise has not set one. For more
information, see
About default availability.
Changing this policy does not change any Copilot feature or client policy that has already been set.
Organization owners can use this endpoint.
OAuth app tokens and personal access tokens (classic) need the admin:org or repo scope to use this endpoint.
Organization SAML authorization and OAuth app access restrictions also apply.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

#### Body parameters

- **`default_availability`** (object) (required)
  - **`policy_state`** (string) (required)
    The organization default policy applied to newly released Copilot features and clients.
    Can be one of: `enabled`, `disabled`

### HTTP response status codes

- **200** - OK

- **401** - Requires authentication

- **403** - Forbidden

- **404** - Resource not found

- **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/orgs/ORG/copilot/feature-policies \
  -d '{
  "default_availability": {
    "policy_state": "enabled"
  }
}'
```

**Response schema (Status: 200):**

Same response schema as [Get feature policies for an organization](#get-feature-policies-for-an-organization).