# REST API endpoints for agent automations

Use the REST API to manage agent automations.

> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## List automations for user

```
GET /agents/automations
```

Returns automations whose created_by user is the authenticated caller, across
repositories the caller can read. This includes both user-owned and repository-owned
automations created by the caller but excludes repository-owned automations created by
someone else even if the caller has write access to the repository.
Use the repository-scoped list operation for those automations. The owner_type filter
only narrows this creator-scoped collection.
Fine-grained access tokens for "List automations for user"
This endpoint works with the following fine-grained token types:

GitHub App user access tokens
Fine-grained personal access tokens

The fine-grained token must have one of the following permission sets for each
repository accessed by this request:

"Agent tasks" repository permissions (read)
"Contents" repository permissions (read)

The required permission set depends on each repository's Automation permission
configuration.
GitHub App installation access tokens are not supported for this endpoint.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`page`** (integer)
  The page number of the results to fetch.
  Default: `1`

- **`per_page`** (integer)
  The number of results per page (max 100).
  Default: `30`

- **`owner_type`** (string)
  Filter automations by owner type. user returns automations owned by their creator, repository returns automations owned by the repository. Omit to return both.
  Can be one of: `user`, `repository`

### HTTP response status codes

- **200** - Automations retrieved successfully

- **400** - Bad request

- **401** - Authentication required

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/agents/automations
```

**Response schema (Status: 200):**

Array of objects:
  * `id`: required, string
  * `repository`: required, object:
    * `id`: required, integer, format: int64
    * `owner`: required, string
    * `name`: required, string
  * `name`: required, string
  * `enabled`: boolean
  * `owner_type`: string, enum: `user`, `repository`, read-only
  * `write_scope`: string, enum: `trigger`, `repository`, default: `"trigger"`
  * `require_actor_write_permission`: boolean, default: `false`
  * `model`: string
  * `reasoning_effort`: string
  * `triggers`: object:
    * `interval`: object:
      * `cadence`: required, array of string, enum: `hourly`, `daily`, `weekly`
      * `hour_utc`: integer, minimum: 0, maximum: 23
      * `day_of_week`: integer, minimum: 0, maximum: 6
      * `minute_utc`: integer, enum: `0`, `15`, `30`, `45`, default: `0`
      * `write_scope`: string, enum: `trigger`, `repository`
    * `issue_opened`: object:
      * `query`: string, minLength: 1
      * `write_scope`: string, enum: `trigger`, `repository`
    * `issue_labeled`: object:
      * `query`: string, minLength: 1
      * `labels`: array of string
      * `write_scope`: string, enum: `trigger`, `repository`
    * `workflow_run`: object:
      * `workflows`: required, array of string, minLength: 1
      * `conclusions`: required, array of string, enum: `failure`
      * `query`: string, minLength: 1
      * `write_scope`: string, enum: `trigger`, `repository`
    * `pull_request_opened`: object:
      * `query`: string, minLength: 1
      * `paths`: array of string, minLength: 1
      * `write_scope`: string, enum: `trigger`, `repository`
    * `pull_request_synchronize`: object:
      * `query`: string, minLength: 1
      * `paths`: array of string, minLength: 1
      * `write_scope`: string, enum: `trigger`, `repository`
    * `pull_request_merged`: object:
      * `query`: string, minLength: 1
      * `paths`: array of string, minLength: 1
      * `write_scope`: string, enum: `trigger`, `repository`
    * `issue_comment`: object:
      * `body_substring`: string
      * `write_scope`: string, enum: `trigger`, `repository`
    * `pull_request_comment`: object:
      * `comment_types`: required, array of string, enum: `timeline_comment`, `review_comment`
      * `body_substring`: string
      * `write_scope`: string, enum: `trigger`, `repository`
    * `discussion_opened`: object:
      * `categories`: array of string
      * `body_substring`: string
      * `write_scope`: string, enum: `trigger`, `repository`
    * `discussion_updated`: object:
      * `categories`: array of string
      * `body_substring`: string
      * `write_scope`: string, enum: `trigger`, `repository`
    * `discussion_comment`: object:
      * `comment_types`: array of string, enum: `comment`, `reply`
      * `categories`: array of string
      * `body_substring`: string
      * `write_scope`: string, enum: `trigger`, `repository`
    * `issue_assigned`: object:
      * `query`: string, minLength: 1
      * `assignees`: array of string
      * `write_scope`: string, enum: `trigger`, `repository`
    * `pull_request_assigned`: object:
      * `query`: string, minLength: 1
      * `paths`: array of string, minLength: 1
      * `assignees`: array of string
      * `write_scope`: string, enum: `trigger`, `repository`
    * `sub_issue_added`: object:
      * `query`: string, minLength: 1
      * `write_scope`: string, enum: `trigger`, `repository`
    * `pull_request_ready_for_review`: object:
      * `query`: string, minLength: 1
      * `paths`: array of string, minLength: 1
      * `write_scope`: string, enum: `trigger`, `repository`
    * `pull_request_labeled`: object:
      * `query`: string, minLength: 1
      * `paths`: array of string, minLength: 1
      * `labels`: array of string
      * `write_scope`: string, enum: `trigger`, `repository`
    * `pull_request_merge_conflict`: object:
      * `query`: string, minLength: 1
      * `paths`: array of string, minLength: 1
      * `write_scope`: string, enum: `trigger`, `repository`
    * `pull_request_review_submitted`: object:
      * `query`: string, minLength: 1
      * `paths`: array of string, minLength: 1
      * `states`: required, array of string, enum: `approved`, `changes_requested`, `commented`
      * `write_scope`: string, enum: `trigger`, `repository`
    * `pull_request_review_requested`: object:
      * `query`: string, minLength: 1
      * `paths`: array of string, minLength: 1
      * `write_scope`: string, enum: `trigger`, `repository`
    * `automation_completed`: object:
      * `automation_ids`: required, array of string
      * `write_scope`: string, enum: `trigger`, `repository`
  * `created_at`: required, string, format: date-time
  * `updated_at`: required, string, format: date-time
  * `created_by`: required, object:
    * `id`: integer, format: int64

## List available automation tools

```
GET /agents/automations/available-tools
```

Returns the tools available to the authenticated caller for use when creating or updating an automation.
Fine-grained access tokens for "List available automation tools"
This endpoint works with the following fine-grained token types:

GitHub App user access tokens
Fine-grained personal access tokens

This endpoint does not require repository permissions.
GitHub App installation access tokens are not supported for this endpoint.

### HTTP response status codes

- **200** - Available automation tools retrieved successfully

- **401** - Authentication required

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/agents/automations/available-tools
```

**Response schema (Status: 200):**

Array of objects:
  * `id`: required, string
  * `title`: required, string
  * `tools`: required, array of objects:
    * `id`: required, string
    * `title`: required, string
    * `description`: required, string
    * `scope`: string, enum: `read`, `write`

## List available automation triggers

```
GET /agents/automations/available-triggers
```

