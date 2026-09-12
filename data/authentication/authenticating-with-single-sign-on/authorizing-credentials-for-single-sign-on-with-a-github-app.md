# Authorizing credentials for single sign-on with a GitHub App

Authorize credentials for multiple organizations by allowing an enterprise-installed GitHub App to manage single sign-on (SSO) authorizations.

## About authorizing credentials with a GitHub App

By default, enterprise-installed GitHub Apps cannot authorize credentials. To reduce the number of times that enterprise members must authorize the same credential for individual organizations, you can allow an app to authorize existing personal access tokens (classic) or verified, user-owned SSH authentication keys. Up to 50 selected organizations are allowed per request.

To authorize a credential for a single organization without a GitHub App, see [Authorizing a personal access token for use with single sign-on](/en/enterprise-cloud@latest/authentication/authenticating-with-single-sign-on/authorizing-a-personal-access-token-for-use-with-single-sign-on) or [Authorizing an SSH key for use with single sign-on](/en/enterprise-cloud@latest/authentication/authenticating-with-single-sign-on/authorizing-an-ssh-key-for-use-with-single-sign-on).

## Prerequisites

Before the app can authorize credentials, the following requirements must be met:

* The enterprise must use enterprise-level SSO.
* The credential owner must be a member of every organization where the app will authorize the credential.

## Creating the GitHub App

1. Register a new app. For instructions, see [Registering a GitHub App](/en/enterprise-cloud@latest/apps/creating-github-apps/registering-a-github-app/registering-a-github-app#registering-a-github-app). The app must:

   * Be owned by the enterprise or an organization in the enterprise.
   * Have write access to the "Enterprise credentials" permission.

2. Note the app's client ID, then generate and securely store a private key. See [Managing private keys for GitHub Apps](/en/enterprise-cloud@latest/apps/creating-github-apps/authenticating-with-a-github-app/managing-private-keys-for-github-apps).

3. Install the app on your enterprise account. See [Installing a GitHub App on your enterprise](/en/enterprise-cloud@latest/apps/using-github-apps/installing-a-github-app-on-your-enterprise).

4. In the URL of the app's installation page, note the installation ID. The ID is the string of numbers at the end of the `/enterprises/ENTERPRISE/settings/installations/ID` URL.

## Allowing a GitHub App to authorize credentials

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.

2. Under **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> Settings**, click **Authentication security**.

3. Under "Credentials," enable **Allow GitHub Apps to authorize credentials**.

## Generating an installation access token

The app must use an enterprise installation access token to authenticate its API requests. Organization installation access tokens, user access tokens, and personal access tokens are not supported.

To generate an installation access token:

1. Use the app's client ID and private key to generate a JSON Web Token (JWT). See [Generating a JSON Web Token (JWT) for a GitHub App](/en/enterprise-cloud@latest/apps/creating-github-apps/authenticating-with-a-github-app/generating-a-json-web-token-jwt-for-a-github-app).
2. Use the JWT and enterprise installation ID to create an installation access token. See [Generating an installation access token for a GitHub App](/en/enterprise-cloud@latest/apps/creating-github-apps/authenticating-with-a-github-app/generating-an-installation-access-token-for-a-github-app).

The installation access token inherits the enterprise permissions granted to the app, cannot be scoped down, and expires after one hour.

## Finding credential identifiers

For credentials that are already authorized for an organization in your enterprise, an organization owner can use the REST API to obtain identifiers in bulk. See [REST API endpoints for organizations](/en/enterprise-cloud@latest/rest/orgs/orgs#list-saml-sso-authorizations-for-an-organization).

In the response, use `authorized_credential_id` for a personal access token (classic), or `fingerprint` for an SSH key. Do not use `credential_id`, which identifies the credential's authorization for that organization.

This endpoint does not return credentials that have not been authorized for the organization. To obtain an identifier for another credential, use one of these methods:

* For a personal access token (classic), open the token from the [token settings](https://github.com/settings/tokens) page. The token ID is the number at the end of the `/settings/tokens/ID` URL. Alternatively, if the token was used for an action recorded in the enterprise audit log, an enterprise owner can find the ID in the event's `token_id` field. The ID is available in the audit log only while an enterprise-visible event authenticated with that token is retained. Share the ID, not the token value. For more information, see [Managing your personal access tokens](/en/enterprise-cloud@latest/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens) and [Searching the audit log for your enterprise](/en/enterprise-cloud@latest/admin/monitoring-activity-in-your-enterprise/reviewing-audit-logs-for-your-enterprise/searching-the-audit-log-for-your-enterprise).
* For an SSH key, find the SHA-256 fingerprint for the verified, user-owned authentication key. For more information, see [Reviewing your SSH keys](/en/enterprise-cloud@latest/authentication/keeping-your-account-and-data-secure/reviewing-your-ssh-keys).

## Authorizing a credential

Use the REST API to authorize the credential for selected organizations. For example:

```shell
curl --request POST \
  --url "https://api.github.com/enterprises/ENTERPRISE/credential-authorizations" \
  --header "Accept: application/vnd.github+json" \
  --header "Authorization: Bearer INSTALLATION-ACCESS-TOKEN" \
  --header "X-GitHub-Api-Version: 2026-03-10" \
  --data '{
    "credential_id": 12345678,
    "credential_type": "classic_pat",
    "organizations": ["ORGANIZATION-1", "ORGANIZATION-2"]
  }'
```

Replace `ENTERPRISE` with the enterprise slug, `INSTALLATION-ACCESS-TOKEN` with the installation access token, and `ORGANIZATION-1` and `ORGANIZATION-2` with the organization slugs. Replace `12345678` with the ID of the personal access token (classic). To authorize an SSH key instead, replace `12345678` with the key's SHA-256 fingerprint and replace `classic_pat` with `ssh_key`.

For more information, see [REST API endpoints for enterprise credential authorizations](/en/enterprise-cloud@latest/rest/enterprise-admin/credential-authorizations).

## Disabling credential authorization by GitHub Apps

Disabling the setting prevents apps from creating new credential authorizations. Existing authorizations remain active until they are revoked, the credential is revoked or deleted, or the credential owner loses membership in the organization.

You can use the same REST API to revoke authorizations that an app created through enterprise delegation.