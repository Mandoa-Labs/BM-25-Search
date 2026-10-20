# REST API endpoints for Copilot model policy management

Use the REST API to manage Copilot model policies for an organization.

> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## Get model policies for an organization

```
GET /orgs/{org}/copilot/model-policies
```

Use this endpoint to retrieve the effective Copilot model policy for every
model available to an organization, whether explicitly configured or
determined by default availability.
For a model without an effective explicit policy that is eligible for
default availability, the enterprise default is used when it is configured.
Otherwise, the organization's default is used. A model that is not eligible
for default availability and has no effective explicit policy is disabled.
For more information, see
About default availability of Copilot models.
The organization must either be independent or belong to an enterprise that is not
using enterprise teams for model policy.
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
  https://api.github.com/orgs/ORG/copilot/model-policies
```

**Response schema (Status: 200):**

* `default_availability`: required, object:
  * `policy_state`: required, string, enum: `enabled`, `disabled`
  * `editable`: required, boolean
* `models`: required, array of objects:
  * `model_name`: required, string
  * `display_name`: required, string
  * `policy_state`: required, string, enum: `enabled`, `disabled`, `delegate_to_default`, `unconfigured`

## Update model policies for an organization

```
PATCH /orgs/{org}/copilot/model-policies
```

Use this endpoint to set explicit Copilot model policies and default
availability for an organization. All policies in the request are updated atomically,
meaning if any change in the request cannot be applied, none of the changes are saved.
Use the model_name values returned by the "Get model policies for an organization"
endpoint. Models with an inherited enterprise policy are locked and cannot be updated.
Default availability cannot be updated when its editable value is false.
The response contains the effective policies for all models available to the
organization, not only the policies updated by the request.
The organization must either be independent or belong to an enterprise that is not
using enterprise teams for model policy.
Organization owners can use this endpoint.
OAuth app tokens and personal access tokens (classic) need the admin:org or repo scope to use this endpoint.
Organization SAML authorization and OAuth app access restrictions apply.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

#### Body parameters

- **`default_availability`** (object)
  The organization's default availability for eligible models without an explicit
policy. It cannot be updated when it is inherited from the enterprise.
  - **`policy_state`** (string) (required)
    Can be one of: `enabled`, `disabled`

- **`models`** (array of objects)
  The model policies to update. Each model_name must be unique.
  - **`model_name`** (string) (required)
    The public identifier of a model returned by the get endpoint.
  - **`policy_state`** (string) (required)
    The explicit policy state to set for the organization.
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
  https://api.github.com/orgs/ORG/copilot/model-policies \
  -d '{
  "default_availability": {
    "policy_state": "disabled"
  },
  "models": [
    {
      "model_name": "gpt-5.6-sol",
      "policy_state": "enabled"
    },
    {
      "model_name": "gpt-5",
      "policy_state": "disabled"
    }
  ]
}'
```

**Response schema (Status: 200):**

Same response schema as [Get model policies for an organization](#get-model-policies-for-an-organization).