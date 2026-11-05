# REST API endpoints for Copilot team customizations

Use the REST API to manage Copilot customizations for a team.

> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.

## Get Copilot customizations for a team

```
GET /orgs/{org}/teams/{team_slug}/copilot/customizations
```

Note

This endpoint is in public preview and is subject to change.

Gets the GitHub-managed Copilot customizations of a team.
The authenticated user must be an organization owner or a team maintainer. Teams that keep their
customizations in a repository return 409.
OAuth app tokens and personal access tokens (classic) need the admin:org or read:org scope to use this endpoint.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`team_slug`** (string) (required)
  The slug of the team name.

### HTTP response status codes

- **200** - OK

- **401** - Requires authentication

- **403** - Forbidden

- **404** - Resource not found

- **409** - Conflict

- **422** - Validation failed, or the endpoint has been spammed.

- **500** - Internal Error

- **503** - Service unavailable

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X GET \
  https://api.github.com/orgs/ORG/teams/TEAM_SLUG/copilot/customizations
```

**Response schema (Status: 200):**

* `pluginAssignments`: object, additional properties: object
* `extraKnownMarketplaces`: object, additional properties: object

## Set Copilot customizations for a team

```
PUT /orgs/{org}/teams/{team_slug}/copilot/customizations
```

Note

This endpoint is in public preview and is subject to change.

Replaces the GitHub-managed Copilot customizations of a team, creating them on the first write.
The authenticated user must be an organization owner or a team maintainer. Teams that keep their
customizations in a repository return 409. Documents that fail validation return 422 with the reason.
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`team_slug`** (string) (required)
  The slug of the team name.

#### Body parameters

- **`pluginAssignments`** (object)
  Plugins assigned to the team, keyed by PLUGIN@MARKETPLACE.
  - **`key`** (object)
    A user-defined key to represent an item in pluginAssignments.
    - **`state`** (string)
      The assignment state.
      Can be one of: `defaultEnabled`

- **`extraKnownMarketplaces`** (object)
  Additional plugin marketplaces available to the team, keyed by marketplace name.
  - **`key`** (object)
    A user-defined key to represent an item in extraKnownMarketplaces.

### HTTP response status codes

- **200** - OK

- **401** - Requires authentication

- **403** - Forbidden

- **404** - Resource not found

- **409** - Conflict

- **422** - Validation failed, or the endpoint has been spammed.

- **500** - Internal Error

- **503** - Service unavailable

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X PUT \
  https://api.github.com/orgs/ORG/teams/TEAM_SLUG/copilot/customizations \
  -d '{
  "pluginAssignments": {
    "code-review@acme-marketplace": {
      "state": "defaultEnabled"
    }
  },
  "extraKnownMarketplaces": {
    "acme-marketplace": {
      "source": {
        "source": "github",
        "repo": "acme/copilot-marketplace"
      }
    }
  }
}'
```

**Response schema (Status: 200):**

Same response schema as [Get Copilot customizations for a team](#get-copilot-customizations-for-a-team).

## Delete Copilot customizations for a team

```
DELETE /orgs/{org}/teams/{team_slug}/copilot/customizations
```

Note

This endpoint is in public preview and is subject to change.

Deletes the GitHub-managed Copilot customizations of a team. Deleting customizations that don't exist succeeds.
The authenticated user must be an organization owner or a team maintainer. Teams that keep their
customizations in a repository return 409.
OAuth app tokens and personal access tokens (classic) need the admin:org scope to use this endpoint.

### Parameters

#### Headers

- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.

#### Path and query parameters

- **`org`** (string) (required)
  The organization name. The name is not case sensitive.

- **`team_slug`** (string) (required)
  The slug of the team name.

### HTTP response status codes

- **204** - No Content

- **401** - Requires authentication

- **403** - Forbidden

- **404** - Resource not found

- **409** - Conflict

- **422** - Validation failed, or the endpoint has been spammed.

- **500** - Internal Error

- **503** - Service unavailable

### Code examples

#### Example

**Request:**

```curl
curl -L \
  -X DELETE \
  https://api.github.com/orgs/ORG/teams/TEAM_SLUG/copilot/customizations
```

**Response schema (Status: 204):**