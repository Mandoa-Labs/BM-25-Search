# REST API endpoints for issue types

Use the REST API to manage issue types for a repository.

> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## List issue types for a repository

```
GET /repos/{owner}/{repo}/issue-types
```

Lists issue types available for a repository (inherited from its organization owner, with any per-repository overrides applied).
OAuth app tokens and personal access tokens (classic) need the repo scope to use this endpoint.
Fine-grained access tokens require the "Metadata" repository permission (read).

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

- **200** - OK

- **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/issue-types
```

**Response schema (Status: 200):**

Array of `Issue Type`:
  * `id`: required, integer
  * `node_id`: required, string
  * `name`: required, string
  * `description`: required, string or null
  * `color`: string or null, enum: `gray`, `blue`, `green`, `yellow`, `orange`, `red`, `pink`, `purple`, `null`
  * `created_at`: string, format: date-time
  * `updated_at`: string, format: date-time
  * `is_enabled`: boolean