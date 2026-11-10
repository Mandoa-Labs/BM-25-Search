# REST API endpoints for Copilot code review

Use the REST API to manage Copilot code review.

> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## Request a Copilot code review for a pull request

```
POST /repos/{owner}/{repo}/pulls/{pull_number}/copilot-code-review
```

Requests a Copilot code review for a pull request. Every call expresses intent to start a
new review: if no Copilot review has been requested yet, an initial request is created; if
the most recent Copilot review has already completed (including if it was later dismissed or
superseded), a new request is created automatically to continue the review lifecycle. If a
Copilot code review request is already pending for the pull request, no new request is
created and the response is 409.
If the actor or repository is not eligible for Copilot code review, the actor has no quota
remaining, or the licensing organization is unavailable, no request is created and the
response is 422 with a stable failure_reason. A review_effort is accepted only when that
effort level is available for the repository and actor; an unrecognized or unavailable
review_effort returns 422 with failure_reason INVALID_REVIEW_EFFORT. If
the actor, repository owner, or requesting application owner has been flagged, the response
is 403 with failure_reason ACTOR_FLAGGED. If the per-actor or per-owner request rate
limit is exceeded, the response is 429 with failure_reason RATE_LIMITED. If Copilot
code review cannot be serviced right now, the response is 503.
Existing human and team review requests on the pull request are left unchanged.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

- **`pull_number`** (integer) (required)
  The number that identifies the pull request.

#### Body parameters

- **`review_effort`** (string)
  The effort level to use for the Copilot code review. Omit to use the default effort level. Only effort levels available for the repository and actor are accepted. For more information, see Review effort level.

### HTTP response status codes

- **201** - Created

- **401** - Requires authentication

- **403** - Forbidden. failure_reason is ACTOR_FLAGGED when the actor, repository owner, or requesting application owner has been flagged; it is absent for other authorization failures.

- **404** - Resource not found

- **409** - Conflict, a Copilot code review request is already pending for this pull request

- **422** - Validation failed. failure_reason is present for a stable business denial (the actor or repository is not eligible, the actor has no quota remaining, or the licensing organization is unavailable) and absent when the request body fails generic request validation. failure_reason is INVALID_REVIEW_EFFORT when the requested review_effort is unrecognized or not available for the repository and actor, and message lists the available effort levels.

- **429** - Too many requests. The per-actor or per-owner Copilot code review request rate limit has been exceeded. failure_reason is RATE_LIMITED.

- **503** - Service unavailable, Copilot code review cannot be serviced right now

### Code examples

#### Request a review with a specific effort level

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/pulls/PULL_NUMBER/copilot-code-review \
  -d '{
  "review_effort": "balanced"
}'
```

**Response schema (Status: 201):**

* `node_id`: required, string
* `state`: required, string, enum: `PENDING`