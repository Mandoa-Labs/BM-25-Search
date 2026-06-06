# Supply chain security

GitHub helps you secure your supply chain, from understanding the dependencies in your environment, to knowing about vulnerabilities in those dependencies, and patching them.

## About supply chain security at GitHub

When developing a software project, you likely use other software to build and run your application, such as open-source libraries, frameworks or other tools. These resources are collectively referred to as your “dependencies”, because your project depends on them to function properly. Your project could rely on hundreds of these dependencies, forming what is known as your "supply chain".

Your supply chain can pose a security problem. If one of your dependencies has a known security weakness or a bug, malicious actors could exploit this vulnerability to, for example, insert malicious code ("malware"), steal sensitive data, or cause some other type of disruption to your project. This type of threat is called a "supply chain attack". Having vulnerable dependencies in your supply chain compromises the security of your own project, and you put your users at risk, too.

One of the most important things you can do to protect your supply chain is to patch your vulnerable dependencies and replace any malware.

You add dependencies directly to your supply chain when you specify them in a manifest file or a lockfile. Dependencies can also be included transitively, that is, even if you don’t specify a particular dependency, but a dependency of yours uses it, then you’re also dependent on that dependency.

GitHub offers a range of features to help you understand the dependencies in your environment, know about vulnerabilities in those dependencies, and patch them.

The supply chain features on GitHub are:

* **Dependency graph**
* **Dependency review**
* **Dependabot alerts**
  * **Dependabot malware alerts**
* **Dependabot updates**
  * **Dependabot security updates**
  * **Dependabot version updates**
* **Immutable releases**
* **Artifact attestations**

The dependency graph is central to supply chain security. The dependency graph identifies all upstream dependencies and public downstream dependents of a repository or package. Your repository’s dependency graph tracks and displays its dependencies and some of their properties, like vulnerability information.

The following supply chain features on GitHub rely on the information provided by the dependency graph.

* Dependency review uses the dependency graph to identify dependency changes and help you understand the security impact of these changes when you review pull requests.
* Dependabot cross-references dependency data provided by the dependency graph with the list of advisories published in the GitHub Advisory Database, scans your dependencies and generates Dependabot alerts when a potential vulnerability is detected.
* Dependabot security updates use the dependency graph and Dependabot alerts to help you update dependencies with known vulnerabilities in your repository.

Dependabot version updates don't use the dependency graph and rely on the semantic versioning of dependencies instead. Dependabot version updates help you keep your dependencies updated, even when they don’t have any vulnerabilities.

For best practice guides on end-to-end supply chain security including the protection of personal accounts, code, and build processes, see [Securing your end-to-end supply chain](/en/code-security/supply-chain-security/end-to-end-supply-chain/end-to-end-supply-chain-overview).

## Feature overview

### What is the dependency graph?

To generate the dependency graph, GitHub looks at a repository’s explicit dependencies declared in the manifest and lockfiles. When enabled, the dependency graph automatically parses all known package manifest files in the repository, and uses this to construct a graph with known dependency names and versions.

* The dependency graph includes information on your *direct* dependencies and *transitive* dependencies.
* The dependency graph is automatically updated when you push a commit to GitHub that changes or adds a supported manifest or lock file to the default branch, and when anyone pushes a change to the repository of one of your dependencies.
* The dependency graph can also include information you provide as your project is building using GitHub Actions. Some package ecosystems pull in most of their transitive dependencies at build time, so submitting dependency information as the build is happening provides a more complete view of the supply chain.
* You can see the dependency graph by opening the repository's main page on GitHub, and navigating to the **Insights** tab.
* If you have at least read access to the repository, you can export the dependency graph for the repository as an SPDX-compatible, Software Bill of Materials (SBOM), via the GitHub UI or GitHub REST API. For more information, see [Exporting a software bill of materials for your repository](/en/code-security/supply-chain-security/understanding-your-software-supply-chain/exporting-a-software-bill-of-materials-for-your-repository).

You can use the dependency submission API to submit dependencies from the package manager or ecosystem of your choice, even if the ecosystem is not supported by dependency graph for manifest or lock file analysis.
Dependencies submitted to a project using the dependency submission API will show which detector was used for their submission and when they were submitted. For more information on the dependency submission API, see [Using the dependency submission API](/en/code-security/supply-chain-security/understanding-your-software-supply-chain/using-the-dependency-submission-api).

