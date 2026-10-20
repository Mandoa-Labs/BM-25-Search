# Protecting endpoints with GitHub package firewall

Protect dependency installations on developer machines, AI agents, and CI runners with GitHub package firewall.

> \[!NOTE]
> This feature is currently in public preview and is subject to change.

## About GitHub package firewall

The GitHub package firewall sits between your endpoints and package registries. It evaluates package downloads against policies such as minimum package age and malware advisories, and blocks downloads that do not meet those policies. You can use it to protect dependency installations in CI builds, AI agent sessions, and local development.

To use the firewall, configure your enterprise's policy controls, then configure your endpoints to request packages through the firewall instead of directly from a public registry. You can also grant access to manage the policy through a custom role.

## Configuring policy controls

Enterprise security managers and enterprise administrators can configure policy controls.

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.
2. At the top of the page, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-law" aria-label="law" role="img"><path d="M8.75.75V2h.985c.304 0 .603.08.867.231l1.29.736c.038.022.08.033.124.033h2.234a.75.75 0 0 1 0 1.5h-.427l2.111 4.692a.75.75 0 0 1-.154.838l-.53-.53.529.531-.001.002-.002.002-.006.006-.006.005-.01.01-.045.04c-.21.176-.441.327-.686.45C14.556 10.78 13.88 11 13 11a4.498 4.498 0 0 1-2.023-.454 3.544 3.544 0 0 1-.686-.45l-.045-.04-.016-.015-.006-.006-.004-.004v-.001a.75.75 0 0 1-.154-.838L12.178 4.5h-.162c-.305 0-.604-.079-.868-.231l-1.29-.736a.245.245 0 0 0-.124-.033H8.75V13h2.5a.75.75 0 0 1 0 1.5h-6.5a.75.75 0 0 1 0-1.5h2.5V3.5h-.984a.245.245 0 0 0-.124.033l-1.289.737c-.265.15-.564.23-.869.23h-.162l2.112 4.692a.75.75 0 0 1-.154.838l-.53-.53.529.531-.001.002-.002.002-.006.006-.016.015-.045.04c-.21.176-.441.327-.686.45C4.556 10.78 3.88 11 3 11a4.498 4.498 0 0 1-2.023-.454 3.544 3.544 0 0 1-.686-.45l-.045-.04-.016-.015-.006-.006-.004-.004v-.001a.75.75 0 0 1-.154-.838L2.178 4.5H1.75a.75.75 0 0 1 0-1.5h2.234a.249.249 0 0 0 .125-.033l1.288-.737c.265-.15.564-.23.869-.23h.984V.75a.75.75 0 0 1 1.5 0Zm2.945 8.477c.285.135.718.273 1.305.273s1.02-.138 1.305-.273L13 6.327Zm-10 0c.285.135.718.273 1.305.273s1.02-.138 1.305-.273L3 6.327Z"></path></svg> Policies**.
3. In the sidebar, click **Package firewall**.
4. Configure the policy controls described in the following sections. These controls apply to all requests that pass through the firewall.

### Block known malware

When enabled, this control checks the GitHub Advisory Database for active malware advisories and blocks packages with a matching advisory. This control defaults to **On**.

### Block vulnerability advisories

This control checks the GitHub Advisory Database for vulnerabilities that affect the requested package version. Select the minimum advisory severity that blocks an installation: **Critical only**, **High or higher**, **Medium or higher**, or **Any severity**. This control defaults to **Critical only**.

### Block attestation downgrades

This control compares attestations for the requested package version with those of earlier versions. If the package previously had SLSA attestations but the requested version does not, the firewall blocks the download. Missing attestations can indicate a compromised publishing process. For more information about attestations, see [Artifact attestations](/en/actions/concepts/security/artifact-attestations). This control defaults to **On**.

### Block newly-introduced install scripts

This control checks whether the package recently added scripts that run during installation, such as `preinstall` or `postinstall` scripts. These scripts can run arbitrary commands on your system and can be used to steal credentials. This control defaults to **On**.

### Minimum package age

This control sets a cooldown period for newly published package versions. The firewall blocks versions that are newer than the configured minimum age, allowing time for threats to be discovered before you install them.

