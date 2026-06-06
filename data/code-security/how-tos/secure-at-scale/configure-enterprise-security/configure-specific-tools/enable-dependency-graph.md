# Enabling the dependency graph for your enterprise

You can allow users to identify their projects' dependencies by enabling the dependency graph.

## About the dependency graph

The dependency graph is a summary of the manifest and lock files stored in a repository and any dependencies that are submitted for the repository using the dependency submission API. For each repository, it shows dependencies, the ecosystems and packages it depends on.

For each dependency, you can see the version,  the manifest file which included it, and whether it has known vulnerabilities. For package ecosystems supporting transitive dependencies, the relationship status will be displayed and you can click "<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="Show dependency options" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>", then "Show paths", to see the transitive path which brought in the dependency.

You can also search for a specific dependency using the search bar. Dependencies are sorted automatically with vulnerable packages at the top.

GitHub does not retrieve license information for dependencies, and does not calculate information about dependents, the repositories and packages that depend on a repository. For more information, see [Dependency graph](/en/enterprise-server@3.21/code-security/supply-chain-security/understanding-your-software-supply-chain/about-the-dependency-graph)

After you enable the dependency graph, users will have access to the dependency review feature. Dependency review helps you understand dependency changes and the security impact of these changes at every pull request. For more information, see [Dependency review](/en/enterprise-server@3.21/code-security/supply-chain-security/understanding-your-software-supply-chain/about-dependency-review).

After you enable the dependency graph for your enterprise, you can enable Dependabot to detect insecure dependencies in your repository and automatically fix the vulnerabilities. For more information, see [Enabling Dependabot for your enterprise](/en/enterprise-server@3.21/admin/configuration/configuring-github-connect/enabling-dependabot-for-your-enterprise).

You can enable the dependency graph via the Management Console or the administrative shell. We recommend using the Management Console unless your instance uses clustering.

## Enabling the dependency graph via the Management Console

If your instance uses clustering, you cannot enable the dependency graph with the Management Console and must use the administrative shell instead. For more information, see [Enabling the dependency graph via the administrative shell](#enabling-the-dependency-graph-via-the-administrative-shell).

1. Sign in to your GitHub Enterprise Server instance at `http(s)://HOSTNAME/login`.

2. From an administrative account on GitHub Enterprise Server, in the upper-right corner of any page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="Site admin" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg>.

3. If you're not already on the "Site admin" page, in the upper-left corner, click **Site admin**.

4. In the "<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="rocket" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Site admin" sidebar, click **Management Console**.

5. In the "Settings" sidebar, click **Security**.

6. Under "Security," select **Dependency graph**.

7. Under the "Settings" sidebar, click **Save settings**.

   > \[!NOTE]
   > Saving settings in the Management Console restarts system services, which could result in user-visible downtime.

8. Wait for the configuration run to complete.

9. Click **Visit your instance**.

## Enabling the dependency graph via the administrative shell

1. Sign in to your GitHub Enterprise Server instance at `http(s)://HOSTNAME/login`.

2. In the administrative shell, enable the dependency graph:

   ```shell
   ghe-config app.dependency-graph.enabled true
   ```

   > \[!NOTE]
   > For more information about enabling access to the administrative shell via SSH, see [Accessing the administrative shell (SSH)](/en/enterprise-server@3.21/admin/configuration/configuring-your-enterprise/accessing-the-administrative-shell-ssh).

3. Apply the configuration.

   ```shell
   ghe-config-apply
   ```

4. Return to GitHub Enterprise Server.