For more information about the dependency graph, see [Dependency graph](/en/code-security/supply-chain-security/understanding-your-software-supply-chain/about-the-dependency-graph).

### What is dependency review?

Dependency review helps reviewers and contributors understand dependency changes and their security impact in every pull request.

* Dependency review tells you which dependencies were added, removed, or updated, in a pull request. You can use the release dates, popularity of dependencies, and vulnerability information to help you decide whether to accept the change.
* You can see the dependency review for a pull request by showing the rich diff on the **Files Changed** tab.

For more information about dependency review, see [Dependency review](/en/code-security/supply-chain-security/understanding-your-software-supply-chain/about-dependency-review).

### What is Dependabot?

Dependabot keeps your dependencies up to date by informing you of any security vulnerabilities in your dependencies and automatically opening pull requests to upgrade your dependencies. Dependabot pull requests will target the next available secure version when a Dependabot alert is triggered, or to the latest version when a release is published.

The term "Dependabot" encompasses the following features:

* Dependabot alerts: Displayed notification on the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab for the repository, and in the repository's dependency graph. The alert includes a link to the affected file in the project, and information about a fixed version.
* Dependabot updates:
  * Dependabot security updates: Triggered updates to upgrade your dependencies to a secure version when an alert is triggered.
  * Dependabot version updates: Scheduled updates to keep your dependencies up to date with the latest version.

Pull requests opened by Dependabot can trigger workflows that run actions. For more information, see [Automating Dependabot with GitHub Actions](/en/code-security/dependabot/working-with-dependabot/automating-dependabot-with-github-actions).

By default:

* If GitHub Actions is enabled for the repository, GitHub runs Dependabot updates on GitHub Actions.

* If GitHub Actions is not enabled for the repository, GitHub generates Dependabot alerts using its built-in Dependabot application.

For more information, see [Dependabot on GitHub Actions runners](/en/code-security/dependabot/working-with-dependabot/about-dependabot-on-github-actions-runners).

Dependabot security updates can fix vulnerable dependencies in GitHub Actions. When security updates are enabled, Dependabot will automatically raise a pull request to update vulnerable GitHub Actions used in your workflows to the minimum patched version. For more information, see [Dependabot security updates](/en/code-security/dependabot/dependabot-security-updates/about-dependabot-security-updates).

#### What are Dependabot alerts?

Dependabot alerts highlight repositories affected by a newly discovered vulnerability based on the dependency graph and the GitHub Advisory Database, which contains advisories for known vulnerabilities.

* Dependabot performs a scan to detect insecure dependencies and sends Dependabot alerts when:

  * A new advisory is added to the GitHub Advisory Database
  * The dependency graph for the repository changes
* Dependabot alerts are displayed on the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab for the repository and in the repository's dependency graph. The alert includes a link to the affected file in the project, and information about a fixed version.

For more information, see [Dependabot alerts](/en/code-security/dependabot/dependabot-alerts/about-dependabot-alerts).

##### What are Dependabot malware alerts?

Dependabot malware alerts flag malicious dependencies in your repositories. Dependabot generates alerts using the GitHub Advisory Database, which contains advisories for known vulnerabilities and malicious packages.

Dependabot scans for malicious packages and sends alerts when:

* A new advisory is added to the GitHub Advisory Database
* The dependency graph for a repository changes

You can view malware alerts for a repository:

* From the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab
* In the dependency graph

Each alert includes a link to the affected file in the project, as well as the patch version number for the package (if available).

#### What are Dependabot updates?

There are two types of Dependabot updates: Dependabot *security* updates and *version* updates. Dependabot generates automatic pull requests to update your dependencies in both cases, but there are several differences.

Dependabot security updates:

* Triggered by a Dependabot alert
* Update dependencies to the minimum version that resolves a known vulnerability
* Supported for ecosystems the dependency graph supports
* Does not require a configuration file, but you can use one to override the default behavior

Dependabot version updates:

* Requires a configuration file
* Run on a schedule you configure
* Update dependencies to the latest version that matches the configuration
* Supported for a different group of ecosystems

For more information about Dependabot updates, see [Dependabot security updates](/en/code-security/dependabot/dependabot-security-updates/about-dependabot-security-updates) and [Dependabot version updates](/en/code-security/dependabot/dependabot-version-updates/about-dependabot-version-updates).

### What are immutable releases?

