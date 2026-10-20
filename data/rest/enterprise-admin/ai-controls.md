# REST API endpoints for enterprise AI controls

Use the REST API to manage Copilot model policies for your enterprise, enterprise teams, and enterprise apps.

> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## Get model policies for enterprise apps

```
GET /enterprises/{enterprise}/copilot/apps/model-policies
```

Use this endpoint to retrieve Copilot model policies for enterprise apps.
The response shows which model settings can be changed and which are
controlled by enterprise policy.
For models whose settings can be changed, the response shows the configured
setting or optional if no setting has been configured. For models
controlled by enterprise policy, it shows the enterprise setting or the
applicable default. These settings do not necessarily determine whether
an individual user can access a model.
Enterprise owners and users with the read_enterprise_ai_controls permission can use this endpoint.
OAuth app tokens and personal access tokens (classic) need the read:enterprise scope to use this endpoint.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

### HTTP response status codes

- **200** - OK

- **401** - Requires authentication

- **403** - Forbidden

- **404** - Resource not found

- **503** - Service unavailable

### Code examples

#### Example 1: Status Code 200

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/copilot/apps/model-policies
```

**Response schema (Status: 200):**

* `models`: required, array of objects:
  * `model_name`: required, string
  * `display_name`: required, string
  * `policy_state`: required, string, enum: `enabled`, `disabled`, `optional`
  * `enterprise_policy_state`: required, string, enum: `enabled`, `disabled`, `delegate_to_teams_and_apps`, `delegate_to_default`, `unconfigured`
  * `editable`: required, boolean

#### Example 2: Status Code 200

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/copilot/apps/model-policies
```

**Response schema (Status: 200):**

* `models`: required, array of objects:
  * `model_name`: required, string
  * `display_name`: required, string
  * `policy_state`: required, string, enum: `enabled`, `disabled`, `optional`
  * `enterprise_policy_state`: required, string, enum: `enabled`, `disabled`, `delegate_to_teams_and_apps`, `delegate_to_default`, `unconfigured`
  * `editable`: required, boolean

## Update model policies for enterprise apps

```
PATCH /enterprises/{enterprise}/copilot/apps/model-policies
```

Use this endpoint to set Copilot model policies for enterprise apps. Set a
model to enabled to configure an apps policy, or to optional to remove
the stored apps policy for that model.
Locked models cannot be updated.
Returns the apps policy state representation, including enterprise policy and editability.
These states are not a final access decision for a user.
Enterprise owners and users with the write_enterprise_ai_controls permission can use this endpoint.
OAuth app tokens and personal access tokens (classic) need the admin:enterprise scope to use this endpoint.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

#### Body parameters

- **`models`** (array of objects) (required)
  - **`model_name`** (string) (required)
  - **`policy_state`** (string) (required)
    Use optional to remove the apps policy.
    Can be one of: `enabled`, `disabled`, `optional`

### HTTP response status codes

- **200** - OK

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
  -X PATCH \
  https://api.github.com/enterprises/ENTERPRISE/copilot/apps/model-policies \
  -d '{
  "models": [
    {
      "model_name": "gpt-5.6-sol",
      "policy_state": "enabled"
    }
  ]
}'
```

**Response schema (Status: 200):**

Same response schema as [Get model policies for enterprise apps](#get-model-policies-for-enterprise-apps).

## Get model policies for an enterprise

```
GET /enterprises/{enterprise}/copilot/model-policies
```

Use this endpoint to retrieve Copilot model policies for an enterprise.
For enterprises that manage Copilot through organizations, delegated models use the
policy state of delegate_to_organizations.
Enterprise owners and users with the read_enterprise_ai_controls permission can use this endpoint.
OAuth app tokens and personal access tokens (classic) need the read:enterprise scope to use this endpoint.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

### HTTP response status codes

- **200** - OK

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
  https://api.github.com/enterprises/ENTERPRISE/copilot/model-policies
```

**Response schema (Status: 200):**

* `default_availability`: object:
  * `policy_state`: required, string, enum: `enabled`, `disabled`, `delegate_to_organizations`
* `models`: required, array of objects:
  * `model_name`: required, string
  * `display_name`: required, string
  * `policy_state`: required, string, enum: `enabled`, `disabled`, `delegate_to_teams_and_apps`, `delegate_to_organizations`, `delegate_to_default`, `unconfigured`

## Update model policies for an enterprise

