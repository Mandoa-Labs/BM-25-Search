# REST API endpoints for issue types

Use the REST API to create and manage issue types for the authenticated user.

> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## List issue types

```
GET /user/issue-types
```

Lists all issue types for the authenticated user. OAuth app tokens and personal access tokens (classic) need the read:user scope to use this endpoint.

### HTTP response status codes

- **200** - OK

- **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/user/issue-types
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

## Create an issue type

```
POST /user/issue-types
```

Creates a new issue type for the authenticated user's personal account.
OAuth app tokens and personal access tokens (classic) need the user scope to use this endpoint.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Body parameters

- **`name`** (string) (required)
  Name of the issue type.

- **`is_enabled`** (boolean) (required)
  Whether or not the issue type is enabled.

- **`description`** (string or null)
  Description of the issue type.

- **`color`** (string or null)
  Color for the issue type.
  Can be one of: `gray`, `blue`, `green`, `yellow`, `orange`, `red`, `pink`, `purple`, `null`

### HTTP response status codes

- **200** - OK

- **404** - Resource not found

- **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/user/issue-types \
  -d '{
  "name": "Epic",
  "description": "An issue type for a multi-week tracking of work",
  "is_enabled": true,
  "color": "green"
}'
```

**Response schema (Status: 200):**

* `id`: required, integer
* `node_id`: required, string
* `name`: required, string
* `description`: required, string or null
* `color`: string or null, enum: `gray`, `blue`, `green`, `yellow`, `orange`, `red`, `pink`, `purple`, `null`
* `created_at`: string, format: date-time
* `updated_at`: string, format: date-time
* `is_enabled`: boolean

## Update an issue type

```
PUT /user/issue-types/{issue_type_id}
```

Updates an issue type for the authenticated user.
The authenticated user must own the issue type. OAuth app tokens and personal access tokens (classic)
need the user scope to use this endpoint.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`issue_type_id`** (integer) (required)
  The unique identifier of the issue type.

#### Body parameters

- **`name`** (string) (required)
  Name of the issue type.

- **`is_enabled`** (boolean) (required)
  Whether or not the issue type is enabled.

- **`description`** (string or null)
  Description of the issue type.

- **`color`** (string or null)
  Color for the issue type.
  Can be one of: `gray`, `blue`, `green`, `yellow`, `orange`, `red`, `pink`, `purple`, `null`

### HTTP response status codes

- **200** - OK

- **404** - Resource not found

- **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/user/issue-types/ISSUE_TYPE_ID \
  -d '{
  "name": "Epic",
  "description": "An issue type for a multi-week tracking of work",
  "is_enabled": true,
  "color": "green"
}'
```

**Response schema (Status: 200):**

Same response schema as [Create an issue type](#create-an-issue-type).

## Delete an issue type

```
DELETE /user/issue-types/{issue_type_id}
```

Deletes an issue type for the authenticated user.
The authenticated user must own the issue type. OAuth app tokens and personal access tokens (classic)
need the user scope to use this endpoint.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`issue_type_id`** (integer) (required)
  The unique identifier of the issue type.

### HTTP response status codes

- **204** - No Content

- **404** - Resource not found

- **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/user/issue-types/ISSUE_TYPE_ID
```

**Response schema (Status: 204):**