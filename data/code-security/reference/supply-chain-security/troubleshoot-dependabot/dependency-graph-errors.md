# Troubleshooting the dependency graph

If the dependency information reported by the dependency graph is not what you expected, there are a number of points to consider, and various things you can check.

The results of dependency detection reported by GitHub may be different from the results returned by other tools. There are good reasons for this and it's helpful to understand how GitHub determines dependencies for your project.

## Does the dependency graph only find dependencies in manifests and lockfiles?

The dependency graph automatically includes information on dependencies that are explicitly declared in your environment. That is, dependencies that are specified in a manifest or a lockfile. The dependency graph generally also includes transitive dependencies, even when they aren't specified in a lockfile, by looking at the dependencies of the dependencies in a manifest file.

The dependency graph doesn't automatically include "loose" dependencies. "Loose" dependencies are individual files that are copied from another source and checked into the repository directly or within an archive (such as a ZIP or JAR file), rather than being referenced by in a package manager’s manifest or lockfile.

However, you can use the dependency submission API to add dependencies to a project's dependency graph, even if the dependencies are not declared in a manifest or lock file, such as dependencies resolved when a project is built. Dependencies submitted to a project using the dependency submission API will show which detector was used for their submission and when they were submitted. For more information on the dependency submission API, see [Using the dependency submission API](/en/code-security/supply-chain-security/understanding-your-software-supply-chain/using-the-dependency-submission-api).

**Check:** Is the missing dependency for a component that's not specified in the repository's manifest or lockfile?

## Does the dependency graph detect dependencies specified using variables?

The dependency graph analyzes manifests as they’re pushed to GitHub. The dependency graph doesn't, therefore, have access to the build environment of the project, so it can't resolve variables used within manifests. If you use variables within a manifest to specify the name, or more commonly the version of a dependency, then that dependency will not automatically be included in the dependency graph.

However, you can use the dependency submission API to add dependencies to a project's dependency graph, even if the dependencies are only resolved when a project is built. For more information on the dependency submission API, see [Using the dependency submission API](/en/code-security/supply-chain-security/understanding-your-software-supply-chain/using-the-dependency-submission-api).

**Check:** Is the missing dependency declared in the manifest by using a variable for its name or version?

## Are there limits which affect the dependency graph data?

Yes, the dependency graph has limits on the size, number, and location of manifest files that it will process.

The processing limits affect the dependency graph displayed within GitHub and also prevent Dependabot alerts being created.

Manifests over 10 MB in size are ignored and will not generate Dependabot alerts.

By default, GitHub will not process more than 150 manifests per repository. Dependabot doesn't generate Dependabot alerts for manifests beyond this limit, and Dependabot alerts may behave unpredictably if this limit is exceeded.

Manifest files stored in directories with names that are typically used for vendored dependencies will not be processed. A directory whose name matches the following regular expressions is considered a vendored dependencies directory:

  <!-- markdownlint-disable MD011 -->

* <code>(3rd|\[Tt]hird)\[-\_]?\[Pp]arty/</code>
* <code>(^|/)vendors?/</code>
* <code>(^|/)\[Ee]xtern(als?)?/</code>
* <code>(^|/)\[Vv]+endor/</code>

  <!-- markdownlint-enable MD011 -->

Examples:

* third-party/dependencies/dependency1
* vendors/dependency1
* /externals/vendor1/dependency1

## My dependencies don't look right, what can I do?

If the table of dependencies for your project doesn't accurately represent your repository's manifests, you can trigger a rebuild of its dependency graph.

From the repository's Dependabot tab, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="settings" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> at the top of the alert list. Select **Refresh Dependabot alerts** from the dropdown menu. This will enqueue a background task to process the repository's manifests, detect any new or changed dependencies, and update the alerts.

> \[!NOTE] You need to have permission to manage security alerts in order to refresh a repository's dependency graph. See [Managing security and analysis settings for your repository](/en/repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-security-and-analysis-settings-for-your-repository#granting-access-to-security-alerts) for information on configuring this access. To further reduce the potential for abuse, the **Refresh Dependabot alerts** option can only be triggered once an hour per repository.

Clicking **Refresh Dependabot alerts** will only scan manifest files. If your dependency graph also includes build-time dependency information submitted using the dependency submission API, rerunning the Action or external process which generates and submits the dependency information will also trigger a rebuild of the repository's dependency graph. For more information about the dependency submission API, see [Using the dependency submission API](/en/code-security/supply-chain-security/understanding-your-software-supply-chain/using-the-dependency-submission-api).

If you are using automatic dependency submission, pushing a commit that updates the repository's manifest file will trigger the automatic submission action to run.

In all cases, the timestamp at the top of the list of alerts indicates the last time the dependency graph was built.

## Further reading

* [Dependency graph](/en/code-security/supply-chain-security/understanding-your-software-supply-chain/about-the-dependency-graph)
* [Managing security and analysis settings for your repository](/en/repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-security-and-analysis-settings-for-your-repository)
* [Vulnerable dependency detection](/en/code-security/dependabot/troubleshooting-dependabot/troubleshooting-the-detection-of-vulnerable-dependencies)
* [Dependabot errors](/en/code-security/dependabot/troubleshooting-dependabot/troubleshooting-dependabot-errors)