Returns the triggers available to the authenticated caller, including machine-readable schemas for their configurable fields.
Fine-grained access tokens for "List available automation triggers"
This endpoint works with the following fine-grained token types:

GitHub App user access tokens
Fine-grained personal access tokens

This endpoint does not require repository permissions.
GitHub App installation access tokens are not supported for this endpoint.

### HTTP response status codes

- **200** - Available automation triggers retrieved successfully

- **401** - Authentication required

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/agents/automations/available-triggers
```

**Response schema (Status: 200):**

Array of objects:
  * `id`: required, string
  * `title`: required, string
  * `description`: required, string
  * `fields`: required, array of objects:
    * `id`: required, string
    * `label`: required, string
    * `required`: required, boolean
    * `description`: string
    * `schema`: required, one of:
      * **object**
        * `type`: required, string, enum: `string`
        * `enum`: array of string
        * `minLength`: integer, minimum: 0
      * **object**
        * `type`: required, string, enum: `array`
        * `items`: required, object:
          * `type`: required, string, enum: `string`
          * `enum`: array of string
          * `minLength`: integer, minimum: 0
        * `minItems`: integer, minimum: 0
        * `maxItems`: integer, minimum: 0
        * `uniqueItems`: boolean
      * **object**
        * `type`: required, string, enum: `integer`
        * `enum`: array of integer
        * `minimum`: integer
        * `maximum`: integer
  * `supports_run_now`: boolean

## Get an automation by ID

```
GET /agents/automations/{automation_id}
```

Returns an automation by ID without requiring repository context when its created_by
user is the authenticated caller and the caller can read its repository. This includes
both user-owned and repository-owned automations created by the caller but excludes
repository-owned automations created by someone else even if the caller has write
access to the repository.
Use the repository-scoped get operation for those automations. The response includes
repository identity so clients can link back to the repository.
Fine-grained access tokens for "Get an automation by ID"
This endpoint works with the following fine-grained token types:

GitHub App user access tokens
Fine-grained personal access tokens

The fine-grained token must have one of the following permission sets for each
repository accessed by this request:

"Agent tasks" repository permissions (read)
"Contents" repository permissions (read)

The required permission set depends on each repository's Automation permission
configuration.
GitHub App installation access tokens are not supported for this endpoint.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`automation_id`** (string) (required)
  The unique identifier of the automation.

### HTTP response status codes

- **200** - Automation retrieved successfully

- **400** - Bad request

- **401** - Authentication required

- **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/agents/automations/AUTOMATION_ID
```

**Response schema (Status: 200):**

* `id`: required, string
* `repository`: required, object:
  * `id`: required, integer, format: int64
  * `owner`: required, string
  * `name`: required, string
* `name`: required, string
* `enabled`: boolean
* `owner_type`: string, enum: `user`, `repository`, read-only
* `write_scope`: string, enum: `trigger`, `repository`, default: `"trigger"`
* `require_actor_write_permission`: boolean, default: `false`
* `triggers`: object:
  * `interval`: object:
    * `cadence`: required, array of string, enum: `hourly`, `daily`, `weekly`
    * `hour_utc`: integer, minimum: 0, maximum: 23
    * `day_of_week`: integer, minimum: 0, maximum: 6
    * `minute_utc`: integer, enum: `0`, `15`, `30`, `45`, default: `0`
    * `write_scope`: string, enum: `trigger`, `repository`
  * `issue_opened`: object:
    * `query`: string, minLength: 1
    * `write_scope`: string, enum: `trigger`, `repository`
  * `issue_labeled`: object:
    * `query`: string, minLength: 1
    * `labels`: array of string
    * `write_scope`: string, enum: `trigger`, `repository`
  * `workflow_run`: object:
    * `workflows`: required, array of string, minLength: 1
    * `conclusions`: required, array of string, enum: `failure`
    * `query`: string, minLength: 1
    * `write_scope`: string, enum: `trigger`, `repository`
  * `pull_request_opened`: object:
    * `query`: string, minLength: 1
    * `paths`: array of string, minLength: 1
    * `write_scope`: string, enum: `trigger`, `repository`
  * `pull_request_synchronize`: object:
    * `query`: string, minLength: 1
    * `paths`: array of string, minLength: 1
    * `write_scope`: string, enum: `trigger`, `repository`
  * `pull_request_merged`: object:
    * `query`: string, minLength: 1
    * `paths`: array of string, minLength: 1
    * `write_scope`: string, enum: `trigger`, `repository`
  * `issue_comment`: object:
    * `body_substring`: string
    * `write_scope`: string, enum: `trigger`, `repository`
  * `pull_request_comment`: object:
    * `comment_types`: required, array of string, enum: `timeline_comment`, `review_comment`
    * `body_substring`: string
    * `write_scope`: string, enum: `trigger`, `repository`
  * `discussion_opened`: object:
    * `categories`: array of string
    * `body_substring`: string
    * `write_scope`: string, enum: `trigger`, `repository`
  * `discussion_updated`: object:
    * `categories`: array of string
    * `body_substring`: string
    * `write_scope`: string, enum: `trigger`, `repository`
  * `discussion_comment`: object:
    * `comment_types`: array of string, enum: `comment`, `reply`
    * `categories`: array of string
    * `body_substring`: string
    * `write_scope`: string, enum: `trigger`, `repository`
  * `issue_assigned`: object:
    * `query`: string, minLength: 1
    * `assignees`: array of string
    * `write_scope`: string, enum: `trigger`, `repository`
  * `pull_request_assigned`: object:
    * `query`: string, minLength: 1
    * `paths`: array of string, minLength: 1
    * `assignees`: array of string
    * `write_scope`: string, enum: `trigger`, `repository`
  * `sub_issue_added`: object:
    * `query`: string, minLength: 1
    * `write_scope`: string, enum: `trigger`, `repository`
  * `pull_request_ready_for_review`: object:
    * `query`: string, minLength: 1
    * `paths`: array of string, minLength: 1
    * `write_scope`: string, enum: `trigger`, `repository`
  * `pull_request_labeled`: object:
    * `query`: string, minLength: 1
    * `paths`: array of string, minLength: 1
    * `labels`: array of string
    * `write_scope`: string, enum: `trigger`, `repository`
  * `pull_request_merge_conflict`: object:
    * `query`: string, minLength: 1
    * `paths`: array of string, minLength: 1
    * `write_scope`: string, enum: `trigger`, `repository`
  * `pull_request_review_submitted`: object:
    * `query`: string, minLength: 1
    * `paths`: array of string, minLength: 1
    * `states`: required, array of string, enum: `approved`, `changes_requested`, `commented`
    * `write_scope`: string, enum: `trigger`, `repository`
  * `pull_request_review_requested`: object:
    * `query`: string, minLength: 1
    * `paths`: array of string, minLength: 1
    * `write_scope`: string, enum: `trigger`, `repository`
  * `automation_completed`: object:
    * `automation_ids`: required, array of string
    * `write_scope`: string, enum: `trigger`, `repository`
