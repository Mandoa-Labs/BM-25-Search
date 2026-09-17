# REST API endpoints for GitHub Actions policies

Use the REST API to view and manage policies for GitHub Actions.

> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## List organization Actions policies

```
GET /orgs/{org}/actions/policies
```

List all Actions policies for an organization.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

- **`has_parents`** (boolean)
  Include policies configured at higher levels that apply to this organization
  Default: `true`

### HTTP response status codes

- **200** - OK

- **404** - Resource not found

- **500** - Internal Error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/actions/policies
```

**Response schema (Status: 200):**

* `total_count`: required, integer
* `policies`: required, array of `Actions Policy`:
  * `id`: required, integer
  * `name`: required, string
  * `target`: required, string, enum: `actions`
  * `source_type`: required, string, enum: `Repository`, `Organization`, `Enterprise`
  * `source`: required, string
  * `enforcement`: required, string, enum: `disabled`, `active`, `evaluate`
  * `conditions`: any of:
    * **Repository Actions policy conditions**
    * **Organization Actions policy conditions**
    * **Enterprise Actions policy conditions**
  * `rules`: array of object
  * `node_id`: string
  * `_links`: object:
    * `self`: object:
      * `href`: string
    * `html`: object:
      * `href`: string
  * `created_at`: string, format: date-time
  * `updated_at`: string, format: date-time

## Create an organization Actions policy

```
POST /orgs/{org}/actions/policies
```

Create an Actions policy for an organization.
Omitting workflow_path targets all workflows without storing an explicit condition.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

#### Body parameters

- **`name`** (string) (required)
  The name of the policy.

- **`enforcement`** (string) (required)
  The enforcement level of the ruleset. evaluate allows admins to test rules before enforcing them. Admins can view insights on the Rule Insights page (evaluate is only available with GitHub Enterprise).
  Can be one of: `disabled`, `active`, `evaluate`

- **`conditions`** (object)
  Conditions for an organization Actions policy. The conditions object should contain one of
repository_name, repository_id, or repository_property, and may also contain workflow_path.
  - **`Repository ruleset conditions for repository names`** (object)
    Parameters for a repository name condition
    - **`repository_name`** (object) (required)
      - **`include`** (array of strings)
        Array of repository names or patterns to include. One of these patterns must match for the condition to pass. Also accepts ~ALL to include all repositories.
      - **`exclude`** (array of strings)
        Array of repository names or patterns to exclude. The condition will not pass if any of these patterns match.
      - **`protected`** (boolean)
        Whether renaming of target repositories is prevented.
    - **`workflow_path`** (object)
      - **`include`** (array of strings) (required)
        Array of workflow file paths or glob patterns to include. An empty array includes all
workflows not matched by an excluded pattern. Use ~ALL by itself to include all workflows.
~ALL cannot be combined with other included patterns.
      - **`exclude`** (array of strings) (required)
        Array of workflow file paths or glob patterns to exclude. The condition will not pass
if any of these patterns match. ~ALL is not allowed in this array.
  - **`Repository ruleset conditions for repository IDs`** (object)
    Parameters for a repository ID condition
    - **`repository_id`** (object) (required)
      - **`repository_ids`** (array of integers)
        The repository IDs that the ruleset applies to. One of these IDs must match for the condition to pass.
    - **`workflow_path`** (object)
      - **`include`** (array of strings) (required)
        Array of workflow file paths or glob patterns to include. An empty array includes all
workflows not matched by an excluded pattern. Use ~ALL by itself to include all workflows.
~ALL cannot be combined with other included patterns.
      - **`exclude`** (array of strings) (required)
        Array of workflow file paths or glob patterns to exclude. The condition will not pass
if any of these patterns match. ~ALL is not allowed in this array.
  - **`Repository ruleset conditions for repository properties`** (object)
    Parameters for a repository property condition
    - **`repository_property`** (object) (required)
      - **`include`** (array of objects)
        The repository properties and values to include. All of these properties must match for the condition to pass.
        - **`name`** (string) (required)
          The name of the repository property to target
        - **`property_values`** (array of strings) (required)
          The values to match for the repository property
        - **`source`** (string)
          The source of the repository property. Defaults to 'custom' if not specified.
          Can be one of: `custom`, `system`
      - **`exclude`** (array of objects)
        The repository properties and values to exclude. The condition will not pass if any of these properties match.
        - **`name`** (string) (required)
          The name of the repository property to target
        - **`property_values`** (array of strings) (required)
          The values to match for the repository property
        - **`source`** (string)
          The source of the repository property. Defaults to 'custom' if not specified.
          Can be one of: `custom`, `system`
    - **`workflow_path`** (object)
      - **`include`** (array of strings) (required)
        Array of workflow file paths or glob patterns to include. An empty array includes all
workflows not matched by an excluded pattern. Use ~ALL by itself to include all workflows.
~ALL cannot be combined with other included patterns.
      - **`exclude`** (array of strings) (required)
        Array of workflow file paths or glob patterns to exclude. The condition will not pass
if any of these patterns match. ~ALL is not allowed in this array.

- **`rules`** (array of objects)
  An array of rules within the policy.
  - **`restrict_actions_actors`** (object)
    Choose specific actors that are authorized to trigger Actions workflows.
    - **`type`** (string) (required)
      Can be one of: `restrict_actions_actors`
    - **`parameters`** (object)
      - **`allowed_actors`** (array of objects) (required)
        Select the actors who can run Actions workflows.
        - **`id`** (integer) (required)
          ID of the actor authorized to trigger Actions workflows.
        - **`type`** (string) (required)
          The type of the actor
          Can be one of: `User`, `Bot`, `Team`, `BusinessTeam`, `EnterpriseTeam`, `IntegrationInstallation`, `App`, `RepositoryRole`
  - **`restrict_action_events`** (object)
    Choose specific GitHub events that will trigger Actions workflows.
    - **`type`** (string) (required)
      Can be one of: `restrict_action_events`
    - **`parameters`** (object)
      - **`allowed_events`** (array of strings) (required)
        Select the events that can trigger Actions workflows.
Supported values are: branch_protection_rule, check_run, check_suite, create, delete, deployment, deployment_status, discussion, discussion_comment, fork, gollum, image_version, issue_comment, issues, label, merge_group, milestone, page_build, project, project_card, project_column, public, pull_request, pull_request_review, pull_request_review_comment, pull_request_target, push, registry_package, release, repository_dispatch, schedule, status, watch, workflow_call, workflow_dispatch, workflow_run

### HTTP response status codes

- **201** - Created

- **404** - Resource not found

- **422** - Validation failed, or the endpoint has been spammed.

- **500** - Internal Error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/orgs/ORG/actions/policies \
  -d '{
  "name": "Require approved actors",
  "enforcement": "active",
  "rules": [
    {
      "type": "restrict_actions_actors",
      "parameters": {
        "allowed_actors": [
          {
            "id": 1234,
            "type": "Team"
          }
        ]
      }
    }
  ]
}'
```

