# REST API endpoints for planning statuses

Use the REST API to list the planning statuses that issues in a repository can have. Issue statuses are in preview and only available to accounts enrolled in the preview.

> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## List planning statuses for a repository

```
GET /repos/{owner}/{repo}/planning-statuses
```

Lists the selectable planning statuses available.
Planning statuses are returned in deterministic display order:
Backlog, Todo, In progress, In review, Done, Not planned, and Duplicate.
Clients should expect new keys to be added.
Returns 404 Not Found when issue statuses aren't available in the repository.
Note

Issue statuses are in preview and subject to change. They're only available to accounts enrolled in the preview.

You need read access to the repository's issues to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the repo scope
to use this endpoint with a private repository.
Fine-grained access tokens require the "Issues" repository permission (read).

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

- **200** - Available planning statuses in display order

- **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/planning-statuses
```

**Response schema (Status: 200):**

Array of `Planning status`:
  * `id`: required, integer, format: int64
  * `name`: required, string
  * `category`: required, string