* `prompt`: required, string
* `tools`: array of string
* `allowed_custom_agents`: array of string
* `model`: string
* `reasoning_effort`: string
* `created_at`: required, string, format: date-time
* `updated_at`: required, string, format: date-time
* `created_by`: required, object:
  * `id`: integer, format: int64

## List tasks for an automation

```
GET /agents/automations/{automation_id}/tasks
```

Returns a list of tasks triggered by the specified automation.
User-owned automation history is available only to its creator, while repository-owned automation
history is available to anyone with read access to the repository. Deleted and unlisted tasks are excluded.
Tasks produced by private-session agents are excluded unless the caller created the task,
is a task collaborator, or the task is shared.
Fine-grained access tokens for "List tasks for an automation"
This endpoint works with the following fine-grained token types:

GitHub App user access tokens
Fine-grained personal access tokens

The fine-grained token must have one of the following permission sets for each
repository accessed by this request:

"Agent tasks" repository permissions (read)
"Contents" repository permissions (read)

The required permission set depends on each repository's Automation permission
configuration.
GitHub App installation access tokens are not supported for this endpoint.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`automation_id`** (string) (required)
  The unique identifier of the automation.

- **`per_page`** (integer)
  The number of results per page (max 100).
  Default: `30`

- **`page`** (integer)
  The page number of the results to fetch.
  Default: `1`

- **`sort`** (string)
  The field to sort results by. Can be updated_at or created_at.
  Default: `updated_at`
  Can be one of: `updated_at`, `created_at`

- **`direction`** (string)
  The direction to sort results. Can be asc or desc.
  Default: `desc`
  Can be one of: `asc`, `desc`

- **`state`** (string)
  Comma-separated list of task states to filter by. Can be any combination of: queued, in_progress, completed, failed, idle, waiting_for_user, timed_out, cancelled.

- **`is_archived`** (boolean)
  Filter by archived status. When true, returns only archived tasks. When false or omitted, returns only non-archived tasks. Defaults to false.
  Default: `false`

### HTTP response status codes

- **200** - Tasks retrieved successfully

- **401** - Authentication required

- **404** - Not found

- **422** - Validation Failed

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/agents/automations/AUTOMATION_ID/tasks
```

**Response schema (Status: 200):**

* `tasks`: required, array of objects:
  * `id`: required, string
  * `url`: string
  * `html_url`: string
  * `name`: string
  * `creator`: one of:
    * **object**
      * `id`: integer, format: int64
  * `creator_type`: string, enum: `user`, `organization`
  * `user_collaborators`: array of objects:
    * `id`: integer, format: int64
  * `owner`: object:
    * `id`: integer, format: int64
  * `repository`: object:
    * `id`: integer, format: int64
  * `state`: required, string, enum: `queued`, `in_progress`, `completed`, `failed`, `idle`, `waiting_for_user`, `timed_out`, `cancelled`
  * `session_count`: integer, format: int32
  * `artifacts`: array of objects:
    * `provider`: required, string, enum: `github`
    * `type`: required, string, enum: `pull`, `branch`
    * `data`: required, one of:
      * **object**
        * `id`: required, integer, format: int64
        * `global_id`: string
      * **object**
        * `head_ref`: required, string
        * `base_ref`: required, string
  * `archived_at`: string or null, format: date-time
  * `updated_at`: string, format: date-time
  * `created_at`: required, string, format: date-time
  * `custom_agent`: object:
    * `id`: string

## List automations for a repository

```
GET /agents/repos/{owner}/{repo}/automations
```

Returns a paginated list of the authenticated user's automations for a repository,
together with every repository-owned automation in it. total_count is the number of
caller-visible automations matching the supplied filters across all pages.
Repository-owned automations are visible to anyone with read access to the repository,
so the results are not limited to automations the caller created. Use the owner_type
field on each automation to tell the two apart.
Fine-grained access tokens for "List automations for a repository"
This endpoint works with the following fine-grained token types:

GitHub App user access tokens
Fine-grained personal access tokens

The fine-grained token must have one of the following permission sets for each
repository accessed by this request:

"Agent tasks" repository permissions (read)
"Contents" repository permissions (read)

The required permission set depends on each repository's Automation permission
configuration.
GitHub App installation access tokens are not supported for this endpoint.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository. The name is not case sensitive.

- **`page`** (integer)
  The page number of the results to fetch.
  Default: `1`

- **`per_page`** (integer)
  The number of results per page (max 100).
  Default: `30`

- **`owner_type`** (string)
  Filter automations by owner type. user returns automations owned by their creator, repository returns automations owned by the repository. Omit to return both.
  Can be one of: `user`, `repository`

### HTTP response status codes

- **200** - Automations retrieved successfully

- **400** - Bad request

- **401** - Authentication required

- **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/agents/repos/OWNER/REPO/automations
```

**Response schema (Status: 200):**

