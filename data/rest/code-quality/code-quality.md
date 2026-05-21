# REST API endpoints for code quality

Use the REST API to manage a code quality configuration.


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## Get a code quality setup configuration

```
GET /repos/{owner}/{repo}/code-quality/setup
```

Gets a code quality setup configuration.
OAuth app tokens and personal access tokens (classic) need the repo scope to use this endpoint with private or public repositories, or the public_repo scope to use this endpoint with only public repositories.


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


- **403** - Response if the user is not authorized to access Code quality for this repository.


- **404** - Resource not found


- **503** - Service unavailable




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/code-quality/setup
```

**Response schema (Status: 200):**

* `state`: string, enum: `configured`, `not-configured`
* `languages`: array of string, enum: `csharp`, `go`, `java-kotlin`, `javascript-typescript`, `python`, `ruby`, `rust`
* `runner_type`: string or null, enum: `standard`, `labeled`, `null`
* `runner_label`: string or null
* `updated_at`: string or null, format: date-time
* `schedule`: string or null, enum: `weekly`, `null`





## Update a code quality setup configuration

```
PATCH /repos/{owner}/{repo}/code-quality/setup
```

Updates a code quality setup configuration.
OAuth app tokens and personal access tokens (classic) need the repo scope to use this endpoint with private or public repositories, or the public_repo scope to use this endpoint with only public repositories.


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

- **`state`** (string)
  The desired state of code quality setup.
  Can be one of: `configured`, `not-configured`

- **`runner_type`** (string)
  Runner type to be used.
  Can be one of: `standard`, `labeled`

- **`runner_label`** (string or null)
  Runner label to be used if the runner type is labeled.

- **`languages`** (array of strings)
  Languages to be analyzed.
Supported values are: csharp, go, java-kotlin, javascript-typescript, python, ruby





### HTTP response status codes


- **200** - OK


- **202** - Accepted


- **403** - Response if the repository is archived or if Code quality is not enabled for this repository


- **404** - Resource not found


- **409** - Response if there is already a code quality setup configuration update in progress


- **422** - Response if the configuration change cannot be made


- **503** - Service unavailable




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X PATCH \
  https://api.github.com/repos/OWNER/REPO/code-quality/setup \
  -d '{
  "state": "configured",
  "languages": [
    "javascript-typescript",
    "python",
    "ruby"
  ]
}'
```

**Response schema (Status: 202):**

* `run_id`: integer
* `run_url`: string