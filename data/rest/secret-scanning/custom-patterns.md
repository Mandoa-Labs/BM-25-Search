# REST API endpoints for secret scanning custom patterns

Use the REST API to manage custom patterns for secret scanning.

> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## List organization custom patterns

```
GET /orgs/{org}/secret-scanning/custom-patterns
```

Lists secret scanning custom patterns for an organization.
Personal access tokens (classic) need the read:org scope to use this endpoint.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`state`** (string)
  Filter custom patterns by state. When absent, returns patterns in all states.
  Can be one of: `published`, `unpublished`

- **`push_protection`** (string)
  Filter custom patterns by whether push protection is enabled. When absent, returns patterns regardless of push protection status.
  Can be one of: `enabled`, `disabled`

- **`sort`** (string)
  The property to sort the results by.
  Default: `created`
  Can be one of: `created`, `updated`, `name`

- **`direction`** (string)
  The direction to sort the results by.
  Default: `desc`
  Can be one of: `asc`, `desc`

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

### HTTP response status codes

- **200** - OK

- **403** - Forbidden

- **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/secret-scanning/custom-patterns
```

**Response schema (Status: 200):**

Array of `Secret Scanning Custom Pattern`:
  * `id`: required, integer
  * `name`: required, string
  * `pattern`: required, string
  * `slug`: required, string
  * `state`: required, string, enum: `published`, `unpublished`
  * `push_protection_enabled`: required, boolean
  * `start_delimiter`: string or null
  * `end_delimiter`: string or null
  * `must_match`: array of string or null
  * `must_not_match`: array of string or null
  * `custom_pattern_version`: string or null
  * `created_at`: string, format: date-time
  * `updated_at`: string, format: date-time

## Bulk create organization custom patterns

```
POST /orgs/{org}/secret-scanning/custom-patterns
```

Bulk creates secret scanning custom patterns for an organization.
Personal access tokens (classic) need the write:org scope to use this endpoint.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

#### Body parameters

- **`patterns`** (array of objects) (required)
  The list of custom patterns to create.
  - **`name`** (string) (required)
    The name of the custom pattern.
  - **`pattern`** (string) (required)
    The regular expression of the custom pattern.
  - **`start_delimiter`** (string)
    The start delimiter regex for the custom pattern.
Defaults to \A|[^0-9A-Za-z] when not specified.
    Default: `\A|[^0-9A-Za-z]`
  - **`end_delimiter`** (string)
    The end delimiter regex for the custom pattern.
Defaults to \z|[^0-9A-Za-z] when not specified.
    Default: `\z|[^0-9A-Za-z]`
  - **`must_match`** (array of strings)
    List of regexes that the secret must match.
  - **`must_not_match`** (array of strings)
    List of regexes that the secret must not match.

### HTTP response status codes

- **201** - All patterns created successfully.

- **400** - Bad Request

- **403** - Forbidden

- **404** - Resource not found

- **422** - Validation failed for one or more patterns.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/orgs/ORG/secret-scanning/custom-patterns \
  -d '{
  "patterns": [
    {
      "name": "Example Custom Pattern",
      "pattern": "[a-z]+_token_[0-9]+"
    },
    {
      "name": "Another Custom Pattern",
      "pattern": "prefix_[a-zA-Z0-9]{32}",
      "start_delimiter": "\\b",
      "end_delimiter": "\\b",
      "must_match": [
        "^prefix_prod"
      ],
      "must_not_match": [
        "test"
      ]
    }
  ]
}'
```

**Response schema (Status: 201):**

* `created_patterns`: array of `Secret Scanning Custom Pattern`:
  * `id`: required, integer
  * `name`: required, string
  * `pattern`: required, string
  * `slug`: required, string
  * `state`: required, string, enum: `published`, `unpublished`
  * `push_protection_enabled`: required, boolean
  * `start_delimiter`: string or null
  * `end_delimiter`: string or null
  * `must_match`: array of string or null
  * `must_not_match`: array of string or null
  * `custom_pattern_version`: string or null
  * `created_at`: string, format: date-time
  * `updated_at`: string, format: date-time

## Bulk delete organization custom patterns

```
DELETE /orgs/{org}/secret-scanning/custom-patterns
```

Bulk deletes secret scanning custom patterns for an organization.
Personal access tokens (classic) need the write:org scope to use this endpoint.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

#### Body parameters

- **`patterns`** (array of objects) (required)
  The list of custom patterns to delete.
  - **`pattern_id`** (integer) (required)
    The ID of the custom pattern to delete.
  - **`custom_pattern_version`** (string or null)
    The version of the entity. This is used to confirm you're updating the current version of the entity and mitigate unintentionally overriding someone else's update.

- **`post_delete_action`** (string)
  What to do with alerts associated with the deleted patterns.