* `automations`: required, array of objects:
  * `id`: required, string
  * `name`: required, string
  * `enabled`: boolean
  * `owner_type`: string, enum: `user`, `repository`, read-only
  * `write_scope`: string, enum: `trigger`, `repository`, default: `"trigger"`
  * `require_actor_write_permission`: boolean, default: `false`
  * `model`: string
  * `reasoning_effort`: string
  * `triggers`: object:
    * `interval`: object:
      * `cadence`: required, array of string, enum: `hourly`, `daily`, `weekly`
      * `hour_utc`: integer, minimum: 0, maximum: 23
      * `day_of_week`: integer, minimum: 0, maximum: 6
      * `minute_utc`: integer, enum: `0`, `15`, `30`, `45`, default: `0`
      * `write_scope`: string, enum: `trigger`, `repository`
    * `issue_opened`: object:
      * `query`: string, minLength: 1
      * `write_scope`: string, enum: `trigger`, `repository`
    * `issue_labeled`: object:
      * `query`: string, minLength: 1
      * `labels`: array of string
      * `write_scope`: string, enum: `trigger`, `repository`
    * `workflow_run`: object:
      * `workflows`: required, array of string, minLength: 1
      * `conclusions`: required, array of string, enum: `failure`
      * `query`: string, minLength: 1
      * `write_scope`: string, enum: `trigger`, `repository`
    * `pull_request_opened`: object:
      * `query`: string, minLength: 1
      * `paths`: array of string, minLength: 1
      * `write_scope`: string, enum: `trigger`, `repository`
    * `pull_request_synchronize`: object:
      * `query`: string, minLength: 1
      * `paths`: array of string, minLength: 1
      * `write_scope`: string, enum: `trigger`, `repository`
    * `pull_request_merged`: object:
      * `query`: string, minLength: 1
      * `paths`: array of string, minLength: 1
      * `write_scope`: string, enum: `trigger`, `repository`
    * `issue_comment`: object:
      * `body_substring`: string
      * `write_scope`: string, enum: `trigger`, `repository`
    * `pull_request_comment`: object:
      * `comment_types`: required, array of string, enum: `timeline_comment`, `review_comment`
      * `body_substring`: string
      * `write_scope`: string, enum: `trigger`, `repository`
    * `discussion_opened`: object:
      * `categories`: array of string
      * `body_substring`: string
      * `write_scope`: string, enum: `trigger`, `repository`
    * `discussion_updated`: object:
      * `categories`: array of string
      * `body_substring`: string
      * `write_scope`: string, enum: `trigger`, `repository`
    * `discussion_comment`: object:
      * `comment_types`: array of string, enum: `comment`, `reply`
      * `categories`: array of string
      * `body_substring`: string
      * `write_scope`: string, enum: `trigger`, `repository`
    * `issue_assigned`: object:
      * `query`: string, minLength: 1
      * `assignees`: array of string
      * `write_scope`: string, enum: `trigger`, `repository`
    * `pull_request_assigned`: object:
      * `query`: string, minLength: 1
      * `paths`: array of string, minLength: 1
      * `assignees`: array of string
      * `write_scope`: string, enum: `trigger`, `repository`
    * `sub_issue_added`: object:
      * `query`: string, minLength: 1
      * `write_scope`: string, enum: `trigger`, `repository`
    * `pull_request_ready_for_review`: object:
      * `query`: string, minLength: 1
      * `paths`: array of string, minLength: 1
      * `write_scope`: string, enum: `trigger`, `repository`
    * `pull_request_labeled`: object:
      * `query`: string, minLength: 1
      * `paths`: array of string, minLength: 1
      * `labels`: array of string
      * `write_scope`: string, enum: `trigger`, `repository`
    * `pull_request_merge_conflict`: object:
      * `query`: string, minLength: 1
      * `paths`: array of string, minLength: 1
      * `write_scope`: string, enum: `trigger`, `repository`
    * `pull_request_review_submitted`: object:
      * `query`: string, minLength: 1
      * `paths`: array of string, minLength: 1
      * `states`: required, array of string, enum: `approved`, `changes_requested`, `commented`
      * `write_scope`: string, enum: `trigger`, `repository`
    * `pull_request_review_requested`: object:
      * `query`: string, minLength: 1
      * `paths`: array of string, minLength: 1
      * `write_scope`: string, enum: `trigger`, `repository`
    * `automation_completed`: object:
      * `automation_ids`: required, array of string
      * `write_scope`: string, enum: `trigger`, `repository`
  * `created_at`: required, string, format: date-time
  * `updated_at`: required, string, format: date-time
  * `created_by`: required, object:
    * `id`: integer, format: int64
* `total_count`: required, integer, format: int32

## Create an automation for a repository

```
POST /agents/repos/{owner}/{repo}/automations
```

Creates a new automation in a repository. User-owned automations remain private to
their creator. Repository-owned automations are visible to anyone with read access to
the repository and manageable by anyone with write access to the repository.
Fine-grained access tokens for "Create an automation for a repository"
This endpoint works with the following fine-grained token types:

GitHub App user access tokens
Fine-grained personal access tokens

The fine-grained token must have one of the following permission sets for each
repository accessed by this request:

"Agent tasks" repository permissions (read and write)
"Contents" repository permissions (read and write)

The required permission set depends on each repository's Automation permission
configuration.
GitHub App installation access tokens are not supported for this endpoint.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository. The name is not case sensitive.

#### Body parameters

- **`name`** (string) (required)
  The name of the automation.

- **`triggers`** (object)
  Public trigger configuration keyed by stable public trigger identifier. Each trigger has a closed, trigger-specific configuration schema.
  - **`interval`** (object)
    - **`cadence`** (array of strings) (required)
      One or more schedules on which the Automation runs.
Supported values are: hourly, daily, weekly
    - **`hour_utc`** (integer)
      UTC hour anchor (0 through 23) for daily and weekly schedules. Omitted daily and weekly values default to 0 (midnight UTC).
    - **`day_of_week`** (integer)
      UTC weekday anchor for weekly schedules, where 0 is Sunday and 6 is Saturday. Omitted weekly values default to Monday (1).
    - **`minute_utc`** (integer)
      UTC minute anchor for daily and weekly schedules. Omitted daily and weekly values default to 0. Must be omitted whenever cadence includes hourly.
      Default: `0`
      Can be one of: `0`, `15`, `30`, `45`
    - **`write_scope`** (string)
      Override the Automation write_scope for runs started by this trigger. If omitted, the automation's write_scope is used. Organization or repository policy may restrict the effective scope to trigger.
      Can be one of: `trigger`, `repository`
  - **`issue_opened`** (object)
    - **`query`** (string)
      A GitHub issue or pull request search query.
    - **`write_scope`** (string)
      Override the Automation write_scope for runs started by this trigger. If omitted, the automation's write_scope is used. Organization or repository policy may restrict the effective scope to trigger.
      Can be one of: `trigger`, `repository`
  - **`issue_labeled`** (object)
    - **`query`** (string)
      A GitHub issue or pull request search query.
    - **`labels`** (array of strings)
      Label names matched case-insensitively against the label added by the event. Omit or use an empty array to match every added label.
    - **`write_scope`** (string)
      Override the Automation write_scope for runs started by this trigger. If omitted, the automation's write_scope is used. Organization or repository policy may restrict the effective scope to trigger.
      Can be one of: `trigger`, `repository`
  - **`workflow_run`** (object)
    - **`workflows`** (array of strings) (required)
      Workflow names matched against the name in each workflow YAML file.
    - **`conclusions`** (array of strings) (required)
      Workflow conclusions to match. The current trigger supports failure.
Supported values are: failure
    - **`query`** (string)
      A GitHub issue or pull request search query.
    - **`write_scope`** (string)
      Override the Automation write_scope for runs started by this trigger. If omitted, the automation's write_scope is used. Organization or repository policy may restrict the effective scope to trigger.
      Can be one of: `trigger`, `repository`
  - **`pull_request_opened`** (object)
    - **`query`** (string)
      A GitHub issue or pull request search query.
    - **`paths`** (array of strings)
      Gitignore-style changed-file path globs.
    - **`write_scope`** (string)
      Override the Automation write_scope for runs started by this trigger. If omitted, the automation's write_scope is used. Organization or repository policy may restrict the effective scope to trigger.
      Can be one of: `trigger`, `repository`
  - **`pull_request_synchronize`** (object)
    - **`query`** (string)
      A GitHub issue or pull request search query.
    - **`paths`** (array of strings)
      Gitignore-style changed-file path globs.
    - **`write_scope`** (string)
      Override the Automation write_scope for runs started by this trigger. If omitted, the automation's write_scope is used. Organization or repository policy may restrict the effective scope to trigger.
      Can be one of: `trigger`, `repository`
  - **`pull_request_merged`** (object)
    - **`query`** (string)
      A GitHub issue or pull request search query.
    - **`paths`** (array of strings)
      Gitignore-style changed-file path globs.
    - **`write_scope`** (string)
      Override the Automation write_scope for runs started by this trigger. If omitted, the automation's write_scope is used. Organization or repository policy may restrict the effective scope to trigger.
      Can be one of: `trigger`, `repository`
  - **`issue_comment`** (object)
    - **`body_substring`** (string)
      A case-insensitive substring matched against the event body.
    - **`write_scope`** (string)
      Override the Automation write_scope for runs started by this trigger. If omitted, the automation's write_scope is used. Organization or repository policy may restrict the effective scope to trigger.
      Can be one of: `trigger`, `repository`
  - **`pull_request_comment`** (object)
    - **`comment_types`** (array of strings) (required)
      Pull request conversation and inline review comment types to match.
