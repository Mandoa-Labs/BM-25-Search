# REST API endpoints for security advisories

Use the REST API to create and manage innersource security alerts

> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## Sync innersource vulnerabilities for an enterprise

```
POST /enterprises/{enterprise}/innersource-vulnerabilities/sync
```

Synchronize innersource vulnerability data with the Advisory Database for an enterprise.
This endpoint receives vulnerability data in OSV format and creates, updates, or withdraws
innersource vulnerabilities accordingly. Dependabot alerting is triggered for created and
updated vulnerabilities.
The request body accepts up to 100 vulnerabilities per call. The request is validated and
then queued for asynchronous processing: a successful request returns 202 Accepted with a
Location header pointing to a status URL that you poll for the final result.
Syncing vulnerabilities too quickly using this endpoint may result in secondary rate limiting. For more information, see "Rate limits for the API" and "Best practices for using the REST API."
This endpoint does not support OAuth apps or personal access tokens.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

#### Body parameters

- **``** (array)
  Array of vulnerabilities in OSV format to synchronize
  - **`id`** (string) (required)
    Unique identifier for the vulnerability from the external system
  - **`schema_version`** (string)
    The OSV schema version
  - **`summary`** (string)
    A short summary of the vulnerability
  - **`details`** (string)
    Detailed description of the vulnerability
  - **`aliases`** (array of strings)
    IDs for the same vulnerability in other databases. Only CVE IDs are used (to populate the vulnerability's CVE identifier); other aliases are ignored.
  - **`severity`** (array of objects)
    Severity information for the vulnerability
    - **`type`** (string)
      The type of severity scoring (e.g., CVSS_V3)
    - **`score`** (string)
      The severity score or vector string
  - **`affected`** (array of objects)
    Packages and versions affected by the vulnerability
    - **`package`** (object)
      - **`ecosystem`** (string)
        The package ecosystem (e.g., npm, pip, maven)
      - **`name`** (string)
        The package name
    - **`ranges`** (array of objects)
      - **`type`** (string)
      - **`events`** (array of objects)
        - **`introduced`** (string)
          The version that introduced the vulnerability
        - **`fixed`** (string)
          The version that fixed the vulnerability
        - **`last_affected`** (string)
          The last affected version
        - **`limit`** (string)
          The upper limit of the affected range
  - **`references`** (array of objects)
    URLs for more information about the vulnerability
    - **`type`** (string)
      The type of reference. Supported values: PACKAGE, ADVISORY, WEB, FIX, ARTICLE, REPORT, EVIDENCE. References with other types are ignored.
    - **`url`** (string)
      The reference URL
  - **`published`** (string)
    When the vulnerability was first published
  - **`modified`** (string)
    When the vulnerability was last modified
  - **`withdrawn`** (string)
    When the vulnerability was withdrawn. If present, the vulnerability will be marked as withdrawn.

### HTTP response status codes

- **202** - Sync operation accepted for asynchronous processing. Poll the returned URL for results.

- **400** - Bad Request

- **401** - Requires authentication

- **403** - Forbidden

- **404** - Resource not found

- **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/enterprises/ENTERPRISE/innersource-vulnerabilities/sync \
  -d '[
  {
    "id": "MVS-2026-001",
    "schema_version": "1.4.0",
    "summary": "Example vulnerability summary",
    "aliases": [
      "GHSA-xxxx-xxxx-xxxx"
    ],
    "affected": [
      {
        "package": {
          "ecosystem": "npm",
          "name": "example-package"
        },
        "ranges": [
          {
            "type": "SEMVER",
            "events": [
              {
                "introduced": "1.0.0"
              },
              {
                "fixed": "1.0.1"
              }
            ]
          }
        ]
      }
    ]
  }
]'
```

**Response schema (Status: 202):**

* `id`: required, string
* `url`: required, string, format: uri
* `status`: required, string, enum: `queued`

## Get innersource vulnerability sync status for an enterprise

```
GET /enterprises/{enterprise}/innersource-vulnerabilities/sync/status/{job_id}
```

Get the status of an asynchronous innersource vulnerability sync operation for an enterprise.
Returns 202 with a Retry-After header while the sync is still processing, or 200 with
the full sync results once complete.
This endpoint does not support OAuth apps or personal access tokens.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.

- **`job_id`** (string) (required)
  The unique identifier of the sync job.

### HTTP response status codes

- **200** - Sync operation completed

- **202** - Sync operation is still processing

- **401** - Requires authentication

- **403** - Forbidden

- **404** - Resource not found

### Code examples

#### Example 1: Status Code 200

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/innersource-vulnerabilities/sync/status/JOB_ID
```

**Response schema (Status: 200):**

* one of:
  * **External Vulnerability Sync Result**
    * `processed`: required, integer
    * `created`: required, integer
    * `updated`: required, integer
    * `withdrawn`: required, integer
    * `errors`: required, integer
    * `results`: required, array of objects:
      * `external_id`: required, string
      * `status`: required, string, enum: `created`, `updated`, `withdrawn`, `error`
      * `ghsa_id`: string
      * `error`: string
  * **object**
    * `status`: string, enum: `error`
    * `error`: string

#### Example 2: Status Code 200

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/innersource-vulnerabilities/sync/status/JOB_ID
```

**Response schema (Status: 200):**

* one of:
  * **External Vulnerability Sync Result**
    * `processed`: required, integer
    * `created`: required, integer
    * `updated`: required, integer
    * `withdrawn`: required, integer
    * `errors`: required, integer
    * `results`: required, array of objects:
      * `external_id`: required, string
      * `status`: required, string, enum: `created`, `updated`, `withdrawn`, `error`
      * `ghsa_id`: string
      * `error`: string
  * **object**
    * `status`: string, enum: `error`
    * `error`: string

#### Example 3: Status Code 202

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/enterprises/ENTERPRISE/innersource-vulnerabilities/sync/status/JOB_ID
```

**Response schema (Status: 202):**

* `id`: required, string
* `status`: required, string, enum: `processing`