Set the minimum age to a value between 1 and 365 days, or set it to 0 to disable the control. The default is 1 day.

## Configuring endpoints to use the Package firewall

Configure your package manager to fetch packages from the firewall's URL instead of the default public registry.

### Authentication token

The registry URL is specific to your enterprise. Each request must include an authentication token associated with a user or bot account that is a member of the enterprise. The token does not need any elevated permission beyond **Read-only access to public repositories**. For more information, see [Managing your personal access tokens](/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens).

### Configuring npm

Use your user-level `.npmrc` file to configure npm. In the examples, replace `ENTERPRISE` with your enterprise slug. Set the `GITHUB_TOKEN` environment variable to a GitHub token with access to your enterprise. Store the token securely, such as in a CI secret, and do not commit it to a repository.

1. Add the following configuration to your user-level `.npmrc` file:

   ```text
   registry=https://package-firewall.githubapp.com/npm/enterprises/ENTERPRISE
   //package-firewall.githubapp.com/npm/enterprises/ENTERPRISE/:_authToken=${GITHUB_TOKEN}
   ```

Alternatively, configure the same settings from the command line:

```shell
npm config set registry \
  https://package-firewall.githubapp.com/npm/enterprises/ENTERPRISE
npm config set \
  '//package-firewall.githubapp.com/npm/enterprises/ENTERPRISE/:_authToken=${GITHUB_TOKEN}'
```

### Configuring Artifactory

You can configure JFrog Artifactory to retrieve packages through the firewall. Your endpoints continue to use Artifactory, which lets you combine public and private packages while applying firewall policies to packages retrieved through the firewall.

You must have administrator privileges in your Artifactory instance.