Repositories can enable immutable releases to prevent the assets and associated Git tag of a release from being changed after publication. This reduces the risk of supply chain attacks by preventing attackers from injecting vulnerabilities into releases you consume. It also means projects that rely on specific releases are less likely to break.

Creating an immutable release automatically generates an attestation for the release. You can use this attestation to make sure the release and its artifacts match the published information.

### What are artifact attestations?

Software providers can generate attestations for software built with GitHub Actions. Attestations are cryptographically signed claims that establish the build's provenance (the source code and workflow run used to build it) or associated software bill of materials (SBOM).

You can increase supply chain security by verifying attestations for your dependencies. Although attestations do not guarantee security, they give you information about where and how software was built, so you can be more confident that your dependencies haven't been tampered with. You can gate deployments using a tool like the Kubernetes admissions controller to prevent unattested builds from being deployed.

When you use GitHub Actions to generate attestations for your organization's own builds, the built artifacts are automatically uploaded to the linked artifacts page. This platform allows you to view the storage and deployment records of all linked artifacts, so you can find the source code and workflow run used to build an artifact or filter security alerts based on deployment context.

## Feature availability

Public repositories:

* **Dependency graph:** Enabled by default and cannot be disabled.
* **Dependency review:** Enabled by default and cannot be disabled.
* **Dependabot alerts:** Not enabled by default. GitHub detects insecure dependencies and displays information in the dependency graph, but does not generate Dependabot alerts by default. Repository owners or people with admin access can enable Dependabot alerts.
  You can also enable or disable Dependabot alerts for all repositories owned by your user account or organization. For more information, see [Managing security and analysis features](/en/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-personal-account-settings/managing-security-and-analysis-settings-for-your-personal-account) or [Managing security and analysis settings for your organization](/en/organizations/keeping-your-organization-secure/managing-security-settings-for-your-organization/managing-security-and-analysis-settings-for-your-organization).
* **Artifact attestations:** Available in all public repositories, but you must explicitly generate attestations in your build workflows. See [Using artifact attestations to establish provenance for builds](/en/actions/how-tos/secure-your-work/use-artifact-attestations/use-artifact-attestations).

Private repositories:

* **Dependency graph:** Not enabled by default. The feature can be enabled by repository administrators. For more information, see [Exploring the dependencies of a repository](/en/code-security/supply-chain-security/understanding-your-software-supply-chain/exploring-the-dependencies-of-a-repository#enabling-and-disabling-the-dependency-graph).
* **Dependency review:** Available in private repositories owned by organizations that use GitHub Team or GitHub Enterprise Cloud and have a license for GitHub Code Security or GitHub Advanced Security. For more information, see [About GitHub Advanced Security](/en/get-started/learning-about-github/about-github-advanced-security) and [Exploring the dependencies of a repository](/en/code-security/supply-chain-security/understanding-your-software-supply-chain/exploring-the-dependencies-of-a-repository#enabling-and-disabling-the-dependency-graph).
* **Dependabot alerts:** Not enabled by default. Owners of private repositories, or people with admin access, can enable Dependabot alerts by enabling the dependency graph and Dependabot alerts for their repositories.
  You can also enable or disable Dependabot alerts for all repositories owned by your user account or organization. For more information, see [Managing security and analysis features](/en/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-personal-account-settings/managing-security-and-analysis-settings-for-your-personal-account) or [Managing security and analysis settings for your organization](/en/organizations/keeping-your-organization-secure/managing-security-settings-for-your-organization/managing-security-and-analysis-settings-for-your-organization).
* **Artifact attestations:** Only available in private repositories on GitHub Enterprise Cloud.

Any repository type:

* **Dependabot security updates:** Not enabled by default. You can enable Dependabot security updates for any repository that uses Dependabot alerts and the dependency graph. For information about enabling security updates, see [Configuring Dependabot security updates](/en/code-security/dependabot/dependabot-security-updates/configuring-dependabot-security-updates).
* **Dependabot version updates:** Not enabled by default. People with write permissions to a repository can enable Dependabot version updates. For information about enabling version updates, see [Configuring Dependabot version updates](/en/code-security/dependabot/dependabot-version-updates/configuring-dependabot-version-updates).
* **Immutable releases*:*\* Not enabled by default. You can enable release immutability for a repository or organization. See [Preventing changes to your releases](/en/code-security/how-tos/secure-your-supply-chain/establish-provenance-and-integrity/preventing-changes-to-your-releases).