```
PATCH /enterprises/{enterprise}/copilot/model-policies
```

Use this endpoint to update Copilot model policies for an enterprise.
For enterprises that manage Copilot through organizations, use
delegate_to_organizations to delegate a model or default availability.
Enterprises without organizations cannot use delegate_to_organizations.
Enterprise owners and users with the write_enterprise_ai_controls permission can use this endpoint.
OAuth app tokens and personal access tokens (classic) need the admin:enterprise scope to use this endpoint.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

#### Body parameters

- **`default_availability`** (object)
  - **`policy_state`** (string) (required)
    delegate_to_organizations is only accepted for enterprises that manage Copilot through organizations.
    Can be one of: `enabled`, `disabled`, `delegate_to_organizations`

- **`models`** (array of objects)
  - **`model_name`** (string) (required)
  - **`policy_state`** (string) (required)
    delegate_to_organizations is only accepted for enterprises that manage Copilot through organizations.
    Can be one of: `enabled`, `disabled`, `delegate_to_teams_and_apps`, `delegate_to_organizations`

### HTTP response status codes

- **200** - OK

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
  -X PATCH \
  https://api.github.com/enterprises/ENTERPRISE/copilot/model-policies \
  -d '{
  "default_availability": {
    "policy_state": "enabled"
  },
  "models": [
    {
      "model_name": "gpt-5.6-sol",
      "policy_state": "enabled"
    }
  ]
}'
```

**Response schema (Status: 200):**

Same response schema as [Get model policies for an enterprise](#get-model-policies-for-an-enterprise).

## Get model policies for an enterprise team

```
GET /enterprises/{enterprise}/teams/{team_id}/copilot/model-policies
```

Use this endpoint to retrieve Copilot model policy states for an enterprise
team, along with the corresponding enterprise-level policies. The response
shows which model policies the team can update based on enterprise policy
and the available team policy controls.
For models the team can update, the response shows the team’s configured
value or optional if the team has not set one. For locked models, it shows
the enterprise’s explicit value or the applicable default availability for
eligible models. These states are not a final access decision for a user.
Enterprise owners and users with the read_enterprise_ai_controls permission can use this endpoint.
OAuth app tokens and personal access tokens (classic) need the read:enterprise scope to use this endpoint.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

- **`team_id`** (integer) (required)
  The unique identifier of the team.

### HTTP response status codes

- **200** - OK

- **401** - Requires authentication

- **403** - Forbidden

- **404** - Resource not found

- **503** - Service unavailable

### Code examples

#### Example 1: Status Code 200

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/teams/TEAM_ID/copilot/model-policies
```

**Response schema (Status: 200):**

Same response schema as [Get model policies for enterprise apps](#get-model-policies-for-enterprise-apps).

#### Example 2: Status Code 200

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/teams/TEAM_ID/copilot/model-policies
```

**Response schema (Status: 200):**

Same response schema as [Get model policies for enterprise apps](#get-model-policies-for-enterprise-apps).

## Update model policies for an enterprise team

```
PATCH /enterprises/{enterprise}/teams/{team_id}/copilot/model-policies
```

Use this endpoint to update Copilot model policies for an enterprise team.
Only editable model policies can be updated.
Set a model to enabled to configure a team policy, or to optional to clear
the team’s policy for that model. Locked models cannot be updated.
The response contains the same policy state information as the corresponding
GET endpoint, including enterprise policies and whether each model policy
can be updated. These states do not necessarily determine whether an
individual user can access a model.
Enterprise owners and users with the write_enterprise_ai_controls permission can use this endpoint.
OAuth app tokens and personal access tokens (classic) need the admin:enterprise scope to use this endpoint.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

- **`team_id`** (integer) (required)
  The unique identifier of the team.

#### Body parameters

- **`models`** (array of objects) (required)
  - **`model_name`** (string) (required)
  - **`policy_state`** (string) (required)
    Use optional to remove the team's policy.
    Can be one of: `enabled`, `disabled`, `optional`

### HTTP response status codes

- **200** - OK

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
  -X PATCH \
  https://api.github.com/enterprises/ENTERPRISE/teams/TEAM_ID/copilot/model-policies \
  -d '{
  "models": [
    {
      "model_name": "gpt-5.6-sol",
      "policy_state": "enabled"
    }
  ]
}'
```

**Response schema (Status: 200):**

Same response schema as [Get model policies for enterprise apps](#get-model-policies-for-enterprise-apps).