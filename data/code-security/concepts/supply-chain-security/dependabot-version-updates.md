# Dependabot version updates

You can use Dependabot to keep the packages you use updated to the latest versions.

## About Dependabot version updates

Dependabot takes the effort out of maintaining your dependencies. You can use it to ensure that your repository automatically keeps up with the latest releases of the packages and applications it depends on.

When Dependabot raises pull requests, these pull requests could be for *security* or *version* updates:

* *Dependabot security updates* are automated pull requests that help you update dependencies with known vulnerabilities.
* *Dependabot version updates* are automated pull requests that keep your dependencies updated, even when they don’t have any vulnerabilities. To check the status of version updates, navigate to the **Insights** tab of your repository, then select **Dependency Graph**, and Dependabot.

You enable Dependabot version updates by checking a `dependabot.yml` configuration file into your repository.

Dependabot and all related features are covered by [GitHub's Terms of Service](/en/site-policy/github-terms/github-terms-of-service).

## Updates for packages

The `dependabot.yml` configuration file specifies the location of the manifest, or of other package definition files, stored in your repository. Dependabot uses this information to check for outdated packages and applications. Dependabot determines if there is a new version of a dependency by looking at the semantic versioning ([semver](https://semver.org/)) of the dependency to decide whether it should update to that version. For information on the supported repositories and ecosystems, see [Dependabot supported ecosystems and repositories](/en/code-security/dependabot/ecosystems-supported-by-dependabot/supported-ecosystems-and-repositories).

The `dependabot.yml` file can also be configured to tell Dependabot how to maintain your dependencies. For more information, see [About the dependabot.yml file](/en/code-security/concepts/supply-chain-security/about-the-dependabot-yml-file).

For certain package managers, Dependabot version updates also supports vendoring. Vendored (or cached) dependencies are dependencies that are checked in to a specific directory in a repository rather than referenced in a manifest. Vendored dependencies are available at build time even if package servers are unavailable. Dependabot version updates can be configured to check vendored dependencies for new versions and update them if necessary.

When Dependabot identifies an outdated dependency, it raises a pull request to update the manifest to the latest version of the dependency. For vendored dependencies, Dependabot raises a pull request to replace the outdated dependency with the new version directly. You check that your tests pass, review the changelog and release notes included in the pull request summary, and then merge it. For more information, see [Configuring Dependabot version updates](/en/code-security/dependabot/dependabot-version-updates/configuring-dependabot-version-updates).

If you enable *security updates*, Dependabot also raises pull requests to update vulnerable dependencies. For more information, see [Dependabot security updates](/en/code-security/dependabot/dependabot-security-updates/about-dependabot-security-updates).

## Updates for actions

Actions are often updated with bug fixes and new features to make automated processes more reliable, faster, and safer. When you enable Dependabot version updates for GitHub Actions, Dependabot will help ensure that references to actions in a repository's *workflow\.yml* file and reusable workflows used inside workflows are kept up to date.

For each action in the file, Dependabot checks the action's reference (typically a version number or commit identifier associated with the action) against the latest version. If a more recent version of the action is available, Dependabot will send you a pull request that updates the reference in the workflow file to the latest version.

Dependabot also checks workflow files for uses of reusable workflows, and updates the Git reference for these called reusable workflows.

To enable this feature, see [Keeping your actions up to date with Dependabot](/en/code-security/how-tos/secure-your-supply-chain/secure-your-dependencies/keeping-your-actions-up-to-date-with-dependabot).

## About automatic deactivation of Dependabot updates

When maintainers of a repository stop interacting with Dependabot pull requests, Dependabot temporarily pauses its updates and lets you know, see [Dependabot update pull requests no longer generated](/en/code-security/dependabot/troubleshooting-dependabot/dependabot-updates-stopped).

## About notifications for Dependabot version updates

You can filter your notifications on GitHub to show notifications for pull requests created by Dependabot. For more information, see [Managing notifications from your inbox](/en/account-and-profile/managing-subscriptions-and-notifications-on-github/viewing-and-triaging-notifications/managing-notifications-from-your-inbox).