Supported values are: timeline_comment, review_comment
    - **`body_substring`** (string)
      A case-insensitive substring matched against the event body.
    - **`write_scope`** (string)
      Override the Automation write_scope for runs started by this trigger. If omitted, the automation's write_scope is used. Organization or repository policy may restrict the effective scope to trigger.
      Can be one of: `trigger`, `repository`
  - **`discussion_opened`** (object)
    - **`categories`** (array of strings)
      Discussion category names matched case-insensitively.
    - **`body_substring`** (string)
      A case-insensitive substring matched against the event body.
    - **`write_scope`** (string)
      Override the Automation write_scope for runs started by this trigger. If omitted, the automation's write_scope is used. Organization or repository policy may restrict the effective scope to trigger.
      Can be one of: `trigger`, `repository`
  - **`discussion_updated`** (object)
    - **`categories`** (array of strings)
      Discussion category names matched case-insensitively.
    - **`body_substring`** (string)
      A case-insensitive substring matched against the event body.
    - **`write_scope`** (string)
      Override the Automation write_scope for runs started by this trigger. If omitted, the automation's write_scope is used. Organization or repository policy may restrict the effective scope to trigger.
      Can be one of: `trigger`, `repository`
  - **`discussion_comment`** (object)
    - **`comment_types`** (array of strings)
      Top-level discussion comments and replies to match. Omit to match both.
Supported values are: comment, reply
    - **`categories`** (array of strings)
      Discussion category names matched case-insensitively.
    - **`body_substring`** (string)
      A case-insensitive substring matched against the event body.
    - **`write_scope`** (string)
      Override the Automation write_scope for runs started by this trigger. If omitted, the automation's write_scope is used. Organization or repository policy may restrict the effective scope to trigger.
      Can be one of: `trigger`, `repository`
  - **`issue_assigned`** (object)
    - **`query`** (string)
      A GitHub issue or pull request search query.
    - **`assignees`** (array of strings)
      Affected assignee logins matched case-insensitively.
    - **`write_scope`** (string)
      Override the Automation write_scope for runs started by this trigger. If omitted, the automation's write_scope is used. Organization or repository policy may restrict the effective scope to trigger.
      Can be one of: `trigger`, `repository`
  - **`pull_request_assigned`** (object)
    - **`query`** (string)
      A GitHub issue or pull request search query.
    - **`paths`** (array of strings)
      Gitignore-style changed-file path globs.
    - **`assignees`** (array of strings)
      Affected assignee logins matched case-insensitively.
    - **`write_scope`** (string)
      Override the Automation write_scope for runs started by this trigger. If omitted, the automation's write_scope is used. Organization or repository policy may restrict the effective scope to trigger.
      Can be one of: `trigger`, `repository`
  - **`sub_issue_added`** (object)
    - **`query`** (string)
      A GitHub issue or pull request search query.
    - **`write_scope`** (string)
      Override the Automation write_scope for runs started by this trigger. If omitted, the automation's write_scope is used. Organization or repository policy may restrict the effective scope to trigger.
      Can be one of: `trigger`, `repository`
  - **`pull_request_ready_for_review`** (object)
    - **`query`** (string)
      A GitHub issue or pull request search query.
    - **`paths`** (array of strings)
      Gitignore-style changed-file path globs.
    - **`write_scope`** (string)
      Override the Automation write_scope for runs started by this trigger. If omitted, the automation's write_scope is used. Organization or repository policy may restrict the effective scope to trigger.
      Can be one of: `trigger`, `repository`
  - **`pull_request_labeled`** (object)
    - **`query`** (string)
      A GitHub issue or pull request search query.
    - **`paths`** (array of strings)
      Gitignore-style changed-file path globs.
    - **`labels`** (array of strings)
      Label names matched case-insensitively against the label added by the event. Omit or use an empty array to match every added label.
    - **`write_scope`** (string)
      Override the Automation write_scope for runs started by this trigger. If omitted, the automation's write_scope is used. Organization or repository policy may restrict the effective scope to trigger.
      Can be one of: `trigger`, `repository`
  - **`pull_request_merge_conflict`** (object)
    - **`query`** (string)
      A GitHub issue or pull request search query.
    - **`paths`** (array of strings)
      Gitignore-style changed-file path globs.
    - **`write_scope`** (string)
      Override the Automation write_scope for runs started by this trigger. If omitted, the automation's write_scope is used. Organization or repository policy may restrict the effective scope to trigger.
      Can be one of: `trigger`, `repository`
  - **`pull_request_review_submitted`** (object)
    - **`query`** (string)
      A GitHub issue or pull request search query.
    - **`paths`** (array of strings)
      Gitignore-style changed-file path globs.
    - **`states`** (array of strings) (required)
      Submitted review states to match.
Supported values are: approved, changes_requested, commented
    - **`write_scope`** (string)
      Override the Automation write_scope for runs started by this trigger. If omitted, the automation's write_scope is used. Organization or repository policy may restrict the effective scope to trigger.
      Can be one of: `trigger`, `repository`
  - **`pull_request_review_requested`** (object)
    - **`query`** (string)
      A GitHub issue or pull request search query.
    - **`paths`** (array of strings)
      Gitignore-style changed-file path globs.
    - **`write_scope`** (string)
      Override the Automation write_scope for runs started by this trigger. If omitted, the automation's write_scope is used. Organization or repository policy may restrict the effective scope to trigger.
      Can be one of: `trigger`, `repository`
  - **`automation_completed`** (object)
    - **`automation_ids`** (array of strings) (required)
      Upstream Automation IDs in the same repository.
    - **`write_scope`** (string)
      Override the Automation write_scope for runs started by this trigger. If omitted, the automation's write_scope is used. Organization or repository policy may restrict the effective scope to trigger.
      Can be one of: `trigger`, `repository`

- **`prompt`** (string) (required)
  The prompt template for the automation.

- **`model`** (string)
  The model to use for sessions triggered by this automation. Omit to use the platform default.

- **`reasoning_effort`** (string)
  The reasoning effort to use for sessions triggered by this automation. Omit or leave empty for no override. Currently supported values: none, low, medium, high, xhigh, max

- **`tools`** (array of strings)
  The tools available to the automation.

- **`allowed_custom_agents`** (array of strings)
  Custom agents (subagents) this automation is allowed to invoke.

- **`enabled`** (boolean)
  Whether the automation should be created enabled. Defaults to true when omitted.
  Default: `true`