**Response schema (Status: 201):**

* `id`: required, integer
* `name`: required, string
* `target`: required, string, enum: `actions`
* `source_type`: required, string, enum: `Repository`, `Organization`, `Enterprise`
* `source`: required, string
* `enforcement`: required, string, enum: `disabled`, `active`, `evaluate`
* `conditions`: any of:
  * **Repository Actions policy conditions**
  * **Organization Actions policy conditions**
  * **Enterprise Actions policy conditions**
* `rules`: array of object
* `node_id`: string
* `_links`: object:
  * `self`: object:
    * `href`: string
  * `html`: object:
    * `href`: string
* `created_at`: string, format: date-time
* `updated_at`: string, format: date-time

## Get an organization Actions policy

```
GET /orgs/{org}/actions/policies/{policy_id}
```

Get a specific Actions policy for an organization.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`policy_id`** (integer) (required)
  The ID of the policy.

### HTTP response status codes

- **200** - OK

- **404** - Resource not found

- **500** - Internal Error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/actions/policies/POLICY_ID
```

**Response schema (Status: 200):**

Same response schema as [Create an organization Actions policy](#create-an-organization-actions-policy).

## Update an organization Actions policy

```
PUT /orgs/{org}/actions/policies/{policy_id}
```

Update an Actions policy for an organization.
Omitting workflow_path preserves the policy's existing workflow targeting.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`policy_id`** (integer) (required)
  The ID of the policy.

#### Body parameters

- **`name`** (string)
  The name of the policy.

- **`enforcement`** (string)
  The enforcement level of the ruleset. evaluate allows admins to test rules before enforcing them. Admins can view insights on the Rule Insights page (evaluate is only available with GitHub Enterprise).
  Can be one of: `disabled`, `active`, `evaluate`

- **`conditions`** (object)
  Conditions for an organization Actions policy. The conditions object should contain one of
repository_name, repository_id, or repository_property, and may also contain workflow_path.
  - **`Repository ruleset conditions for repository names`** (object)
    Parameters for a repository name condition
    - **`repository_name`** (object) (required)
      - **`include`** (array of strings)
        Array of repository names or patterns to include. One of these patterns must match for the condition to pass. Also accepts ~ALL to include all repositories.
      - **`exclude`** (array of strings)
        Array of repository names or patterns to exclude. The condition will not pass if any of these patterns match.
      - **`protected`** (boolean)
        Whether renaming of target repositories is prevented.
    - **`workflow_path`** (object)
      - **`include`** (array of strings) (required)
        Array of workflow file paths or glob patterns to include. An empty array includes all
workflows not matched by an excluded pattern. Use ~ALL by itself to include all workflows.
~ALL cannot be combined with other included patterns.
      - **`exclude`** (array of strings) (required)
        Array of workflow file paths or glob patterns to exclude. The condition will not pass
if any of these patterns match. ~ALL is not allowed in this array.
  - **`Repository ruleset conditions for repository IDs`** (object)
    Parameters for a repository ID condition
    - **`repository_id`** (object) (required)
      - **`repository_ids`** (array of integers)
        The repository IDs that the ruleset applies to. One of these IDs must match for the condition to pass.
    - **`workflow_path`** (object)
      - **`include`** (array of strings) (required)
        Array of workflow file paths or glob patterns to include. An empty array includes all
workflows not matched by an excluded pattern. Use ~ALL by itself to include all workflows.
~ALL cannot be combined with other included patterns.
      - **`exclude`** (array of strings) (required)
        Array of workflow file paths or glob patterns to exclude. The condition will not pass
if any of these patterns match. ~ALL is not allowed in this array.
  - **`Repository ruleset conditions for repository properties`** (object)
    Parameters for a repository property condition
    - **`repository_property`** (object) (required)
      - **`include`** (array of objects)
        The repository properties and values to include. All of these properties must match for the condition to pass.
        - **`name`** (string) (required)
          The name of the repository property to target
        - **`property_values`** (array of strings) (required)
          The values to match for the repository property
        - **`source`** (string)
          The source of the repository property. Defaults to 'custom' if not specified.
          Can be one of: `custom`, `system`
      - **`exclude`** (array of objects)
        The repository properties and values to exclude. The condition will not pass if any of these properties match.
        - **`name`** (string) (required)
          The name of the repository property to target
        - **`property_values`** (array of strings) (required)
          The values to match for the repository property
        - **`source`** (string)
          The source of the repository property. Defaults to 'custom' if not specified.
          Can be one of: `custom`, `system`
    - **`workflow_path`** (object)
      - **`include`** (array of strings) (required)
        Array of workflow file paths or glob patterns to include. An empty array includes all
workflows not matched by an excluded pattern. Use ~ALL by itself to include all workflows.
~ALL cannot be combined with other included patterns.
      - **`exclude`** (array of strings) (required)
        Array of workflow file paths or glob patterns to exclude. The condition will not pass
if any of these patterns match. ~ALL is not allowed in this array.

- **`rules`** (array of objects)
  An array of rules within the policy.
  - **`restrict_actions_actors`** (object)
    Choose specific actors that are authorized to trigger Actions workflows.
    - **`type`** (string) (required)
      Can be one of: `restrict_actions_actors`
    - **`parameters`** (object)
      - **`allowed_actors`** (array of objects) (required)
        Select the actors who can run Actions workflows.
        - **`id`** (integer) (required)
          ID of the actor authorized to trigger Actions workflows.
        - **`type`** (string) (required)
          The type of the actor
          Can be one of: `User`, `Bot`, `Team`, `BusinessTeam`, `EnterpriseTeam`, `IntegrationInstallation`, `App`, `RepositoryRole`
  - **`restrict_action_events`** (object)
    Choose specific GitHub events that will trigger Actions workflows.
    - **`type`** (string) (required)
      Can be one of: `restrict_action_events`
    - **`parameters`** (object)
      - **`allowed_events`** (array of strings) (required)
        Select the events that can trigger Actions workflows.
Supported values are: branch_protection_rule, check_run, check_suite, create, delete, deployment, deployment_status, discussion, discussion_comment, fork, gollum, image_version, issue_comment, issues, label, merge_group, milestone, page_build, project, project_card, project_column, public, pull_request, pull_request_review, pull_request_review_comment, pull_request_target, push, registry_package, release, repository_dispatch, schedule, status, watch, workflow_call, workflow_dispatch, workflow_run

### HTTP response status codes

- **200** - OK

- **404** - Resource not found

- **422** - Validation failed, or the endpoint has been spammed.

- **500** - Internal Error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/orgs/ORG/actions/policies/POLICY_ID \
  -d '{
  "name": "Updated policy name",
  "enforcement": "active"
}'
```

