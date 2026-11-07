# REST API endpoints for Dependabot runner settings

Use the REST API to get and set Dependabot runner settings.

> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## Get repository Dependabot runner settings

```
GET /repos/{owner}/{repo}/dependabot/runner-settings
```

Gets the runner Dependabot uses for this repository: standard GitHub-hosted
runners, or labeled runners with their labels and optional runner group. The
response matches the repository's code security settings page.
Labeled runners take effect only for private and internal repositories with
GitHub Actions enabled. Otherwise, the response shows standard.
Repository administrators and users who can manage security products for the
repository can use this endpoint. OAuth app tokens and personal access tokens
(classic) require the repo scope for both public and private repositories.
GitHub App tokens and fine-grained personal access tokens require repository
Administration read permission. Workflow GITHUB_TOKEN access is not supported.

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

- **401** - Requires authentication

- **403** - Forbidden

- **404** - Resource not found

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/repos/OWNER/REPO/dependabot/runner-settings
```

**Response schema (Status: 200):**

* `runner_type`: required, string, enum: `standard`, `labeled`
* `runner_labels`: required, array of string
* `runner_group`: required, string or null

## Set repository Dependabot runner settings

```
PUT /repos/{owner}/{repo}/dependabot/runner-settings
```

Sets the runner Dependabot uses for this repository. This is the same setting
as on the repository's code security settings page.
labeled turns on labeled runners with exactly one runner label and an optional
runner group. standard turns them off and clears the label and group.
Labeled runners are only available for private and internal repositories with
GitHub Actions enabled. The response returns the settings after the change.
Repository administrators and users who can manage security products for the
repository can use this endpoint, subject to enterprise policy. OAuth app tokens
and personal access tokens (classic) require the repo scope. GitHub App tokens
and fine-grained personal access tokens require repository Administration write
permission. Workflow GITHUB_TOKEN access is not supported.

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

- **`runner_type`** (string) (required)
  labeled for labeled runners, standard for standard GitHub-hosted runners.
  Can be one of: `standard`, `labeled`

- **`runner_labels`** (array of strings)
  Required for labeled. Exactly one non-blank runner label. Not allowed for standard.

- **`runner_group`** (string or null)
  Optional for labeled. Omitted, null or blank means no group. Not allowed for standard.

### HTTP response status codes

- **200** - OK

- **400** - Bad Request

- **401** - Requires authentication

- **403** - Forbidden

- **404** - Resource not found

- **422** - Validation failed, or the endpoint has been spammed.

### Code examples

#### Select labeled runners in a runner group

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/repos/OWNER/REPO/dependabot/runner-settings \
  -d '{
  "runner_type": "labeled",
  "runner_labels": [
    "dependabot"
  ],
  "runner_group": "dependabot-runners"
}'
```

**Response schema (Status: 200):**

Same response schema as [Get repository Dependabot runner settings](#get-repository-dependabot-runner-settings).