# Exploring the dependencies of a repository

You can use the dependency graph to see the packages your project depends on. In addition, you can see any vulnerabilities detected in its dependencies.

## Viewing the dependency graph

The dependency graph shows the dependencies and dependents of your repository.  For each dependency, you can see the version, license information, the manifest file which included it, and whether it has known vulnerabilities. For package ecosystems supporting transitive dependencies, the relationship status will be displayed and you can click "<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="Show dependency options" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>", then "Show paths", to see the transitive path which brought in the dependency.

You can also search for a specific dependency using the search bar. Dependencies are sorted automatically with vulnerable packages at the top. For information about the detection of dependencies and which ecosystems are supported, see [Dependency graph supported package ecosystems](/en/code-security/supply-chain-security/understanding-your-software-supply-chain/dependency-graph-supported-package-ecosystems).

1. On GitHub, navigate to the main page of the repository.

2. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-graph" aria-label="graph" role="img"><path d="M1.5 1.75V13.5h13.75a.75.75 0 0 1 0 1.5H.75a.75.75 0 0 1-.75-.75V1.75a.75.75 0 0 1 1.5 0Zm14.28 2.53-5.25 5.25a.75.75 0 0 1-1.06 0L7 7.06 4.28 9.78a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042l3.25-3.25a.75.75 0 0 1 1.06 0L10 7.94l4.72-4.72a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042Z"></path></svg> Insights**.

   ![Screenshot of the main page of a repository. In the horizontal navigation bar, a tab, labeled with a graph icon and "Insights," is outlined in orange.](/assets/images/help/repository/repo-nav-insights-tab.png)

3. In the left sidebar, click **Dependency graph**.
   ![Screenshot of the "Dependency graph" tab. The tab is highlighted with an orange outline.](/assets/images/help/graphs/graphs-sidebar-dependency-graph.png)

4. Optionally, use the search bar to find a specific dependency or set of dependencies. You can use the keywords `ecosystem:` to show only packages of a certain type, or `relationship:` to show only direct or transitive dependencies (if the ecosystem supports transitivity). Plain words in search bar will only match package names.

5. Optionally, to view the repositories and packages that depend on your repository, under "Dependency graph", click **Dependents**.

   ![Screenshot of the "Dependency graph" page. The "Dependents" tab is highlighted with an orange outline.](/assets/images/help/graphs/dependency-graph-dependents-tab.png)

   > \[!NOTE] GitHub currently only determines dependents for public repositories.

### Dependencies view

For each dependency, you can see its ecosystem, the manifest file in which it was found, and its license (where detected).

* Dependencies for private repositories, private packages, or unrecognized files are shown in plain text.
* If the package manager for the dependency is in a public repository, you can hover on the dependency name to display a pop-up with the associated repository information.
* You can sort and filter dependencies by typing filters as `key:value` pairs into the search bar.

  * Use `ecosystem: <ecosystem-name>` to display dependencies for the selected ecosystem.
  * Use `relationship:` to filter the list by relationship status. Possible values are `direct`, `transitive`, and `inconclusive`. Alternatively, you can click the relationship label adjacent to a dependency name to only show dependencies of the same relationship status. This filter is only available for ecosystems with transitive dependency support. See [Dependency graph supported package ecosystems](/en/code-security/supply-chain-security/understanding-your-software-supply-chain/dependency-graph-supported-package-ecosystems) for more information.

Dependencies submitted to a project using the dependency submission API will show which detector was used for their submission and when they were submitted. For more information on using the dependency submission API, see [Using the dependency submission API](/en/code-security/supply-chain-security/understanding-your-software-supply-chain/using-the-dependency-submission-api).

If vulnerabilities have been detected in the repository, these are shown at the top of the view for users with access to Dependabot alerts.

### Dependents view

For public repositories, the dependents view shows how the repository is used by other repositories. To show only the repositories that contain a library in a package manager, click **NUMBER Packages** immediately above the list of dependent repositories. The dependent counts are approximate and may not always match the dependents listed.

## Further reading

* [Troubleshooting the dependency graph](/en/code-security/supply-chain-security/understanding-your-software-supply-chain/troubleshooting-the-dependency-graph)
* [Dependency graph](/en/code-security/supply-chain-security/understanding-your-software-supply-chain/about-the-dependency-graph)
* [Viewing and updating Dependabot alerts](/en/code-security/dependabot/dependabot-alerts/viewing-and-updating-dependabot-alerts)
* [Archiving your GitHub personal account and public repositories](/en/get-started/privacy-on-github)