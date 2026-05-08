# REST API endpoints for enterprise credential authorizations

Use the REST API to manage enterprise credential authorizations.


> [!NOTE]
> Most endpoints use `Authorization: Bearer <YOUR-TOKEN>` and `Accept: application/vnd.github+json` headers, plus `X-GitHub-Api-Version: 2026-03-10`. Curl examples below omit these standard headers for brevity.


## Revoke all credential authorizations for an enterprise

```
POST /enterprises/{enterprise}/credential-authorizations/revoke-all
```

Revokes all credential authorizations for all organizations within the enterprise.
This includes any guest, outside, or repository collaborators.
For Enterprise Managed User (EMU) enterprises, you can optionally also destroy all
credentials (PATs v1, PATs v2, and SSH keys) owned by enterprise members by setting
the revoke_credentials parameter to true.
This operation is performed asynchronously. A background job will be queued to process
the revocations.
Warning

If you use a personal access token to call this endpoint, that token may also be
revoked or destroyed as part of this operation.

The authenticated user must be an enterprise owner or have the write_enterprise_credentials permission to use this endpoint.
OAuth app tokens and personal access tokens (classic) need the admin:enterprise scope to use this endpoint.


### Parameters


#### Headers


- **`accept`** (string)
  Setting to `application/vnd.github+json` is recommended.



#### Path and query parameters

- **`enterprise`** (string) (required)
  The slug version of the enterprise name.




#### Body parameters

- **`revoke_credentials`** (boolean)
  Whether to also destroy the actual credentials (PATs and SSH keys) owned by
enterprise members. This option is only available for Enterprise Managed User
(EMU) enterprises. When set to true, all PATs (v1 and v2) and SSH keys owned
by enterprise members will be destroyed in addition to the credential authorizations.
  Default: `false`





### HTTP response status codes


- **202** - Accepted - The revocation request has been queued


- **403** - Forbidden


- **404** - Resource not found


- **422** - Validation error - The revoke_credentials option is only available for EMU enterprises




### Code examples



#### Example

**Request:**

```curl
curl -L \
  -X POST \
  https://api.github.com/enterprises/ENTERPRISE/credential-authorizations/revoke-all \
  -d '{
  "revoke_credentials": false
}'
```

**Response schema (Status: 202):**

* `message`: string
* `warning`: string