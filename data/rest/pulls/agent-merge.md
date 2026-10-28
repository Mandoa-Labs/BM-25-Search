# REST API endpoints for Agent Merge

Use the REST API to get, update, and disable Agent Merge for pull requests.

> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## Get Agent Merge configuration for a pull request

```
GET /agents/repos/{owner}/{repo}/pulls/{pull_number}/agent-merge
```

Gets the Agent Merge configuration for a pull request.
You must have write access to the repository.
OAuth app tokens and personal access tokens (classic) need the repo scope for private or internal repositories, or the public_repo scope for public repositories.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository. The name is not case sensitive.

- **`pull_number`** (integer) (required)
  The number that identifies the pull request.

### HTTP response status codes

- **200** - Stored configuration retrieved successfully

- **401** - Authentication required

- **403** - Caller is not permitted to read this enrollment

- **404** - Resource or enrollment is absent, enrollment is disabled, or access is masked as not found

- **422** - Invalid request parameters

- **429** - Rate limit exceeded

- **503** - Enrollment storage or an authorization dependency is unavailable

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/agents/repos/OWNER/REPO/pulls/PULL_NUMBER/agent-merge
```

**Response schema (Status: 200):**

* `allowed_actions`: required, array of string, enum: `fix_ci`, `resolve_merge_conflicts`
* `created_at`: required, string, format: date-time
* `updated_at`: required, string, format: date-time
* `user`: required, object:
  * `id`: required, integer, format: int64, minimum: 1

## Update Agent Merge configuration for a pull request

```
PUT /agents/repos/{owner}/{repo}/pulls/{pull_number}/agent-merge
```

Updates the Agent Merge configuration for a pull request, enabling Agent Merge
or changing the allowed actions that Copilot is allowed to take on the pull
request.
If Agent Merge is currently enabled for the pull request, only the user
who most recently enabled it may change its allowed actions.
If enrollment eligibility cannot be determined, the operation returns 503.
This endpoint is only available to users with a Copilot subscription,
excluding Copilot Free users. You must have write access to the repository,
the pull request must not be from a fork or part of a stack, and the repository
must have the "Allow automations" setting enabled.
OAuth app tokens and personal access tokens (classic) need the repo scope for private or internal repositories, or the public_repo scope for public repositories.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository. The name is not case sensitive.

- **`pull_number`** (integer) (required)
  The number that identifies the pull request.

#### Body parameters

- **`allowed_actions`** (array of strings) (required)
  The set of actions that Copilot may perform on the pull request.
  Supported values are: fix_ci, resolve_merge_conflicts

### HTTP response status codes

- **200** - Existing Agent Merge enrollment updated

- **201** - Pull request enrolled for Agent Merge

- **400** - Malformed JSON request body

- **401** - Authentication required

- **403** - Caller lacks the permissions or eligibility to enroll the pull request for Agent Merge

- **404** - Resource is absent or masked as not found

- **409** - Enrollment changed during the write; no replacement was committed

- **422** - Ineligible pull request, invalid action selection, or unknown body properties

- **429** - Rate limit exceeded

- **503** - Enrollment storage or an authorization dependency is unavailable, or eligibility is unknown

### Code examples

#### Only ask Copilot to fix failing Actions workflows

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/agents/repos/OWNER/REPO/pulls/PULL_NUMBER/agent-merge \
  -d '{
  "allowed_actions": [
    "fix_ci"
  ]
}'
```

**Response schema (Status: 201):**

Same response schema as [Get Agent Merge configuration for a pull request](#get-agent-merge-configuration-for-a-pull-request).

#### Ask Copilot to fix failing Actions workflows and resolve merge conflicts

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/agents/repos/OWNER/REPO/pulls/PULL_NUMBER/agent-merge \
  -d '{
  "allowed_actions": [
    "fix_ci",
    "resolve_merge_conflicts"
  ]
}'
```

**Response schema (Status: 201):**

Same response schema as [Get Agent Merge configuration for a pull request](#get-agent-merge-configuration-for-a-pull-request).

## Disable Agent Merge for a pull request

```
DELETE /agents/repos/{owner}/{repo}/pulls/{pull_number}/agent-merge
```

Disables Agent Merge for a pull request.
You must have write access to the repository. Disabling does not require
enrollment eligibility: your Copilot subscription, coding-agent and Automations
policies, the Agent Merge execution flag, pull request state, stack membership,
and repository archive state do not prevent cleanup. Authentication, token
repository selection, and "Agent tasks" write permission remain required.
OAuth app tokens and personal access tokens (classic) need the repo scope for private or internal repositories, or the public_repo scope for public repositories.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository. The name is not case sensitive.

- **`pull_number`** (integer) (required)
  The number that identifies the pull request.

### HTTP response status codes

- **204** - Agent Merge successfully disabled for the pull request

- **401** - Authentication required

- **403** - Caller lacks write permission

- **404** - Resource or enrollment is absent or masked as not found

- **409** - Enrollment changed during the write; no replacement was committed

- **422** - Invalid request parameters

- **429** - Rate limit exceeded

- **503** - Enrollment storage, authorization, or required publication is unavailable

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/agents/repos/OWNER/REPO/pulls/PULL_NUMBER/agent-merge
```

**Response schema (Status: 204):**