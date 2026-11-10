# REST API endpoints for Copilot code review

Use the REST API to manage Copilot code review.

> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## Get the Copilot code review policy for an enterprise

```
GET /enterprises/{enterprise}/copilot/policies/code-review
```

Gets the configured Copilot code review policy for an enterprise.
This does not return a user's effective access, preview approval controls, or automatic-review rulesets.
Enterprise owners and users with the read_enterprise_ai_controls permission can use this endpoint.
OAuth app tokens and personal access tokens (classic) need the read:enterprise scope.
GitHub App tokens and fine-grained personal access tokens are not supported.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

### HTTP response status codes

- **200** - The configured enterprise policy.

- **401** - Requires authentication

- **403** - Forbidden

- **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/copilot/policies/code-review
```

**Response schema (Status: 200):**

* `policy_state`: required, string or null, enum: `enabled_for_all_organizations`, `disabled_for_all_organizations`, `configured_by_organization_admins`, `null`

## Set the Copilot code review policy for an enterprise

```
PUT /enterprises/{enterprise}/copilot/policies/code-review
```

Sets the configured Copilot code review policy for an enterprise, using the same
asynchronous propagation and notifications as enterprise settings. Policies that
depend on Copilot code review keep their values.
Enterprise owners and users with the write_enterprise_ai_controls permission can use this endpoint.
OAuth app tokens and personal access tokens (classic) need the admin:enterprise scope.
GitHub App tokens and fine-grained personal access tokens are not supported.
Standalone enterprises support enabled and disabled policies, but cannot delegate
policy to organization administrators. Invalid or unsupported input does not change any policy.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

#### Body parameters

- **`policy_state`** (string) (required)
  The enterprise's Copilot code review policy.
  Can be one of: `enabled_for_all_organizations`, `disabled_for_all_organizations`, `configured_by_organization_admins`

### HTTP response status codes

- **204** - A header with no content is returned.

- **400** - Bad Request

- **401** - Requires authentication

- **403** - Forbidden

- **404** - Resource not found

- **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/enterprises/ENTERPRISE/copilot/policies/code-review \
  -d '{
  "policy_state": "enabled_for_all_organizations"
}'
```

**Response schema (Status: 204):**

## Get the Copilot code review runner configuration for an organization

```
GET /orgs/{org}/copilot/code-review/runner
```

Gets the runner configuration that Copilot code review uses for an organization.
Until the organization saves a Copilot code review runner configuration, the response reports the values
inherited from the organization's Copilot coding agent runner configuration, with configured_by set to coding_agent.
Organization owners can use this endpoint.
OAuth app tokens and personal access tokens (classic) need either the
manage_billing:copilot or read:org scope.
GitHub App tokens and fine-grained personal access tokens are not supported.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

### HTTP response status codes

- **200** - The organization runner configuration.

- **401** - Requires authentication

- **403** - Forbidden

- **404** - Resource not found

- **503** - Service unavailable

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/copilot/code-review/runner
```

**Response schema (Status: 200):**

* `runner_type`: required, string, enum: `standard`, `labeled`
* `runner_labels`: required, array of string
* `runner_group_name`: required, string or null
* `allow_repository_customization`: required, boolean
* `configured_by`: required, string, enum: `code_review`, `coding_agent`

## Set the Copilot code review runner configuration for an organization

```
PUT /orgs/{org}/copilot/code-review/runner
```

Sets the runner configuration that Copilot code review uses for an organization. After a successful
update, Copilot code review uses its own runner configuration and configured_by is code_review.
A labeled runner requires at least one label in runner_labels or a runner_group_name. A standard
runner does not accept labels or a runner group. When allow_repository_customization is omitted, the current
effective value is kept. The whole request is validated before any change is made, so invalid input does not
change the configuration.
Organization owners can use this endpoint.
OAuth app tokens and personal access tokens (classic) need either the
manage_billing:copilot or admin:org scope.
GitHub App tokens and fine-grained personal access tokens are not supported.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

#### Body parameters

- **`runner_type`** (string) (required)
  The type of runner. standard uses GitHub-hosted runners. labeled uses runners that match the labels or runner group.
  Can be one of: `standard`, `labeled`

- **`runner_labels`** (array of strings or null)
  The runner labels for a labeled runner.

- **`runner_group_name`** (string or null)
  The runner group for a labeled runner.

- **`allow_repository_customization`** (boolean)
  Whether repositories can use their own runner configuration.

### HTTP response status codes

- **200** - The updated organization runner configuration.

- **400** - Bad Request

- **401** - Requires authentication

- **403** - Forbidden

- **404** - Resource not found

- **422** - Validation failed, or the endpoint has been spammed.

- **503** - Service unavailable

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/orgs/ORG/copilot/code-review/runner \
  -d '{
  "runner_type": "labeled",
  "runner_labels": [
    "copilot-review"
  ],
  "runner_group_name": "copilot-runners",
  "allow_repository_customization": false
}'
```