> \[!NOTE]
> Artifactory support is experimental. To share suggestions or concerns about Artifactory support, see the [community discussion](https://gh.io/package-fw-discussion).

1. In Artifactory, click the **Administration** tab, then click **Create a repository**.
2. Select **Remote** as the repository type, then select **npm** as the package type.
3. In the "Repository key" field, type a name such as `gh-package-firewall`.
4. In the "URL" field, type `https://package-firewall.githubapp.com/npm/enterprises/ENTERPRISE`, replacing `ENTERPRISE` with your enterprise slug.
5. In the "Password / Access Token" field, paste a valid personal access token, then select **Enable Token Authentication**.
6. Select the **Stage** where you want to use the firewall, based on your Artifactory configuration.
7. In the "Pattern" field, type `**/*` to include all package paths.
8. Click **Save**.
9. Create or update a virtual npm repository to include this remote and your private npm repositories. Exclude remotes that fetch packages directly from the public npm registry so they cannot bypass the firewall.
10. Follow the virtual repository's **Set me up** instructions to configure your endpoints.

## Fine-grained permissions

By default, enterprise administrators and enterprise security managers can modify the firewall policy. To grant other users access to view and change the policy, add the "Edit enterprise-level package firewall policy" fine-grained permission to a custom role, then assign that role to a team or individual.

## Managing exceptions

If the firewall blocks a package you need, you can request an exception to the policy. For example, a new package version that includes a security fix could be blocked by the minimum package age policy.

### Requesting an exception

When the firewall blocks a package, the npm output or CI/CD log includes a URL for requesting an exception. For example:

```text
npm notice testcontainers: 1 version blocked by package-firewall due to security policies (version cooldown). Request an override: https://github.com/enterprises/octocats/security/bypass-requests/package-firewall/new?ecosystem=npm&package=testcontainers
```

1. Open the URL in your browser.

2. Review the prefilled fields and provide any missing information:

   * "Repository": The repository where the block occurred
   * "Ecosystem": The package ecosystem (currently, only npm is supported)
   * "Package name": The package name, including the `@scope` prefix if applicable
   * "Version": The version you attempted to install
   * "Reason": Why the package should be unblocked
   * "Add a comment": Additional context for reviewers

3. Submit the request.

### Reviewing and approving exception requests

Enterprise administrators and enterprise security managers can review exception requests.

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.
2. At the top of the page, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality**.
3. In the sidebar, click **Package firewall bypass**.
4. In the "Package firewall bypass requests" list, use the search bar to find a request, then click the request.
5. In the "Review package allow override" dialog, review the requested exception.
6. Optionally, to allow all versions of the package, replace the requested version in the "Version or range to allow" field with `*`. This broadens the exception beyond the requested version.
7. Add a comment explaining your decision, then click **Approve request**.

For example, you might allow all versions of an enterprise-owned package rather than require a separate exception each time the minimum package age policy blocks a new version.

### Managing approvals

Approved bypass requests are added to the firewall policy. Enterprise administrators and enterprise security managers can review and remove outdated or unwanted exceptions, including exceptions added manually.

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.
2. At the top of the page, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-law" aria-label="law" role="img"><path d="M8.75.75V2h.985c.304 0 .603.08.867.231l1.29.736c.038.022.08.033.124.033h2.234a.75.75 0 0 1 0 1.5h-.427l2.111 4.692a.75.75 0 0 1-.154.838l-.53-.53.529.531-.001.002-.002.002-.006.006-.006.005-.01.01-.045.04c-.21.176-.441.327-.686.45C14.556 10.78 13.88 11 13 11a4.498 4.498 0 0 1-2.023-.454 3.544 3.544 0 0 1-.686-.45l-.045-.04-.016-.015-.006-.006-.004-.004v-.001a.75.75 0 0 1-.154-.838L12.178 4.5h-.162c-.305 0-.604-.079-.868-.231l-1.29-.736a.245.245 0 0 0-.124-.033H8.75V13h2.5a.75.75 0 0 1 0 1.5h-6.5a.75.75 0 0 1 0-1.5h2.5V3.5h-.984a.245.245 0 0 0-.124.033l-1.289.737c-.265.15-.564.23-.869.23h-.162l2.112 4.692a.75.75 0 0 1-.154.838l-.53-.53.529.531-.001.002-.002.002-.006.006-.016.015-.045.04c-.21.176-.441.327-.686.45C4.556 10.78 3.88 11 3 11a4.498 4.498 0 0 1-2.023-.454 3.544 3.544 0 0 1-.686-.45l-.045-.04-.016-.015-.006-.006-.004-.004v-.001a.75.75 0 0 1-.154-.838L2.178 4.5H1.75a.75.75 0 0 1 0-1.5h2.234a.249.249 0 0 0 .125-.033l1.288-.737c.265-.15.564-.23.869-.23h.984V.75a.75.75 0 0 1 1.5 0Zm2.945 8.477c.285.135.718.273 1.305.273s1.02-.138 1.305-.273L13 6.327Zm-10 0c.285.135.718.273 1.305.273s1.02-.138 1.305-.273L3 6.327Z"></path></svg> Policies**.
3. In the sidebar, click **Package firewall**.
4. Under "Overrides", click **Package overrides**.
5. To remove an exception from the policy, next to the exception, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-trash" aria-label="Delete exception" role="img"><path d="M11 1.75V3h2.25a.75.75 0 0 1 0 1.5H2.75a.75.75 0 0 1 0-1.5H5V1.75C5 .784 5.784 0 6.75 0h2.5C10.216 0 11 .784 11 1.75ZM4.496 6.675l.66 6.6a.25.25 0 0 0 .249.225h5.19a.25.25 0 0 0 .249-.225l.66-6.6a.75.75 0 0 1 1.492.149l-.66 6.6A1.748 1.748 0 0 1 10.595 15h-5.19a1.75 1.75 0 0 1-1.741-1.575l-.66-6.6a.75.75 0 1 1 1.492-.15ZM6.5 1.75V3h3V1.75a.25.25 0 0 0-.25-.25h-2.5a.25.25 0 0 0-.25.25Z"></path></svg>.

## Further reading

* [Creating custom roles in an enterprise](/en/enterprise-cloud@latest/admin/managing-accounts-and-repositories/managing-roles-in-your-enterprise/create-custom-roles)
* [Assigning roles to people in an enterprise](/en/enterprise-cloud@latest/admin/managing-accounts-and-repositories/managing-roles-in-your-enterprise/assign-roles)
* [Browsing security advisories in the GitHub Advisory Database](/en/code-security/how-tos/report-and-fix-vulnerabilities/fix-reported-vulnerabilities/browse-advisory-database)