- **`owner_type`** (string)
  Who owns the automation, fixed at creation. user keeps it private to its creator and its runs act as that user. repository makes it belong to the repository, visible to anyone with read access to the repository and maintainable by anyone with write access to the repository, and its runs act as the Copilot app rather than as a person. repository is rejected when repository ownership is not available for the repository. Supported values: user, repository. Defaults to user.
  Default: `user`
  Can be one of: `user`, `repository`

- **`write_scope`** (string)
  Controls which repository resources a run may modify. trigger limits writes to the resource that started the run, when one exists, and resources created during the run; repository allows writes to any resource in the repository. Supported values: trigger, repository.
  Default: `trigger`
  Can be one of: `trigger`, `repository`

- **`require_actor_write_permission`** (boolean)
  When true, event-triggered runs require the event actor to have repo write permission, even when the org's allow_read_access_triggers policy is enabled. Does not apply to interval-scheduled runs, which always run as the automation owner. Defaults to false.

### HTTP response status codes

- **201** - Automation created successfully

- **400** - Bad request

- **401** - Authentication required

- **403** - Insufficient permissions

- **404** - Resource not found

- **422** - Validation Failed

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/agents/repos/OWNER/REPO/automations \
  -d '{
  "name": "Issue triage",
  "enabled": true,
  "owner_type": "user",
  "triggers": {
    "issue_opened": {
      "query": "is:open"
    }
  },
  "prompt": "Inspect the new issue and suggest labels, priority, and next steps.",
  "tools": [
    "github/get_file_contents",
    "github/issue_read"
  ],
  "model": "gpt-5.4",
  "reasoning_effort": "high"
}'
```

**Response schema (Status: 201):**

* `id`: required, string
* `name`: required, string
* `enabled`: boolean
* `owner_type`: string, enum: `user`, `repository`, read-only
* `write_scope`: string, enum: `trigger`, `repository`, default: `"trigger"`
* `require_actor_write_permission`: boolean, default: `false`
* `triggers`: object:
  * `interval`: object:
    * `cadence`: required, array of string, enum: `hourly`, `daily`, `weekly`
    * `hour_utc`: integer, minimum: 0, maximum: 23
    * `day_of_week`: integer, minimum: 0, maximum: 6
    * `minute_utc`: integer, enum: `0`, `15`, `30`, `45`, default: `0`
    * `write_scope`: string, enum: `trigger`, `repository`
  * `issue_opened`: object:
    * `query`: string, minLength: 1
    * `write_scope`: string, enum: `trigger`, `repository`
  * `issue_labeled`: object:
    * `query`: string, minLength: 1
    * `labels`: array of string
    * `write_scope`: string, enum: `trigger`, `repository`
  * `workflow_run`: object:
    * `workflows`: required, array of string, minLength: 1
    * `conclusions`: required, array of string, enum: `failure`
    * `query`: string, minLength: 1
    * `write_scope`: string, enum: `trigger`, `repository`
  * `pull_request_opened`: object:
    * `query`: string, minLength: 1
    * `paths`: array of string, minLength: 1
    * `write_scope`: string, enum: `trigger`, `repository`
  * `pull_request_synchronize`: object:
    * `query`: string, minLength: 1
    * `paths`: array of string, minLength: 1
    * `write_scope`: string, enum: `trigger`, `repository`
  * `pull_request_merged`: object:
    * `query`: string, minLength: 1
    * `paths`: array of string, minLength: 1
    * `write_scope`: string, enum: `trigger`, `repository`
  * `issue_comment`: object:
    * `body_substring`: string
    * `write_scope`: string, enum: `trigger`, `repository`
  * `pull_request_comment`: object:
    * `comment_types`: required, array of string, enum: `timeline_comment`, `review_comment`
    * `body_substring`: string
    * `write_scope`: string, enum: `trigger`, `repository`
  * `discussion_opened`: object:
    * `categories`: array of string
    * `body_substring`: string
    * `write_scope`: string, enum: `trigger`, `repository`
  * `discussion_updated`: object:
    * `categories`: array of string
    * `body_substring`: string
    * `write_scope`: string, enum: `trigger`, `repository`
  * `discussion_comment`: object:
    * `comment_types`: array of string, enum: `comment`, `reply`
    * `categories`: array of string
    * `body_substring`: string
    * `write_scope`: string, enum: `trigger`, `repository`
  * `issue_assigned`: object:
    * `query`: string, minLength: 1
    * `assignees`: array of string
    * `write_scope`: string, enum: `trigger`, `repository`
  * `pull_request_assigned`: object:
    * `query`: string, minLength: 1
    * `paths`: array of string, minLength: 1
    * `assignees`: array of string
    * `write_scope`: string, enum: `trigger`, `repository`
  * `sub_issue_added`: object:
    * `query`: string, minLength: 1
    * `write_scope`: string, enum: `trigger`, `repository`
  * `pull_request_ready_for_review`: object:
    * `query`: string, minLength: 1
    * `paths`: array of string, minLength: 1
    * `write_scope`: string, enum: `trigger`, `repository`
  * `pull_request_labeled`: object:
    * `query`: string, minLength: 1
    * `paths`: array of string, minLength: 1
    * `labels`: array of string
    * `write_scope`: string, enum: `trigger`, `repository`
  * `pull_request_merge_conflict`: object:
    * `query`: string, minLength: 1
    * `paths`: array of string, minLength: 1
    * `write_scope`: string, enum: `trigger`, `repository`
  * `pull_request_review_submitted`: object:
    * `query`: string, minLength: 1
    * `paths`: array of string, minLength: 1
    * `states`: required, array of string, enum: `approved`, `changes_requested`, `commented`
    * `write_scope`: string, enum: `trigger`, `repository`
  * `pull_request_review_requested`: object:
    * `query`: string, minLength: 1
    * `paths`: array of string, minLength: 1
    * `write_scope`: string, enum: `trigger`, `repository`
  * `automation_completed`: object:
    * `automation_ids`: required, array of string
    * `write_scope`: string, enum: `trigger`, `repository`
* `prompt`: required, string
* `tools`: array of string
* `allowed_custom_agents`: array of string
* `model`: string
* `reasoning_effort`: string
* `created_at`: required, string, format: date-time
* `updated_at`: required, string, format: date-time
* `created_by`: required, object:
  * `id`: integer, format: int64

## Get an automation for a repository

```
GET /agents/repos/{owner}/{repo}/automations/{automation_id}
```

Returns an automation by ID in a repository.
User-owned automations are visible only to their creator. Repository-owned
automations are visible to anyone with read access to the repository. The
created_by field identifies the creator and is distinct from the automation's
owner_type.
Fine-grained access tokens for "Get an automation for a repository"
This endpoint works with the following fine-grained token types:

GitHub App user access tokens
Fine-grained personal access tokens

The fine-grained token must have one of the following permission sets for each
repository accessed by this request:

"Agent tasks" repository permissions (read)
"Contents" repository permissions (read)

The required permission set depends on each repository's Automation permission
configuration.
GitHub App installation access tokens are not supported for this endpoint.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository. The name is not case sensitive.

- **`automation_id`** (string) (required)
  The unique identifier of the automation.

### HTTP response status codes

- **200** - Automation retrieved successfully

- **400** - Bad request

- **401** - Authentication required

- **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/agents/repos/OWNER/REPO/automations/AUTOMATION_ID
```