**Response schema (Status: 200):**

Same response schema as [Get the Copilot code review runner configuration for an organization](#get-the-copilot-code-review-runner-configuration-for-an-organization).

## Get Copilot code review settings for an organization

```
GET /orgs/{org}/copilot/code-review/settings
```

Gets the Copilot code review settings for an organization. Currently this is the default review effort
that repositories in the organization use when they do not choose their own.
For each setting, the response includes the configured value, the effective value, the default inherited
when nothing is configured, whether organization administrators can edit it, and whether the enterprise
or the organization manages it.
Organization owners can use this endpoint.
OAuth app tokens and personal access tokens (classic) need either the
manage_billing:copilot or read:org scope.
GitHub App tokens and fine-grained personal access tokens are not supported.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

### HTTP response status codes

- **200** - The organization settings.

- **401** - Requires authentication

- **403** - Forbidden

- **404** - Resource not found

- **503** - Service unavailable

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/copilot/code-review/settings
```

**Response schema (Status: 200):**

* `default_review_effort`: required, object:
  * `configured`: required, string or null
  * `effective`: required, string
  * `github_default`: required, string
  * `editable`: required, boolean
  * `managed_by`: required, string, enum: `enterprise`, `organization`
* `available_review_efforts`: required, array of string

## Update Copilot code review settings for an organization

```
PATCH /orgs/{org}/copilot/code-review/settings
```

Updates the Copilot code review settings for an organization. Omitted settings are not changed.
Set default_review_effort to inherit to clear the organization's value so repositories use the
inherited default again. Changes use the same audit logging and telemetry as organization settings.
Organization owners can use this endpoint.
OAuth app tokens and personal access tokens (classic) need either the
manage_billing:copilot or admin:org scope.
GitHub App tokens and fine-grained personal access tokens are not supported.
When a submitted setting cannot be changed by the organization, the request fails with 409 and the
code SETTING_NOT_EDITABLE. The whole request is validated before any change is made, so invalid input
and conflicts do not change any setting.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

#### Body parameters

- **`default_review_effort`** (string)
  The default review effort for repositories that do not choose their own. Use inherit to clear the organization's value. Only efforts listed in the settings' available_review_efforts are accepted, and a rejected effort's error message lists them. For more information, see Review effort level.

### HTTP response status codes

- **200** - The updated organization settings.

- **400** - Bad Request

- **401** - Requires authentication

- **403** - Forbidden

- **404** - Resource not found

- **409** - The organization cannot change a submitted setting.

- **422** - Validation failed, or the endpoint has been spammed.

- **503** - Service unavailable

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/orgs/ORG/copilot/code-review/settings \
  -d '{
  "default_review_effort": "balanced"
}'
```

**Response schema (Status: 200):**

Same response schema as [Get Copilot code review settings for an organization](#get-copilot-code-review-settings-for-an-organization).

## Get the Copilot code review policy for an organization

```
GET /orgs/{org}/copilot/policies/code-review
```

Gets the configured and effective Copilot code review policy for an organization,
whether organization administrators can edit it, and whether the enterprise or the organization manages it.
This does not return review effort, repository settings, preview approval controls, or automatic-review rulesets.
Organization owners can use this endpoint.
OAuth app tokens and personal access tokens (classic) need either the
manage_billing:copilot or read:org scope.
GitHub App tokens and fine-grained personal access tokens are not supported.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

### HTTP response status codes

- **200** - The organization policy.

- **401** - Requires authentication

- **403** - Forbidden

- **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/copilot/policies/code-review
```

**Response schema (Status: 200):**

* `configured_state`: required, string or null, enum: `enabled`, `disabled`, `null`
* `effective_state`: required, string, enum: `enabled`, `disabled`
* `editable`: required, boolean
* `managed_by`: required, string, enum: `enterprise`, `organization`

## Set the Copilot code review policy for an organization

```
PUT /orgs/{org}/copilot/policies/code-review
```

Sets the Copilot code review policy for an organization, using the same
user settings propagation and notifications as organization settings. Policies that
depend on Copilot code review keep their values.
Organization owners can use this endpoint.
OAuth app tokens and personal access tokens (classic) need either the
manage_billing:copilot or admin:org scope.
GitHub App tokens and fine-grained personal access tokens are not supported.
When the enterprise manages the policy, the request fails with 409 and the code
POLICY_MANAGED_BY_ENTERPRISE, even if the requested state matches the effective state.
Invalid input and conflicts do not change any policy.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

#### Body parameters

- **`state`** (string) (required)
  The organization's Copilot code review policy.
  Can be one of: `enabled`, `disabled`

### HTTP response status codes

- **204** - A header with no content is returned.

- **400** - Bad Request

- **401** - Requires authentication

- **403** - Forbidden

- **404** - Resource not found

- **409** - The enterprise manages the policy.

- **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/orgs/ORG/copilot/policies/code-review \
  -d '{
  "state": "enabled"
}'
```

**Response schema (Status: 204):**

## Get Copilot code review settings for a repository

```
GET /repos/{owner}/{repo}/copilot/code-review/settings
```

Gets the Copilot code review settings for a repository. These settings tune how Copilot code review
reviews pull requests in the repository. They do not enable Copilot code review.
review_effort.configured is null when the repository inherits its review effort from the organization,
the enterprise, or GitHub's default. review_effort.effective is the review effort that reviews use when the
requester and the pull request do not choose one. Only review efforts available for the repository are reported;
when reviews would use an unavailable effort, review_effort.effective is the review effort they would use without it.
Repository administrators can use this endpoint.
OAuth app tokens and personal access tokens (classic) need the repo scope to use this endpoint.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

### HTTP response status codes

- **200** - The repository settings.

- **401** - Requires authentication

- **403** - Forbidden

- **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/copilot/code-review/settings
```

**Response schema (Status: 200):**

* `review_effort`: required, object:
  * `configured`: required, string or null
  * `effective`: required, string
* `available_review_efforts`: required, array of string
* `severity_filter`: required, string, enum: `no_filter`, `low`, `low_and_medium`
* `custom_instructions_enabled`: required, boolean
* `mcp_enabled`: required, boolean

## Update Copilot code review settings for a repository

```
PATCH /repos/{owner}/{repo}/copilot/code-review/settings
```

Updates the Copilot code review settings for a repository. These settings tune how Copilot code review
reviews pull requests in the repository. They do not enable Copilot code review, and they can be stored
while an enterprise or organization policy disables Copilot code review.
Omitted settings are not changed. Set review_effort to inherit to clear the repository's review effort
so it inherits the effort from the organization, the enterprise, or GitHub's default. The whole request is
validated before any change is made, so invalid input does not change any setting. Changes use the same
audit logging and telemetry as the repository settings page.
Repository administrators can use this endpoint.
OAuth app tokens and personal access tokens (classic) need the repo scope to use this endpoint.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

#### Body parameters

- **`review_effort`** (string)
  The review effort for the repository. Use inherit to clear the repository's value. Only efforts listed in the settings' available_review_efforts are accepted, and a rejected effort's error message lists them. For more information, see Review effort level.

- **`severity_filter`** (string)
  Which review comment severities Copilot code review leaves out. Can only be set when the severity filter is available for the repository.
  Can be one of: `no_filter`, `low`, `low_and_medium`

- **`custom_instructions_enabled`** (boolean)
  Whether reviews use the repository's custom instructions.

- **`mcp_enabled`** (boolean)
  Whether reviews can use MCP servers.

### HTTP response status codes

- **200** - The updated repository settings.

- **400** - Bad Request

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
  https://api.github.com/repos/OWNER/REPO/copilot/code-review/settings \
  -d '{
  "review_effort": "balanced",
  "severity_filter": "low"
}'
```

**Response schema (Status: 200):**

Same response schema as [Get Copilot code review settings for a repository](#get-copilot-code-review-settings-for-a-repository).