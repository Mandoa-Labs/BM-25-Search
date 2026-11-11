# REST API endpoints for issue fields

Use the REST API to create and manage issue fields for the authenticated user.

> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## List issue fields

```
GET /user/issue-fields
```

Lists all issue fields for the authenticated user. OAuth app tokens and personal access tokens (classic) need the read:user scope to use this endpoint.

### HTTP response status codes

- **200** - OK

- **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/user/issue-fields
```

**Response schema (Status: 200):**

Array of `User Issue Field`:
  * `id`: required, integer
  * `node_id`: required, string
  * `name`: required, string
  * `description`: string or null
  * `data_type`: required, string, enum: `text`, `date`, `single_select`, `multi_select`, `number`
  * `visibility`: string, enum: `restricted`, `all`
  * `options`: array of objects or null:
    * `id`: required, integer
    * `name`: required, string
    * `description`: string or null
    * `color`: string or null, enum: `gray`, `blue`, `green`, `yellow`, `orange`, `red`, `pink`, `purple`, `null`
    * `priority`: integer or null
    * `created_at`: string, format: date-time
    * `updated_at`: string, format: date-time
  * `created_at`: string, format: date-time
  * `updated_at`: string, format: date-time

## Create an issue field

```
POST /user/issue-fields
```

Creates a new issue field for the authenticated user's personal account.
OAuth app tokens and personal access tokens (classic) need the user scope to use this endpoint.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Body parameters

- **`name`** (string) (required)
  Name of the issue field.

- **`description`** (string or null)
  Description of the issue field.

- **`data_type`** (string) (required)
  The data type of the issue field.
  Can be one of: `text`, `date`, `single_select`, `multi_select`, `number`

- **`visibility`** (string)
  The visibility of the issue field. Can be restricted (visible only to the owner and to collaborators on the repository the field is read through) or all (visible to all users who can see issues). Defaults to restricted.
  Can be one of: `restricted`, `all`

- **`options`** (array of objects or null)
  Options for select fields. Required when data_type is 'single_select' or 'multi_select'.
  - **`name`** (string) (required)
    Name of the option.
  - **`description`** (string or null)
    Description of the option.
  - **`color`** (string) (required)
    Color for the option.
    Can be one of: `gray`, `blue`, `green`, `yellow`, `orange`, `red`, `pink`, `purple`
  - **`priority`** (integer) (required)
    Priority of the option for ordering.

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
  https://api.github.com/user/issue-fields \
  -d '{
  "name": "Priority",
  "description": "Level of importance for the issue",
  "data_type": "single_select",
  "visibility": "restricted",
  "options": [
    {
      "name": "High",
      "description": "High priority",
      "color": "red",
      "priority": 1
    },
    {
      "name": "Medium",
      "description": "Medium priority",
      "color": "yellow",
      "priority": 2
    },
    {
      "name": "Low",
      "description": "Low priority",
      "color": "green",
      "priority": 3
    }
  ]
}'
```

**Response schema (Status: 200):**

* `id`: required, integer
* `node_id`: required, string
* `name`: required, string
* `description`: string or null
* `data_type`: required, string, enum: `text`, `date`, `single_select`, `multi_select`, `number`
* `visibility`: string, enum: `restricted`, `all`
* `options`: array of objects or null:
  * `id`: required, integer
  * `name`: required, string
  * `description`: string or null
  * `color`: string or null, enum: `gray`, `blue`, `green`, `yellow`, `orange`, `red`, `pink`, `purple`, `null`
  * `priority`: integer or null
  * `created_at`: string, format: date-time
  * `updated_at`: string, format: date-time
* `created_at`: string, format: date-time
* `updated_at`: string, format: date-time

## Update an issue field

```
PATCH /user/issue-fields/{issue_field_id}
```

Updates an issue field for the authenticated user.
The authenticated user must own the issue field. OAuth app tokens and personal access tokens (classic)
need the user scope to use this endpoint.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`issue_field_id`** (integer) (required)
  The unique identifier of the issue field.

#### Body parameters

- **`name`** (string)
  Name of the issue field.

- **`description`** (string or null)
  Description of the issue field.

- **`visibility`** (string)
  The visibility of the issue field. Can be restricted (visible only to the owner and to collaborators on the repository the field is read through) or all (visible to all users who can see issues).
  Can be one of: `restricted`, `all`

- **`options`** (array of objects)
  Options for select fields. Only applicable when updating single_select or multi_select fields. When provided, this array replaces the entire existing set of options rather than adding to or updating individual options. To retain or update an existing option, include it in the array with its id. Options sent without an id are treated as new options and may cause existing options to be deleted and recreated.
  - **`id`** (integer)
    The id of an existing option to retain or update. Omit this when creating a new option.
  - **`name`** (string) (required)
    Name of the option.
  - **`description`** (string or null)
    Description of the option.
  - **`color`** (string) (required)
    Color for the option.
    Can be one of: `gray`, `blue`, `green`, `yellow`, `orange`, `red`, `pink`, `purple`
  - **`priority`** (integer) (required)
    Priority of the option for ordering.

### HTTP response status codes

- **200** - OK

- **404** - Resource not found

- **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Update name and description

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/user/issue-fields/ISSUE_FIELD_ID \
  -d '{
  "name": "Priority",
  "description": "Level of importance for the issue"
}'
```

**Response schema (Status: 200):**

Same response schema as [Create an issue field](#create-an-issue-field).

## Delete an issue field

```
DELETE /user/issue-fields/{issue_field_id}
```

Deletes an issue field for the authenticated user.
The authenticated user must own the issue field. OAuth app tokens and personal access tokens (classic)
need the user scope to use this endpoint.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`issue_field_id`** (integer) (required)
  The unique identifier of the issue field.

### HTTP response status codes

- **204** - A header with no content is returned.

- **404** - Resource not found

- **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/user/issue-fields/ISSUE_FIELD_ID
```

**Response schema (Status: 204):**