**Response schema (Status: 200):**

Same response schema as [Create an organization Actions policy](#create-an-organization-actions-policy).

## Delete an organization Actions policy

```
DELETE /orgs/{org}/actions/policies/{policy_id}
```

Delete an Actions policy for an organization.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`policy_id`** (integer) (required)
  The ID of the policy.

### HTTP response status codes

- **204** - No Content

- **404** - Resource not found

- **500** - Internal Error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/orgs/ORG/actions/policies/POLICY_ID
```

**Response schema (Status: 204):**

## List repository Actions policies

```
GET /repos/{owner}/{repo}/actions/policies
```

List all Actions policies for a repository.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

- **`has_parents`** (boolean)
  Include policies configured at higher levels that apply to this repository
  Default: `true`

### HTTP response status codes

- **200** - OK

- **404** - Resource not found

- **500** - Internal Error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/actions/policies
```

**Response schema (Status: 200):**

Same response schema as [List organization Actions policies](#list-organization-actions-policies).

## Create a repository Actions policy

```
POST /repos/{owner}/{repo}/actions/policies
```

Create an Actions policy for a repository.
Omitting workflow_path targets all workflows without storing an explicit condition.

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

- **`name`** (string) (required)
  The name of the policy.

- **`enforcement`** (string) (required)
  The enforcement level of the ruleset. evaluate allows admins to test rules before enforcing them. Admins can view insights on the Rule Insights page (evaluate is only available with GitHub Enterprise).
  Can be one of: `disabled`, `active`, `evaluate`

- **`conditions`** (object)
  Conditions for a repository Actions policy. The object may be empty to preserve or use the
default workflow targeting, or contain only workflow_path.
  - **``** (object)
  - **`Actions policy workflow path condition`** (object)
    Parameters for an Actions policy workflow path condition. Omitting workflow_path when creating
a policy targets all workflows without storing an explicit condition. Omitting it when updating a
policy preserves the existing workflow targeting. For new or changed workflow conditions, the API
requires at least one included or excluded pattern. This is validated server-side rather than by
this schema, which can also describe existing stored conditions.
    - **`workflow_path`** (object) (required)
      - **`include`** (array of strings) (required)
        Array of workflow file paths or glob patterns to include. An empty array includes all
workflows not matched by an excluded pattern. Use ~ALL by itself to include all workflows.
~ALL cannot be combined with other included patterns.
      - **`exclude`** (array of strings) (required)
        Array of workflow file paths or glob patterns to exclude. The condition will not pass
if any of these patterns match. ~ALL is not allowed in this array.

- **`rules`** (array of objects)
  An array of rules within the policy.
  - **`restrict_actions_actors`** (object)
    Choose specific actors that are authorized to trigger Actions workflows.
    - **`type`** (string) (required)
      Can be one of: `restrict_actions_actors`
    - **`parameters`** (object)
      - **`allowed_actors`** (array of objects) (required)
        Select the actors who can run Actions workflows.
        - **`id`** (integer) (required)
          ID of the actor authorized to trigger Actions workflows.
        - **`type`** (string) (required)
          The type of the actor
          Can be one of: `User`, `Bot`, `Team`, `BusinessTeam`, `EnterpriseTeam`, `IntegrationInstallation`, `App`, `RepositoryRole`
  - **`restrict_action_events`** (object)
    Choose specific GitHub events that will trigger Actions workflows.
    - **`type`** (string) (required)
      Can be one of: `restrict_action_events`
    - **`parameters`** (object)
      - **`allowed_events`** (array of strings) (required)
        Select the events that can trigger Actions workflows.
Supported values are: branch_protection_rule, check_run, check_suite, create, delete, deployment, deployment_status, discussion, discussion_comment, fork, gollum, image_version, issue_comment, issues, label, merge_group, milestone, page_build, project, project_card, project_column, public, pull_request, pull_request_review, pull_request_review_comment, pull_request_target, push, registry_package, release, repository_dispatch, schedule, status, watch, workflow_call, workflow_dispatch, workflow_run

### HTTP response status codes

- **201** - Created

- **404** - Resource not found

- **422** - Validation failed, or the endpoint has been spammed.

- **500** - Internal Error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/actions/policies \
  -d '{
  "name": "Require approved actors",
  "enforcement": "active",
  "rules": [
    {
      "type": "restrict_actions_actors",
      "parameters": {
        "allowed_actors": [
          {
            "id": 1234,
            "type": "Team"
          }
        ]
      }
    }
  ]
}'
```

**Response schema (Status: 201):**

Same response schema as [Create an organization Actions policy](#create-an-organization-actions-policy).

## Get a repository Actions policy

```
GET /repos/{owner}/{repo}/actions/policies/{policy_id}
```

Get a specific Actions policy for a repository.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

- **`policy_id`** (integer) (required)
  The ID of the policy.

### HTTP response status codes

- **200** - OK

- **404** - Resource not found

- **500** - Internal Error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/actions/policies/POLICY_ID
```

**Response schema (Status: 200):**

Same response schema as [Create an organization Actions policy](#create-an-organization-actions-policy).

## Update a repository Actions policy

```
PUT /repos/{owner}/{repo}/actions/policies/{policy_id}
```

Update an Actions policy for a repository.
Omitting workflow_path preserves the policy's existing workflow targeting.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

- **`policy_id`** (integer) (required)
  The ID of the policy.

#### Body parameters

- **`name`** (string)
  The name of the policy.

- **`enforcement`** (string)
  The enforcement level of the ruleset. evaluate allows admins to test rules before enforcing them. Admins can view insights on the Rule Insights page (evaluate is only available with GitHub Enterprise).
  Can be one of: `disabled`, `active`, `evaluate`

- **`conditions`** (object)
  Conditions for a repository Actions policy. The object may be empty to preserve or use the
default workflow targeting, or contain only workflow_path.
  - **``** (object)
  - **`Actions policy workflow path condition`** (object)
    Parameters for an Actions policy workflow path condition. Omitting workflow_path when creating
a policy targets all workflows without storing an explicit condition. Omitting it when updating a
policy preserves the existing workflow targeting. For new or changed workflow conditions, the API
requires at least one included or excluded pattern. This is validated server-side rather than by
this schema, which can also describe existing stored conditions.
    - **`workflow_path`** (object) (required)
      - **`include`** (array of strings) (required)
        Array of workflow file paths or glob patterns to include. An empty array includes all
workflows not matched by an excluded pattern. Use ~ALL by itself to include all workflows.
~ALL cannot be combined with other included patterns.
      - **`exclude`** (array of strings) (required)
        Array of workflow file paths or glob patterns to exclude. The condition will not pass
if any of these patterns match. ~ALL is not allowed in this array.

- **`rules`** (array of objects)
  An array of rules within the policy.
  - **`restrict_actions_actors`** (object)
    Choose specific actors that are authorized to trigger Actions workflows.
    - **`type`** (string) (required)
      Can be one of: `restrict_actions_actors`
    - **`parameters`** (object)
      - **`allowed_actors`** (array of objects) (required)
        Select the actors who can run Actions workflows.
        - **`id`** (integer) (required)
          ID of the actor authorized to trigger Actions workflows.
        - **`type`** (string) (required)
          The type of the actor
          Can be one of: `User`, `Bot`, `Team`, `BusinessTeam`, `EnterpriseTeam`, `IntegrationInstallation`, `App`, `RepositoryRole`
  - **`restrict_action_events`** (object)
    Choose specific GitHub events that will trigger Actions workflows.
    - **`type`** (string) (required)
      Can be one of: `restrict_action_events`
    - **`parameters`** (object)
      - **`allowed_events`** (array of strings) (required)
        Select the events that can trigger Actions workflows.
Supported values are: branch_protection_rule, check_run, check_suite, create, delete, deployment, deployment_status, discussion, discussion_comment, fork, gollum, image_version, issue_comment, issues, label, merge_group, milestone, page_build, project, project_card, project_column, public, pull_request, pull_request_review, pull_request_review_comment, pull_request_target, push, registry_package, release, repository_dispatch, schedule, status, watch, workflow_call, workflow_dispatch, workflow_run

### HTTP response status codes

- **200** - OK

- **404** - Resource not found

- **422** - Validation failed, or the endpoint has been spammed.

- **500** - Internal Error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/repos/OWNER/REPO/actions/policies/POLICY_ID \
  -d '{
  "name": "Updated policy name",
  "enforcement": "active"
}'
```

**Response schema (Status: 200):**

Same response schema as [Create an organization Actions policy](#create-an-organization-actions-policy).

## Delete a repository Actions policy

```
DELETE /repos/{owner}/{repo}/actions/policies/{policy_id}
```

Delete an Actions policy for a repository.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

- **`policy_id`** (integer) (required)
  The ID of the policy.

### HTTP response status codes

- **204** - No Content

- **404** - Resource not found

- **500** - Internal Error

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/repos/OWNER/REPO/actions/policies/POLICY_ID
```

**Response schema (Status: 204):**