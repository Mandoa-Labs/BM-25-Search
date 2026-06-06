# Configuring access to private registries for Dependabot

You can configure Dependabot to access dependencies stored in private registries. You can store authentication information, like passwords and access tokens, as encrypted secrets and then reference these in the Dependabot configuration file. If you have registries on private networks, you can also configure Dependabot access when running Dependabot on self-hosted runners.

## About private registries

Dependabot version updates keeps your dependencies up-to-date and Dependabot security updates updates vulnerable dependencies. Dependabot can access public registries. In addition, you can give Dependabot access to private package registries and private GitHub repositories so that you can keep your private and innersource dependencies as up-to-date and secure as your public dependencies.

In most ecosystems, private dependencies are usually published to private package registries. These private registries are similar to their public equivalents, but they require authentication.

For specific ecosystems, you can configure Dependabot to access *only* private registries by removing calls to public registries. For more information, see [Removing Dependabot access to public registries](/en/code-security/dependabot/maintain-dependencies/removing-dependabot-access-to-public-registries).

To allow Dependabot access to registries hosted privately or restricted to internal networks, configure Dependabot to run on GitHub Actions self-hosted runners. For more information, see [Configuring Dependabot on self-hosted runners](/en/code-security/dependabot/maintain-dependencies/managing-dependabot-on-self-hosted-runners).

## Configuring private registries

You can configure Dependabot's access to private registries at the org-level.

Organization-level registries support **Token**, **Username and password**, and **OIDC** authentication.

For more information about configuration, see [Giving security features access to private registries](/en/code-security/securing-your-organization/enabling-security-features-in-your-organization/giving-org-access-private-registries).

You can also configure Dependabot's access to private registries in the `dependabot.yml` file.
The top-level `registries` key is optional and specifies authentication details.

There are 2 locations in the `dependabot.yml` file where you can use the `registries` key:

* At the top level, where you define the registries and their access information, if needed.
* Within the `updates` blocks, where you can use `registries: "*"` to tell Dependabot to use any or all of the registries you defined at the top level.

```yaml
# registries: gradle-artifactory - provides access details for the gradle-artifactory registry
# registries: "*" - allows Dependabot to use all the defined registries specified at the top level

version: 2
registries:
  gradle-artifactory:
    type: maven-repository
    url: https://acme.jfrog.io/artifactory/my-gradle-registry
    username: octocat
    password: ${{secrets.MY_ARTIFACTORY_PASSWORD}}
updates:
  - package-ecosystem: "gradle"
    directory: "/"
    registries: "*"
    schedule:
      interval: "monthly"

```

You use the following options to specify access settings. Registry settings must contain a `type` and a `url`, and typically either a `username` and `password` combination or a `token`.

| Parameters             | Purpose                                                                                                                                                                                               |
| :--------------------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `REGISTRY_NAME`        | **Required:** Defines an identifier for the registry.                                                                                                                                                 |
| `type`                 | **Required:** Identifies the type of registry.                                                                                                                                                        |
| Authentication details | **Required:** The parameters supported for supplying authentication details vary for registries of different types.                                                                                   |
| `url`                  | **Required:** The URL to use to access the dependencies in this registry. The protocol is optional. If not specified, `https://` is assumed. Dependabot adds or ignores trailing slashes as required. |
| `replaces-base`        | If the boolean value is `true`, Dependabot resolves dependencies using the specified `url` rather than the base URL of that ecosystem.                                                                |