**Response schema (Status: 200):**

Same response schema as [Create an automation for a repository](#create-an-automation-for-a-repository).

## Edit an automation for a repository

```
PATCH /agents/repos/{owner}/{repo}/automations/{automation_id}
```

Edits specified fields on an existing automation in a repository. Omitted fields
are left unchanged.
The automation's owner_type is immutable and cannot be changed by this operation.
Fine-grained access tokens for "Edit an automation for a repository"
This endpoint works with the following fine-grained token types:

GitHub App user access tokens
Fine-grained personal access tokens

The fine-grained token must have one of the following permission sets for each
repository accessed by this request:

"Agent tasks" repository permissions (read and write)
"Contents" repository permissions (read and write)

The required permission set depends on each repository's Automation permission
configuration.
GitHub App installation access tokens are not supported for this endpoint.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository. The name is not case sensitive.

- **`automation_id`** (string) (required)
  The unique identifier of the automation.

#### Body parameters

- **`name`** (string)
  The name of the automation.

- **`enabled`** (boolean)
  Set to true to enable, false to disable. Omit to leave unchanged.

- **`write_scope`** (string)
  Controls which repository resources a run may modify. trigger limits writes to the resource that started the run, when one exists, and resources created during the run; repository allows writes to any resource in the repository. Supported values: trigger, repository. Omit to leave unchanged.
  Can be one of: `trigger`, `repository`

- **`require_actor_write_permission`** (boolean)
  When true, event-triggered runs require the event actor to have repo write permission, even when the org's allow_read_access_triggers policy is enabled. Does not apply to interval-scheduled runs, which always run as the automation owner. Omit to leave unchanged.

- **`model`** (string)
  The model to use for sessions triggered by this automation. Omit to leave unchanged. Send an empty string to clear the model and revert to the platform default.

- **`reasoning_effort`** (string)
  The reasoning effort to use for sessions triggered by this automation. Omit to leave unchanged. Send an empty string to clear the override. Currently supported values: none, low, medium, high, xhigh, max

- **`triggers`** (object)
  Public trigger configuration keyed by stable public trigger identifier. Each trigger has a closed, trigger-specific configuration schema.
  - **`interval`** (object)
    - **`cadence`** (array of strings) (required)
      One or more schedules on which the Automation runs.
Supported values are: hourly, daily, weekly
    - **`hour_utc`** (integer)
      UTC hour anchor (0 through 23) for daily and weekly schedules. Omitted daily and weekly values default to 0 (midnight UTC).
    - **`day_of_week`** (integer)
      UTC weekday anchor for weekly schedules, where 0 is Sunday and 6 is Saturday. Omitted weekly values default to Monday (1).
    - **`minute_utc`** (integer)
      UTC minute anchor for daily and weekly schedules. Omitted daily and weekly values default to 0. Must be omitted whenever cadence includes hourly.
      Default: `0`
      Can be one of: `0`, `15`, `30`, `45`
    - **`write_scope`** (string)
      Override the Automation write_scope for runs started by this trigger. If omitted, the automation's write_scope is used. Organization or repository policy may restrict the effective scope to trigger.
      Can be one of: `trigger`, `repository`
  - **`issue_opened`** (object)
    - **`query`** (string)
      A GitHub issue or pull request search query.
    - **`write_scope`** (string)
      Override the Automation write_scope for runs started by this trigger. If omitted, the automation's write_scope is used. Organization or repository policy may restrict the effective scope to trigger.
      Can be one of: `trigger`, `repository`
  - **`issue_labeled`** (object)
    - **`query`** (string)
      A GitHub issue or pull request search query.
    - **`labels`** (array of strings)
      Label names matched case-insensitively against the label added by the event. Omit or use an empty array to match every added label.
    - **`write_scope`** (string)
      Override the Automation write_scope for runs started by this trigger. If omitted, the automation's write_scope is used. Organization or repository policy may restrict the effective scope to trigger.
      Can be one of: `trigger`, `repository`
  - **`workflow_run`** (object)
    - **`workflows`** (array of strings) (required)
      Workflow names matched against the name in each workflow YAML file.
    - **`conclusions`** (array of strings) (required)
      Workflow conclusions to match. The current trigger supports failure.
Supported values are: failure
    - **`query`** (string)
      A GitHub issue or pull request search query.
    - **`write_scope`** (string)
      Override the Automation write_scope for runs started by this trigger. If omitted, the automation's write_scope is used. Organization or repository policy may restrict the effective scope to trigger.
      Can be one of: `trigger`, `repository`
  - **`pull_request_opened`** (object)
    - **`query`** (string)
      A GitHub issue or pull request search query.
    - **`paths`** (array of strings)
      Gitignore-style changed-file path globs.
    - **`write_scope`** (string)
      Override the Automation write_scope for runs started by this trigger. If omitted, the automation's write_scope is used. Organization or repository policy may restrict the effective scope to trigger.
      Can be one of: `trigger`, `repository`
  - **`pull_request_synchronize`** (object)
    - **`query`** (string)
      A GitHub issue or pull request search query.
    - **`paths`** (array of strings)
      Gitignore-style changed-file path globs.
    - **`write_scope`** (string)
      Override the Automation write_scope for runs started by this trigger. If omitted, the automation's write_scope is used. Organization or repository policy may restrict the effective scope to trigger.
      Can be one of: `trigger`, `repository`
  - **`pull_request_merged`** (object)
    - **`query`** (string)
      A GitHub issue or pull request search query.
    - **`paths`** (array of strings)
      Gitignore-style changed-file path globs.
    - **`write_scope`** (string)
      Override the Automation write_scope for runs started by this trigger. If omitted, the automation's write_scope is used. Organization or repository policy may restrict the effective scope to trigger.
      Can be one of: `trigger`, `repository`
  - **`issue_comment`** (object)
    - **`body_substring`** (string)
      A case-insensitive substring matched against the event body.
    - **`write_scope`** (string)
      Override the Automation write_scope for runs started by this trigger. If omitted, the automation's write_scope is used. Organization or repository policy may restrict the effective scope to trigger.
      Can be one of: `trigger`, `repository`
  - **`pull_request_comment`** (object)
    - **`comment_types`** (array of strings) (required)
      Pull request conversation and inline review comment types to match.
Supported values are: timeline_comment, review_comment
    - **`body_substring`** (string)
      A case-insensitive substring matched against the event body.
    - **`write_scope`** (string)
      Override the Automation write_scope for runs started by this trigger. If omitted, the automation's write_scope is used. Organization or repository policy may restrict the effective scope to trigger.
      Can be one of: `trigger`, `repository`
  - **`discussion_opened`** (object)
    - **`categories`** (array of strings)
      Discussion category names matched case-insensitively.
    - **`body_substring`** (string)
      A case-insensitive substring matched against the event body.
    - **`write_scope`** (string)
      Override the Automation write_scope for runs started by this trigger. If omitted, the automation's write_scope is used. Organization or repository policy may restrict the effective scope to trigger.
      Can be one of: `trigger`, `repository`
  - **`discussion_updated`** (object)
    - **`categories`** (array of strings)
      Discussion category names matched case-insensitively.
    - **`body_substring`** (string)
      A case-insensitive substring matched against the event body.
    - **`write_scope`** (string)
      Override the Automation write_scope for runs started by this trigger. If omitted, the automation's write_scope is used. Organization or repository policy may restrict the effective scope to trigger.
      Can be one of: `trigger`, `repository`
  - **`discussion_comment`** (object)
    - **`comment_types`** (array of strings)
      Top-level discussion comments and replies to match. Omit to match both.
Supported values are: comment, reply
    - **`categories`** (array of strings)
      Discussion category names matched case-insensitively.
    - **`body_substring`** (string)
      A case-insensitive substring matched against the event body.
    - **`write_scope`** (string)
      Override the Automation write_scope for runs started by this trigger. If omitted, the automation's write_scope is used. Organization or repository policy may restrict the effective scope to trigger.
      Can be one of: `trigger`, `repository`
  - **`issue_assigned`** (object)
    - **`query`** (string)
      A GitHub issue or pull request search query.
    - **`assignees`** (array of strings)
      Affected assignee logins matched case-insensitively.
    - **`write_scope`** (string)
      Override the Automation write_scope for runs started by this trigger. If omitted, the automation's write_scope is used. Organization or repository policy may restrict the effective scope to trigger.
      Can be one of: `trigger`, `repository`
  - **`pull_request_assigned`** (object)
    - **`query`** (string)
      A GitHub issue or pull request search query.
    - **`paths`** (array of strings)
      Gitignore-style changed-file path globs.
    - **`assignees`** (array of strings)
      Affected assignee logins matched case-insensitively.
    - **`write_scope`** (string)
      Override the Automation write_scope for runs started by this trigger. If omitted, the automation's write_scope is used. Organization or repository policy may restrict the effective scope to trigger.
      Can be one of: `trigger`, `repository`
  - **`sub_issue_added`** (object)
    - **`query`** (string)
      A GitHub issue or pull request search query.
    - **`write_scope`** (string)
      Override the Automation write_scope for runs started by this trigger. If omitted, the automation's write_scope is used. Organization or repository policy may restrict the effective scope to trigger.
      Can be one of: `trigger`, `repository`
  - **`pull_request_ready_for_review`** (object)
    - **`query`** (string)
      A GitHub issue or pull request search query.
    - **`paths`** (array of strings)
      Gitignore-style changed-file path globs.
    - **`write_scope`** (string)
      Override the Automation write_scope for runs started by this trigger. If omitted, the automation's write_scope is used. Organization or repository policy may restrict the effective scope to trigger.
      Can be one of: `trigger`, `repository`
  - **`pull_request_labeled`** (object)
    - **`query`** (string)
      A GitHub issue or pull request search query.
    - **`paths`** (array of strings)
      Gitignore-style changed-file path globs.
    - **`labels`** (array of strings)
      Label names matched case-insensitively against the label added by the event. Omit or use an empty array to match every added label.
    - **`write_scope`** (string)
      Override the Automation write_scope for runs started by this trigger. If omitted, the automation's write_scope is used. Organization or repository policy may restrict the effective scope to trigger.
      Can be one of: `trigger`, `repository`
  - **`pull_request_merge_conflict`** (object)
    - **`query`** (string)
      A GitHub issue or pull request search query.
    - **`paths`** (array of strings)
      Gitignore-style changed-file path globs.
    - **`write_scope`** (string)
      Override the Automation write_scope for runs started by this trigger. If omitted, the automation's write_scope is used. Organization or repository policy may restrict the effective scope to trigger.
      Can be one of: `trigger`, `repository`
  - **`pull_request_review_submitted`** (object)
    - **`query`** (string)
      A GitHub issue or pull request search query.
    - **`paths`** (array of strings)
      Gitignore-style changed-file path globs.
    - **`states`** (array of strings) (required)
      Submitted review states to match.
Supported values are: approved, changes_requested, commented
    - **`write_scope`** (string)
      Override the Automation write_scope for runs started by this trigger. If omitted, the automation's write_scope is used. Organization or repository policy may restrict the effective scope to trigger.
      Can be one of: `trigger`, `repository`
  - **`pull_request_review_requested`** (object)
    - **`query`** (string)
      A GitHub issue or pull request search query.
    - **`paths`** (array of strings)
      Gitignore-style changed-file path globs.
    - **`write_scope`** (string)
      Override the Automation write_scope for runs started by this trigger. If omitted, the automation's write_scope is used. Organization or repository policy may restrict the effective scope to trigger.
      Can be one of: `trigger`, `repository`
  - **`automation_completed`** (object)
    - **`automation_ids`** (array of strings) (required)
      Upstream Automation IDs in the same repository.
    - **`write_scope`** (string)
      Override the Automation write_scope for runs started by this trigger. If omitted, the automation's write_scope is used. Organization or repository policy may restrict the effective scope to trigger.
      Can be one of: `trigger`, `repository`

- **`prompt`** (string)
  The prompt template for the automation.

- **`tools`** (array of strings)
  The tools available to the automation. Send an empty array to clear all tools.

- **`allowed_custom_agents`** (array of strings)
  Custom agents (subagents) this automation is allowed to invoke. Send an empty array to clear all custom agents.

### HTTP response status codes

- **200** - Automation updated successfully

- **400** - Bad request

- **401** - Authentication required

- **404** - Resource not found

- **422** - Validation Failed

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/agents/repos/OWNER/REPO/automations/AUTOMATION_ID \
  -d '{
  "name": "Issue triage and prioritization",
  "enabled": true,
  "model": "gpt-5.4",
  "reasoning_effort": "high",
  "triggers": {
    "issue_opened": {
      "query": "is:open label:auto-triage"
    }
  }
}'
```

**Response schema (Status: 200):**

Same response schema as [Create an automation for a repository](#create-an-automation-for-a-repository).

## Delete an automation for a repository

```
DELETE /agents/repos/{owner}/{repo}/automations/{automation_id}
```

Deletes an automation in a repository.
Fine-grained access tokens for "Delete an automation for a repository"
This endpoint works with the following fine-grained token types:

GitHub App user access tokens
Fine-grained personal access tokens

The fine-grained token must have one of the following permission sets for each
repository accessed by this request:

"Agent tasks" repository permissions (read and write)
"Contents" repository permissions (read and write)

The required permission set depends on each repository's Automation permission
configuration.
GitHub App installation access tokens are not supported for this endpoint.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository. The name is not case sensitive.

- **`automation_id`** (string) (required)
  The unique identifier of the automation.

### HTTP response status codes

- **204** - Automation deleted successfully

- **400** - Bad request

- **401** - Authentication required

- **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/agents/repos/OWNER/REPO/automations/AUTOMATION_ID
```

**Response schema (Status: 204):**