delete_alerts permanently removes the alerts.
resolve_alerts resolves the alerts as "pattern deleted".
Defaults to delete_alerts when not specified.
  Default: `delete_alerts`
  Can be one of: `delete_alerts`, `resolve_alerts`

### HTTP response status codes

- **204** - All patterns deleted successfully.

- **400** - Bad Request

- **403** - Forbidden

- **404** - Resource not found

- **412** - Precondition Failed

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/orgs/ORG/secret-scanning/custom-patterns \
  -d '{
  "patterns": [
    {
      "pattern_id": 2,
      "custom_pattern_version": "0ujsswThIGTUYm2K8FjOOfXtY1K"
    }
  ]
}'
```

**Response schema (Status: 204):**

## Update an organization custom pattern

```
PATCH /orgs/{org}/secret-scanning/custom-patterns/{pattern_id}
```

Updates a secret scanning custom pattern for an organization.
Personal access tokens (classic) need the write:org scope to use this endpoint.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`pattern_id`** (integer) (required)
  The ID of the custom pattern.

#### Body parameters

- **`pattern`** (string)
  The updated regular expression of the custom pattern.

- **`start_delimiter`** (string)
  The updated start delimiter regex for the custom pattern.

- **`end_delimiter`** (string)
  The updated end delimiter regex for the custom pattern.

- **`must_match`** (array of strings)
  Updated list of regexes that the secret must match.

- **`must_not_match`** (array of strings)
  Updated list of regexes that the secret must not match.

- **`custom_pattern_version`** (string or null) (required)
  The version of the entity. This is used to confirm you're updating the current version of the entity and mitigate unintentionally overriding someone else's update.

### HTTP response status codes

- **200** - Pattern updated successfully.

- **400** - Bad Request

- **403** - Forbidden

- **404** - Resource not found

- **412** - Precondition Failed

- **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/orgs/ORG/secret-scanning/custom-patterns/PATTERN_ID \
  -d '{
  "pattern": "updated_secret_[0-9A-Z]{16}",
  "start_delimiter": "[^0-9A-Za-z]",
  "end_delimiter": "[^0-9A-Za-z]",
  "must_match": [
    "updated_secret_[0-9]{2}*"
  ],
  "must_not_match": [
    "updated_secret_1234567890ABCDEF"
  ],
  "custom_pattern_version": "0ujsswThIGTUYm2K8FjOOfXtY1K"
}'
```

**Response schema (Status: 200):**

* `id`: required, integer
* `name`: required, string
* `pattern`: required, string
* `slug`: required, string
* `state`: required, string, enum: `published`, `unpublished`
* `push_protection_enabled`: required, boolean
* `start_delimiter`: string or null
* `end_delimiter`: string or null
* `must_match`: array of string or null
* `must_not_match`: array of string or null
* `custom_pattern_version`: string or null
* `created_at`: string, format: date-time
* `updated_at`: string, format: date-time

## List repository custom patterns

```
GET /repos/{owner}/{repo}/secret-scanning/custom-patterns
```

Lists secret scanning custom patterns for a repository.
OAuth app tokens and personal access tokens (classic) need the repo or security_events scope to use this endpoint. If this endpoint is only used with public repositories, the token can use the public_repo scope instead.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

- **`state`** (string)
  Filter custom patterns by state. When absent, returns patterns in all states.
  Can be one of: `published`, `unpublished`

- **`push_protection`** (string)
  Filter custom patterns by whether push protection is enabled. When absent, returns patterns regardless of push protection status.
  Can be one of: `enabled`, `disabled`

- **`sort`** (string)
  The property to sort the results by.
  Default: `created`
  Can be one of: `created`, `updated`, `name`

- **`direction`** (string)
  The direction to sort the results by.
  Default: `desc`
  Can be one of: `asc`, `desc`

- **`page`** (integer)
  The page number of the results to fetch. For more information, see "Using pagination in the REST API."
  Default: `1`

- **`per_page`** (integer)
  The number of results per page (max 100). For more information, see "Using pagination in the REST API."
  Default: `30`

### HTTP response status codes

- **200** - OK

- **403** - Forbidden