For more information about the configuration options that are available and about the supported types, see [Dependabot options reference](/en/code-security/reference/supply-chain-security/dependabot-options-reference#top-level-registries-key).

## Storing credentials for Dependabot to use

To give Dependabot access to the private registries supported by GitHub, you store the registry’s access token or secret in the secret store for your repository or organization.

### About encrypted secrets for Dependabot

Dependabot secrets are encrypted credentials that you create at either the organization level or the repository level.
When you add a secret at the organization level, you can specify which repositories can access the secret. You can use secrets to allow Dependabot to update dependencies located in private package registries. When you add a secret, it's encrypted before it reaches GitHub and it remains encrypted until it's used by Dependabot to access a private package registry.

Dependabot secrets also include secrets that are used by GitHub Actions workflows triggered by Dependabot pull requests. Dependabot itself may not use these secrets, but the workflows require them. For more information, see [Troubleshooting Dependabot on GitHub Actions](/en/code-security/dependabot/troubleshooting-dependabot/troubleshooting-dependabot-on-github-actions#accessing-secrets).

After you add a Dependabot secret, you can reference it in the `dependabot.yml` configuration file like this: `${{secrets.NAME}}`, where "NAME" is the name you chose for the secret. For example:

```yaml copy
password: ${{secrets.MY_ARTIFACTORY_PASSWORD}}
```

#### Naming your secrets

The name of a Dependabot secret:

* Can only contain alphanumeric characters (`[A-Z]`, `[0-9]`) or underscores (`_`). Spaces are not allowed. If you enter lowercase letters these are changed to uppercase.
* Must not start with the `GITHUB_` prefix.
* Must not start with a number.

### Adding a repository secret for Dependabot

To create secrets for a personal account repository, you must be the repository owner. To create secrets for an organization repository, you must have `admin` access.

1. On GitHub, navigate to the main page of the repository.
2. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> Settings**. If you cannot see the "Settings" tab, select the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="More" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>** dropdown menu, then click **Settings**.

   ![Screenshot of a repository header showing the tabs. The "Settings" tab is highlighted by a dark orange outline.](/assets/images/help/repository/repo-actions-settings.png)
3. In the "Security" section of the sidebar, select **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-key-asterisk" aria-label="key-asterisk" role="img"><path d="M0 2.75A2.75 2.75 0 0 1 2.75 0h10.5A2.75 2.75 0 0 1 16 2.75v10.5A2.75 2.75 0 0 1 13.25 16H2.75A2.75 2.75 0 0 1 0 13.25ZM2.75 1.5c-.69 0-1.25.56-1.25 1.25v10.5c0 .69.56 1.25 1.25 1.25h10.5c.69 0 1.25-.56 1.25-1.25V2.75c0-.69-.56-1.25-1.25-1.25Z"></path><path d="M8 4a.75.75 0 0 1 .75.75V6.7l1.69-.975a.75.75 0 0 1 .75 1.3L9.5 8l1.69.976a.75.75 0 0 1-.75 1.298L8.75 9.3v1.951a.75.75 0 0 1-1.5 0V9.299l-1.69.976a.75.75 0 0 1-.75-1.3L6.5 8l-1.69-.975a.75.75 0 0 1 .75-1.3l1.69.976V4.75A.75.75 0 0 1 8 4Z"></path></svg> Secrets and variables**, then click **Dependabot**.
4. Click **New repository secret**.
5. Type a name for your secret in the **Name** input box.
6. Enter the value for your secret.
7. Click **Add secret**.

   The name of the secret is listed on the Dependabot secrets page. You can click **Update** to change the secret value. You can click **Remove** to delete the secret.

### Adding an organization secret for Dependabot

When creating a secret in an organization, you can use a policy to limit which repositories can access that secret. For example, you can grant access to all repositories, or limit access to only private repositories or a specified list of repositories.

To create secrets at the organization level, you must have `admin` access.

1. On GitHub, navigate to the main page of the organization.

2. Under your organization name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> Settings**. If you cannot see the "Settings" tab, select the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="More" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>** dropdown menu, then click **Settings**.

   ![Screenshot of the tabs in an organization's profile. The "Settings" tab is outlined in dark orange.](/assets/images/help/discussions/org-settings-global-nav-update.png)

3. In the "Security" section of the sidebar, select **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-key-asterisk" aria-label="key-asterisk" role="img"><path d="M0 2.75A2.75 2.75 0 0 1 2.75 0h10.5A2.75 2.75 0 0 1 16 2.75v10.5A2.75 2.75 0 0 1 13.25 16H2.75A2.75 2.75 0 0 1 0 13.25ZM2.75 1.5c-.69 0-1.25.56-1.25 1.25v10.5c0 .69.56 1.25 1.25 1.25h10.5c.69 0 1.25-.56 1.25-1.25V2.75c0-.69-.56-1.25-1.25-1.25Z"></path><path d="M8 4a.75.75 0 0 1 .75.75V6.7l1.69-.975a.75.75 0 0 1 .75 1.3L9.5 8l1.69.976a.75.75 0 0 1-.75 1.298L8.75 9.3v1.951a.75.75 0 0 1-1.5 0V9.299l-1.69.976a.75.75 0 0 1-.75-1.3L6.5 8l-1.69-.975a.75.75 0 0 1 .75-1.3l1.69.976V4.75A.75.75 0 0 1 8 4Z"></path></svg> Secrets and variables**, then click **Dependabot**. Ignore the "Private Registries" option, this is used only by code scanning default setup.

4. Click **New organization secret**.

5. Type a name for your secret in the **Name** input box.

6. Enter the **Value** for your secret.

7. From the **Repository access** dropdown list, choose an access policy.

8. If you chose **Selected repositories**:

   * Click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="selected repositories" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg>.
   * In the dialog box, select the repositories that can access this secret.
   * Click **Update selection**.

9. Click **Add secret**.

   The name of the secret is listed on the Dependabot secrets page. You can click **Update** to change the secret value or its access policy. You can click **Remove** to delete the secret.

## Configuring firewall IP rules

You can add Dependabot-related IP addresses to your registries IP allow list.

If your private registry is configured with an IP allow list, you can find the IP addresses Dependabot uses to access the registry in the meta API endpoint, under the `actions` key. For more information, see [REST API endpoints for meta data](/en/rest/meta/meta) and [Dependabot on GitHub Actions runners](/en/code-security/dependabot/working-with-dependabot/about-dependabot-on-github-actions-runners).

## Using OIDC for authentication

Dependabot can use OpenID Connect (OIDC) to authenticate with private registries, eliminating the need to store long-lived credentials as repository secrets.

With OIDC-based authentication, Dependabot update jobs can dynamically obtain short-lived credentials from your cloud identity provider, just like GitHub Actions workflows using OIDC federation.

> \[!TIP]
> OIDC authentication is also available for **organization-level** private registries, which you can configure through the organization settings UI or the REST API. For more information, see [Giving security features access to private registries](/en/code-security/securing-your-organization/enabling-security-features-in-your-organization/giving-org-access-private-registries#configuring-oidc-authentication-for-a-private-registry).

Dependabot supports OIDC authentication for any registry type that uses `username` and `password` authentication, when the registry is hosted on one of the following providers:

* AWS CodeArtifact
* Azure DevOps Artifacts
* Cloudsmith
* Google Cloud Artifact Registry
* JFrog Artifactory

To configure OIDC authentication, you need to specify different values instead of `username` and `password` in your registry configuration.

### AWS CodeArtifact

AWS CodeArtifact requires the values `aws-region`, `account-id`, `role-name`, `domain`, and `domain-owner`. The `audience` field is optional.

```yaml
registries:
  my-aws-codeartifact-feed:
    type: npm-registry
    url: https://MY_DOMAIN-MY-ACCOUNT_ID.d.codeartifact.REGION.amazonaws.com/npm/MY_REPOSITORY/
    aws-region: REGION
    account-id: '123456789012'
    role-name: MY_ROLE_NAME
    domain: MY_DOMAIN
    domain-owner: '987654321098'
    audience: MY_AUDIENCE  # if required by your feed
```

### Azure DevOps Artifacts

Azure DevOps Artifacts requires the values `tenant-id` and `client-id`:

```yaml
registries:
  my-azure-devops-artifacts-feed:
    type: npm-registry
    url: https://pkgs.dev.azure.com/MY-ORGANIZATION/MY-PROJECT/_packaging/MY-FEED/npm/registry/
    tenant-id: ${{ secrets.AZURE_TENANT_ID }}
    client-id: ${{ secrets.AZURE_CLIENT_ID }}
```

### Cloudsmith

Cloudsmith requires the values `namespace`, `service-slug`, and `audience`. The `api-host` field is optional and defaults to `api.cloudsmith.io`:

```yaml
registries:
  my-cloudsmith-feed:
    type: npm-registry
    url: https://dl.cloudsmith.io/MY-NAMESPACE/MY-REPOSITORY/npm/
    namespace: MY-NAMESPACE
    service-slug: MY-SERVICE-SLUG
    audience: https://github.com/GITHUB-ORG
    api-host: api.cloudsmith.io  # if required by your feed
```

### Google Cloud Artifact Registry

Google Cloud Artifact Registry requires the values `url` and
`workload-identity-provider`. The values `service-account` and `audience` are
optional:

```yaml
registries:
  my-gcp-artifact-registry:
    type: docker-registry
    url: https://REGION-docker.pkg.dev
    workload-identity-provider: projects/PROJECT-NUMBER/locations/global/workloadIdentityPools/POOL/providers/PROVIDER
    service-account: SA-NAME@PROJECT-ID.iam.gserviceaccount.com  # if required by your provider
    audience: MY-AUDIENCE  # if required by your provider
```

### JFrog Artifactory

JFrog Artifactory requires the values `url` and `jfrog-oidc-provider-name`.  The values `audience` and `identity-mapping-name` are optional:

```yaml
registries:
  my-jfrog-artifactory-feed:
    type: npm-registry
    url: https://JFROG-PLATFORM-URL/artifactory/api/npm/MY-REPOSITORY
    jfrog-oidc-provider-name: MY-PROVIDER
    audience: MY-AUDIENCE  # if required by your feed
    identity-mapping-name: MY-IDENTITY-MAPPING  # if required by your feed
```

For more information about how OIDC works, see [OpenID Connect](/en/actions/concepts/security/openid-connect).

## Allowing external code execution

When you give Dependabot access to one or more registries, external code execution is automatically disabled to protect your code from compromised packages. However, some version updates may fail.

If you need to allow Dependabot to access a private package registry and enable limited external code execution, you can set `insecure-external-code-execution` to `allow`. Allowing Dependabot to execute external code in the manifest during updates is not as scary as it sounds:

* Any external code execution will only have access to the package managers in the registries associated with the enclosing `updates` setting.
* There is no access allowed to any of the registries defined in the top level `registries` configuration.

It is common for tooling, such as `bundler`, `mix`, `pip`, and `swift`, to allow the execution of external code by default.

In this example, the configuration file allows Dependabot to access the `ruby-github` private package registry. In the same `updates`setting, `insecure-external-code-execution`is set to `allow`, which means that the code executed by dependencies will only access the `ruby-github` registry, and not the `dockerhub` registry.

```yaml copy
# Allow external code execution when updating dependencies from private registries

version: 2
registries:
  ruby-github:
    type: rubygems-server
    url: https://rubygems.pkg.github.com/octocat/github_api
    token: ${{secrets.MY_GITHUB_PERSONAL_TOKEN}}
updates:
  - package-ecosystem: "bundler"
    directory: "/rubygems-server"
    insecure-external-code-execution: allow
    registries: "*"
    schedule:
      interval: "monthly"
```

## Supported private registries

Examples of how to configure access to the private registries supported by Dependabot.

* [`cargo-registry`](#cargo-registry)
* [`composer-repository`](#composer-repository)
* [`docker-registry`](#docker-registry)
* [`git`](#git)
* [`goproxy-server`](#goproxy-server)
* [`hex-organization`](#hex-organization)
* [`hex-repository`](#hex-repository)
* [`maven-repository`](#maven-repository)
* [`npm-registry`](#npm-registry)
* [`nuget-feed`](#nuget-feed)
* [`pub-repository`](#pub-repository)
* [`python-index`](#python-index)
* [`rubygems-server`](#rubygems-server)
* [`terraform-registry`](#terraform-registry)

### `cargo-registry`

The `cargo-registry` type supports a token.

This registry type will prefix-match the path provided in the `url` option. This means you can provide multiple credentials to the same host, which can be used to access distinct paths. However, if you don't have multiple registries on the same host, we recommend that you omit the path from the `url`, so that all paths to the registry will receive credentials.

```yaml
registries:
  cargo-example:
    type: cargo-registry
    registry: "name-of-your-registry"
    url: https://cargo.cloudsmith.io/foobaruser/test/
    token: "Token ${{secrets.CARGO_TOKEN}}"
```

We tested this configuration against the `https://cargo.cloudsmith.io` private registry.

### `composer-repository`

The `composer-repository` type supports username and password. If the account is a GitHub account, you can use a GitHub personal access token in place of the password.

This registry type will prefix-match the path provided in the `url` option. This means you can provide multiple credentials to the same host, which can be used to access distinct paths. However, if you don't have multiple registries on the same host, we recommend that you omit the path from the `url`, so that all paths to the registry will receive credentials.

```yaml copy
registries:
  composer:
    type: composer-repository
    url: https://repo.packagist.com/example-company/
    username: octocat
    password: ${{secrets.MY_PACKAGIST_PASSWORD}}
```

### `docker-registry`

Dependabot works with any container registries that implement the OCI container registry spec. For more information, see <https://github.com/opencontainers/distribution-spec/blob/main/spec.md>. Dependabot supports authentication to private registries via a central token service or HTTP Basic Auth. For further details, see [Token Authentication Specification](https://docs.docker.com/registry/spec/auth/token/) in the Docker documentation and [Basic access authentication](https://en.wikipedia.org/wiki/Basic_access_authentication) on Wikipedia.

The `docker-registry` type supports username and password. If the account is a GitHub account, you can use a GitHub personal access token in place of the password.

This registry type will prefix-match the path provided in the `url` option. This means you can provide multiple credentials to the same host, which can be used to access distinct paths. However, if you don't have multiple registries on the same host, we recommend that you omit the path from the `url`, so that all paths to the registry will receive credentials.

```yaml copy
registries:
  dockerhub:
    type: docker-registry
    url: https://registry.hub.docker.com
    username: octocat
    password: ${{secrets.MY_DOCKERHUB_PASSWORD}}
    replaces-base: true
```

The `docker-registry` type can also be used to pull from private Amazon ECR using static AWS credentials.

```yaml copy
registries:
  ecr-docker:
    type: docker-registry
    url: https://1234567890.dkr.ecr.us-east-1.amazonaws.com
    username: ${{secrets.ECR_AWS_ACCESS_KEY_ID}}
    password: ${{secrets.ECR_AWS_SECRET_ACCESS_KEY}}
    replaces-base: true
```

### `git`

The `git` type supports username and password. If the account is a GitHub account, you can use a GitHub personal access token in place of the password.

```yaml copy
registries:
  github-octocat:
    type: git
    url: https://github.com
    username: x-access-token
    password: ${{secrets.MY_GITHUB_PERSONAL_TOKEN}}
```

### `goproxy-server`

The `goproxy-server` type supports username and password. If the account is a GitHub account, you can use a GitHub personal access token in place of the password.

This registry type will prefix-match the path provided in the `url` option. This means you can provide multiple credentials to the same host, which can be used to access distinct paths. However, if you don't have multiple registries on the same host, we recommend that you omit the path from the `url`, so that all paths to the registry will receive credentials.

```yaml copy
registries:
  my-private-registry:
    type: goproxy-server
    url: https://acme.jfrog.io/artifactory/api/go/my-repo
    username: octocat
    password: ${{secrets.MY_GO_REGISTRY_TOKEN}}
```

### `helm-registry`

The `helm-registry` type only supports HTTP Basic Auth and does not support OCI-compliant registries. If you need to access an OCI-compliant registry for Helm charts, configure a [`docker-registry`](#docker-registry) instead.

The `helm-registry` type supports username and password. If the account is a GitHub account, you can use a GitHub personal access token in place of the password.

This registry type will prefix-match the path provided in the `url` option. This means you can provide multiple credentials to the same host, which can be used to access distinct paths. However, if you don't have multiple registries on the same host, we recommend that you omit the path from the `url`, so that all paths to the registry will receive credentials.

```yaml copy
registries:
  helm_registry:
    type: helm-registry
    url: https://registry.example.com
    username: octocat
    password: ${{secrets.MY_REGISTRY_PASSWORD}}
```

### `hex-organization`

The `hex-organization` type supports organization and key.

This registry type will prefix-match the path provided in the `url` option. This means you can provide multiple credentials to the same host, which can be used to access distinct paths. However, if you don't have multiple registries on the same host, we recommend that you omit the path from the `url`, so that all paths to the registry will receive credentials.

```yaml copy
registries:
  github-hex-org:
    type: hex-organization
    organization: github
    key: ${{secrets.MY_HEX_ORGANIZATION_KEY}}
```

### `hex-repository`

The `hex-repository` type supports an authentication key.

`repo` is a required field, which must match the name of the repository used in your dependency declaration.

The `public-key-fingerprint` is an optional configuration field, representing the fingerprint of the public key for the Hex repository. `public-key-fingerprint` is used by Hex to establish trust with the private repository. The `public-key-fingerprint` field can be either listed in plaintext or stored as a Dependabot secret.

```yaml copy
registries:
   github-hex-repository:
     type: hex-repository
     repo: private-repo
     url: https://private-repo.example.com
     auth-key: ${{secrets.MY_AUTH_KEY}}
     public-key-fingerprint: ${{secrets.MY_PUBLIC_KEY_FINGERPRINT}}
```

### `maven-repository`

The `maven-repository` type supports username, password and replaces-base. If the account is a GitHub account, you can use a GitHub personal access token in place of the password.

This registry type will prefix-match the path provided in the `url` option. This means you can provide multiple credentials to the same host, which can be used to access distinct paths. However, if you don't have multiple registries on the same host, we recommend that you omit the path from the `url`, so that all paths to the registry will receive credentials.

```yaml copy
registries:
  maven-artifactory:
    type: maven-repository
    url: https://acme.jfrog.io/artifactory/my-maven-registry
    username: octocat
    password: ${{secrets.MY_ARTIFACTORY_PASSWORD}}
    replaces-base: true
```

You can also use OIDC authentication to access JFrog Artifactory. With OIDC, Dependabot dynamically obtains short-lived credentials instead of using static credentials.

```yaml copy
registries:
  maven-artifactory-oidc:
    type: maven-repository
    url: https://acme.jfrog.io/artifactory/my-maven-registry
    tenant-id: ${{secrets.ARTIFACTORY_TENANT_ID}}
    client-id: ${{secrets.ARTIFACTORY_CLIENT_ID}}
    replaces-base: true
```

### `npm-registry`

The `npm-registry` type supports username and password, or token. If the account is a GitHub account, you can use a GitHub personal access token in place of the password.

When using username and password, your `.npmrc`'s auth token may contain a `base64` encoded `_password`; however, the password referenced in your Dependabot configuration file must be the original (unencoded) password.

> \[!NOTE]
> When using `npm.pkg.github.com`, don't include a path. Instead use the `https://npm.pkg.github.com` URL without a path.

```yaml copy
registries:
  npm-npmjs:
    type: npm-registry
    url: https://registry.npmjs.org
    username: octocat
    password: ${{secrets.MY_NPM_PASSWORD}}  # Must be an unencoded password
    replaces-base: true
```

```yaml copy
registries:
  npm-github:
    type: npm-registry
    url: https://npm.pkg.github.com
    token: ${{secrets.MY_GITHUB_PERSONAL_TOKEN}}
    replaces-base: true
```

For security reasons, Dependabot does not set environment variables. Yarn (v2 and later) requires that any accessed environment variables are set. When accessing environment variables in your `.yarnrc.yml` file, you should provide a fallback value such as `${ENV_VAR-fallback}` or `${ENV_VAR:-fallback}`. For more information, see [Yarnrc files](https://yarnpkg.com/configuration/yarnrc) in the Yarn documentation.

### `nuget-feed`

The `nuget-feed` type supports username and password, or token. If the account is a GitHub account, you can use a GitHub personal access token in place of the password.

`nuget-feed` doesn't support the `replaces-base` parameter.

```yaml copy
registries:
  nuget-example:
    type: nuget-feed
    url: https://nuget.example.com/v3/index.json
    username: octocat@example.com
    password: ${{secrets.MY_NUGET_PASSWORD}}
```

```yaml copy
registries:
  nuget-azure-devops:
    type: nuget-feed
    url: https://pkgs.dev.azure.com/.../_packaging/My_Feed/nuget/v3/index.json
    username: octocat@example.com
    password: ${{secrets.MY_AZURE_DEVOPS_TOKEN}}
```

You can also use OIDC authentication to access Azure DevOps Artifacts. With OIDC, Dependabot dynamically obtains short-lived credentials instead of using static credentials.

```yaml copy
registries:
  nuget-azure-devops-oidc:
    type: nuget-feed
    url: https://pkgs.dev.azure.com/MyOrganization/MyProject/_packaging/MyArtifactFeedName/nuget/v3/index.json
    tenant-id: ${{secrets.AZURE_TENANT_ID}}
    client-id: ${{secrets.AZURE_CLIENT_ID}}
```

The `AZURE_TENANT_ID` and `AZURE_CLIENT_ID` values can be obtained from the overview page of your Entra ID app registration.

### `pub-repository`

The `pub-repository` type supports a URL and a token.

```yaml copy
registries:
  my-pub-registry:
    type: pub-repository
    url: https://example-private-pub-repo.dev/optional-path
    token: ${{secrets.MY_PUB_TOKEN}}
updates:
  - package-ecosystem: "pub"
    directory: "/"
    schedule:
      interval: "weekly"
    registries:
      - my-pub-registry
```

### `python-index`

The `python-index` type supports username and password, or token. If the account is a GitHub account, you can use a GitHub personal access token in place of the password.

This registry type will prefix-match the path provided in the `url` option. This means you can provide multiple credentials to the same host, which can be used to access distinct paths. However, if you don't have multiple registries on the same host, we recommend that you omit the path from the `url`, so that all paths to the registry will receive credentials.

```yaml copy
registries:
  python-example:
    type: python-index
    url: https://example.com/_packaging/my-feed/pypi/example
    username: octocat
    password: ${{secrets.MY_BASIC_AUTH_PASSWORD}}
    replaces-base: true
```

```yaml copy
registries:
  python-azure:
    type: python-index
    url: https://pkgs.dev.azure.com/octocat/_packaging/my-feed/pypi/example
    username: octocat@example.com
    password: ${{secrets.MY_AZURE_DEVOPS_TOKEN}}
    replaces-base: true
```

You can also use OIDC authentication to access Azure DevOps Artifacts. With OIDC, Dependabot dynamically obtains short-lived credentials instead of using static credentials.

```yaml copy
registries:
  python-azure-oidc:
    type: python-index
    url: https://pkgs.dev.azure.com/octocat/_packaging/my-feed/pypi/example
    tenant-id: ${{secrets.AZURE_TENANT_ID}}
    client-id: ${{secrets.AZURE_CLIENT_ID}}
    replaces-base: true
```

### `rubygems-server`

The `rubygems-server` type supports username and password, or token. If the account is a GitHub account, you can use a GitHub personal access token in place of the password.

This registry type will prefix-match the path provided in the `url` option. This means you can provide multiple credentials to the same host, which can be used to access distinct paths. However, if you don't have multiple registries on the same host, we recommend that you omit the path from the `url`, so that all paths to the registry will receive credentials.

```yaml copy
registries:
  ruby-example:
    type: rubygems-server
    url: https://rubygems.example.com
    username: octocat@example.com
    password: ${{secrets.MY_RUBYGEMS_PASSWORD}}
    replaces-base: true
```

```yaml copy
registries:
  ruby-github:
    type: rubygems-server
    url: https://rubygems.pkg.github.com/octocat/github_api
    token: ${{secrets.MY_GITHUB_PERSONAL_TOKEN}}
    replaces-base: true
```

### `terraform-registry`

The `terraform-registry` type supports a token.

```yaml copy
registries:
  terraform-example:
    type: terraform-registry
    url: https://terraform.example.com
    token: ${{secrets.MY_TERRAFORM_API_TOKEN}}
```