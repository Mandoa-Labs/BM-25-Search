# REST API endpoints for license compliance

Use the REST API to check packages against a repository's license compliance policy.

> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## Check license compliance for packages

```
POST /repos/{owner}/{repo}/license-compliance/package-checks
```

Checks whether packages identified by the supplied package URLs (PURLs) are allowed by the repository's license compliance policy.
For requests made on behalf of a user, that user must have write access to the repository or the "View repository license policy" permission.
OAuth apps and classic personal access tokens require the repo scope.

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

- **`purls`** (array of strings) (required)
  Package URLs to check against the license compliance policy. Duplicate package URLs are checked once.

### HTTP response status codes

- **200** - Package license compliance results.

- **403** - Forbidden

- **404** - License compliance policy not found.

- **422** - Validation failed, or the endpoint has been spammed.

- **503** - Service unavailable

### Code examples

#### Example 1: Status Code 200

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/license-compliance/package-checks \
  -d '{
  "purls": [
    "pkg:npm/lodash@4.17.21"
  ]
}'
```

**Response schema (Status: 200):**

* `purls`: required, object, additional properties: object

#### Example 2: Status Code 200

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/repos/OWNER/REPO/license-compliance/package-checks \
  -d '{
  "purls": []
}'
```

**Response schema (Status: 200):**

* `purls`: required, object, additional properties: object