- **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/secret-scanning/custom-patterns
```

**Response schema (Status: 200):**

Same response schema as [List organization custom patterns](#list-organization-custom-patterns).

## Bulk create repository custom patterns

```
POST /repos/{owner}/{repo}/secret-scanning/custom-patterns
```

Bulk creates secret scanning custom patterns for a repository.
OAuth app tokens and personal access tokens (classic) need the repo or security_events scope to use this endpoint. If this endpoint is only used with public repositories, the token can use the public_repo scope instead.

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

- **`patterns`** (array of objects) (required)
  The list of custom patterns to create.
  - **`name`** (string) (required)
    The name of the custom pattern.
  - **`pattern`** (string) (required)
    The regular expression of the custom pattern.
  - **`start_delimiter`** (string)
    The start delimiter regex for the custom pattern.
Defaults to \A|[^0-9A-Za-z] when not specified.
    Default: `\A|[^0-9A-Za-z]`
  - **`end_delimiter`** (string)
    The end delimiter regex for the custom pattern.
Defaults to \z|[^0-9A-Za-z] when not specified.
    Default: `\z|[^0-9A-Za-z]`
  - **`must_match`** (array of strings)
    List of regexes that the secret must match.
  - **`must_not_match`** (array of strings)
    List of regexes that the secret must not match.

### HTTP response status codes

- **201** - All patterns created successfully.

- **400** - Bad Request

- **403** - Forbidden

- **404** - Resource not found

- **422** - Validation failed for one or more patterns.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/secret-scanning/custom-patterns \
  -d '{
  "patterns": [
    {
      "name": "Example Custom Pattern",
      "pattern": "[a-z]+_token_[0-9]+"
    },
    {
      "name": "Another Custom Pattern",
      "pattern": "prefix_[a-zA-Z0-9]{32}",
      "start_delimiter": "\\b",
      "end_delimiter": "\\b",
      "must_match": [
        "^prefix_prod"
      ],
      "must_not_match": [
        "test"
      ]
    }
  ]
}'
```

**Response schema (Status: 201):**

Same response schema as [Bulk create organization custom patterns](#bulk-create-organization-custom-patterns).

## Bulk delete repository custom patterns

```
DELETE /repos/{owner}/{repo}/secret-scanning/custom-patterns
```

Bulk deletes secret scanning custom patterns for a repository.
OAuth app tokens and personal access tokens (classic) need the repo or security_events scope to use this endpoint. If this endpoint is only used with public repositories, the token can use the public_repo scope instead.

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

- **`patterns`** (array of objects) (required)
  The list of custom patterns to delete.
  - **`pattern_id`** (integer) (required)
    The ID of the custom pattern to delete.
  - **`custom_pattern_version`** (string or null)
    The version of the entity. This is used to confirm you're updating the current version of the entity and mitigate unintentionally overriding someone else's update.

- **`post_delete_action`** (string)
  What to do with alerts associated with the deleted patterns.
delete_alerts permanently removes the alerts.
resolve_alerts resolves the alerts as "pattern deleted".
Defaults to delete_alerts when not specified.
  Default: `delete_alerts`
  Can be one of: `delete_alerts`, `resolve_alerts`

### HTTP response status codes

- **204** - All patterns deleted successfully.

- **400** - Bad Request

- **403** - Forbidden

- **404** - Resource not found

- **412** - Precondition Failed

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/repos/OWNER/REPO/secret-scanning/custom-patterns \
  -d '{
  "patterns": [
    {
      "pattern_id": 2,
      "custom_pattern_version": "0ujsswThIGTUYm2K8FjOOfXtY1K"
    }
  ]
}'
```

**Response schema (Status: 204):**

## Update a repository custom pattern

```
PATCH /repos/{owner}/{repo}/secret-scanning/custom-patterns/{pattern_id}
```

Updates a secret scanning custom pattern for a repository.
OAuth app tokens and personal access tokens (classic) need the repo or security_events scope to use this endpoint. If this endpoint is only used with public repositories, the token can use the public_repo scope instead.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`owner`** (string) (required)
  The account owner of the repository. The name is not case sensitive.

- **`repo`** (string) (required)
  The name of the repository without the .git extension. The name is not case sensitive.

- **`pattern_id`** (integer) (required)
  The ID of the custom pattern.

#### Body parameters

- **`pattern`** (string)
  The updated regular expression of the custom pattern.

- **`start_delimiter`** (string)
  The updated start delimiter regex for the custom pattern.

- **`end_delimiter`** (string)
  The updated end delimiter regex for the custom pattern.

- **`must_match`** (array of strings)
  Updated list of regexes that the secret must match.

- **`must_not_match`** (array of strings)
  Updated list of regexes that the secret must not match.

- **`custom_pattern_version`** (string or null) (required)
  The version of the entity. This is used to confirm you're updating the current version of the entity and mitigate unintentionally overriding someone else's update.

### HTTP response status codes

- **200** - Pattern updated successfully.

- **400** - Bad Request

- **403** - Forbidden

- **404** - Resource not found

- **412** - Precondition Failed

- **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/repos/OWNER/REPO/secret-scanning/custom-patterns/PATTERN_ID \
  -d '{
  "pattern": "updated_secret_[0-9A-Z]{16}",
  "start_delimiter": "[^0-9A-Za-z]",
  "end_delimiter": "[^0-9A-Za-z]",
  "must_match": [
    "updated_secret_[0-9]{2}*"
  ],
  "must_not_match": [
    "updated_secret_1234567890ABCDEF"
  ],
  "custom_pattern_version": "0ujsswThIGTUYm2K8FjOOfXtY1K"
}'
```

**Response schema (Status: 200):**

Same response schema as [Update an organization custom pattern](#update-an-organization-custom-pattern).