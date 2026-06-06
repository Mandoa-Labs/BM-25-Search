# Configuring default setup for code scanning

Quickly set up code scanning to find vulnerable code automatically.

We recommend that you start using code scanning with default setup. After you've initially configured default setup, you can evaluate code scanning to see how it's working for you and customize it to better meet your needs. For more information, see [About setup types for code scanning](/en/code-security/concepts/code-scanning/setup-types).

## Prerequisites

Your repository is eligible for default setup for code scanning if:

* GitHub Actions is enabled.
* It is publicly visible, or GitHub Code Security is enabled.

## Configuring default setup for a repository

> \[!NOTE]
> If the analyses fail for all CodeQL-supported languages in a repository, default setup will still be enabled, but it will not run any scans or use any GitHub Actions minutes until another CodeQL-supported language is added to the repository or default setup is manually reconfigured, and the analysis of a CodeQL-supported language succeeds.

1. On GitHub, navigate to the main page of the repository.

   > \[!NOTE]
   > If you are configuring default setup on a fork, you must first enable GitHub Actions. To enable GitHub Actions, under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-play" aria-label="play" role="img"><path d="M8 0a8 8 0 1 1 0 16A8 8 0 0 1 8 0ZM1.5 8a6.5 6.5 0 1 0 13 0 6.5 6.5 0 0 0-13 0Zm4.879-2.773 4.264 2.559a.25.25 0 0 1 0 .428l-4.264 2.559A.25.25 0 0 1 6 10.559V5.442a.25.25 0 0 1 .379-.215Z"></path></svg> Actions**, then click **I understand my workflows, go ahead and enable them**. Be aware that this will enable all existing workflows on your fork.

2. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> Settings**. If you cannot see the "Settings" tab, select the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="More" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>** dropdown menu, then click **Settings**.

   ![Screenshot of a repository header showing the tabs. The "Settings" tab is highlighted by a dark orange outline.](/assets/images/help/repository/repo-actions-settings.png)

3. In the "Security" section of the sidebar, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-codescan" aria-label="codescan" role="img"><path d="M8.47 4.97a.75.75 0 0 0 0 1.06L9.94 7.5 8.47 8.97a.75.75 0 1 0 1.06 1.06l2-2a.75.75 0 0 0 0-1.06l-2-2a.75.75 0 0 0-1.06 0ZM6.53 6.03a.75.75 0 0 0-1.06-1.06l-2 2a.75.75 0 0 0 0 1.06l2 2a.75.75 0 1 0 1.06-1.06L5.06 7.5l1.47-1.47Z"></path><path d="M12.246 13.307a7.501 7.501 0 1 1 1.06-1.06l2.474 2.473a.749.749 0 0 1-.326 1.275.749.749 0 0 1-.734-.215ZM1.5 7.5a6.002 6.002 0 0 0 3.608 5.504 6.002 6.002 0 0 0 6.486-1.117.748.748 0 0 1 .292-.293A6 6 0 1 0 1.5 7.5Z"></path></svg> Advanced Security**.

4. Under "Code Security", to the right of "CodeQL analysis", select **Set up** <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-triangle-down" aria-label="triangle-down" role="img"><path d="m4.427 7.427 3.396 3.396a.25.25 0 0 0 .354 0l3.396-3.396A.25.25 0 0 0 11.396 7H4.604a.25.25 0 0 0-.177.427Z"></path></svg>, then click **Default**.

   ![Screenshot of the "Code scanning" section of "Advanced Security" settings. The "Default setup" button is highlighted with an orange outline.](/assets/images/help/security/default-code-scanning-setup-ghas.png)

   You will then see a "CodeQL default configuration" dialog summarizing the code scanning configuration automatically created by default setup.

5. Optionally, to customize your code scanning setup, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-pencil" aria-label="pencil" role="img"><path d="M11.013 1.427a1.75 1.75 0 0 1 2.474 0l1.086 1.086a1.75 1.75 0 0 1 0 2.474l-8.61 8.61c-.21.21-.47.364-.756.445l-3.251.93a.75.75 0 0 1-.927-.928l.929-3.25c.081-.286.235-.547.445-.758l8.61-8.61Zm.176 4.823L9.75 4.81l-6.286 6.287a.253.253 0 0 0-.064.108l-.558 1.953 1.953-.558a.253.253 0 0 0 .108-.064Zm1.238-3.763a.25.25 0 0 0-.354 0L10.811 3.75l1.439 1.44 1.263-1.263a.25.25 0 0 0 0-.354Z"></path></svg> Edit**.
   * To add or remove a language from the analysis performed by default setup, select or deselect that language in the "Languages" section.
   * To specify the CodeQL query suite you would like to use, select your preferred query suite in the "Query suites" section.

6. Review the settings for default setup on your repository, then click **Enable CodeQL**. This will trigger a workflow that tests the new, automatically generated configuration.

   > \[!NOTE]
   > If you are switching to default setup from advanced setup, you will see a warning informing you that default setup will override existing code scanning configurations. This warning means default setup will disable the existing workflow file and block any CodeQL analysis API uploads.

7. If projects in your repository depend on dependencies in private package registries, you can grant code scanning access to them. This can improve the outcomes and quality of analyses. See [Giving security features access to private registries](/en/code-security/how-tos/secure-at-scale/configure-organization-security/manage-usage-and-access/giving-org-access-private-registries).

8. Optionally, adjust other configuration options which affect default setup. See [Repository properties for code scanning](/en/code-security/concepts/code-scanning/repository-properties).

9. Optionally, to view your default setup configuration after enablement, select <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="Menu" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>, then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> View CodeQL configuration**.

> \[!NOTE]
> If no pushes and pull requests have occurred in a repository with default setup enabled for 6 months, the weekly schedule will be disabled to save your GitHub Actions minutes.

## Running default setup on self-hosted or larger runners

You can use default setup for all CodeQL-supported languages on self-hosted runners or GitHub-hosted runners.

> \[!NOTE]Code scanning sees assigned runners when default setup is enabled. If a runner is assigned to a repository that is already running default setup, you must disable and re-enable default setup to start using the runner. If you add a runner and want to start using it, you can change the configuration manually without needing to disable and re-enable default setup.

### Assigning labels to self-hosted runners

To assign a self-hosted runner for default setup, you can use the default `code-scanning` label, or you can optionally give them custom labels so that individual repositories can use different runners. For information about assigning labels to self-hosted runners, see [Using labels with self-hosted runners](/en/actions/hosting-your-own-runners/managing-self-hosted-runners/using-labels-with-self-hosted-runners).

Once you've assigned custom labels to self-hosted runners, your repositories can use those runners for code scanning default setup.

You can also use security configurations to assign labels to self-hosted runners for code scanning. See [Creating a custom security configuration](/en/code-security/securing-your-organization/meeting-your-specific-security-needs-with-custom-security-configurations/creating-a-custom-security-configuration#creating-a-custom-security-configuration).

### Assigning larger runners

To assign a larger runner, name the runner `code-scanning`. This will automatically add the `code-scanning` label to the larger runner. An organization can only have one larger runner with the `code-scanning` label, and that runner will handle all code scanning jobs from repositories within your organization with access to the runner's group. See [Configuring larger runners for default setup](/en/code-security/code-scanning/managing-your-code-scanning-configuration/configuring-larger-runners-for-default-setup#provisioning-organization-level-larger-runners-for-default-setup).

### Ensuring build support

Default setup uses the `none` build mode for C/C++, C#, Java and Rust and uses the `autobuild` build mode for other compiled languages. You should configure your self-hosted runners to make sure they can run all the necessary commands for C/C++, C#, and Swift analysis. Analysis of JavaScript/TypeScript, Go, Ruby, Python, and Kotlin code does not currently require special configuration.

## Next steps

After your configuration runs successfully at least once, you can start examining and resolving code scanning alerts. For more information on code scanning alerts, see [Code scanning alerts](/en/code-security/code-scanning/managing-code-scanning-alerts/about-code-scanning-alerts) and [Assessing code scanning alerts for your repository](/en/code-security/code-scanning/managing-code-scanning-alerts/assessing-code-scanning-alerts-for-your-repository).

After you've configured default setup for code scanning, you can read about evaluating how it's working for you and the next steps you can take to customize it. For more information, see [Evaluating default setup for code scanning](/en/code-security/code-scanning/enabling-code-scanning/evaluating-default-setup-for-code-scanning).

You can find detailed information about your code scanning configuration, including timestamps for each scan and the percentage of files scanned, on the tool status page. For more information, see [Use the tool status page for code scanning](/en/code-security/code-scanning/managing-your-code-scanning-configuration/about-the-tool-status-page).

When you configure default setup, you may encounter an error. For information on troubleshooting specific errors, see [Troubleshooting code scanning analysis errors](/en/code-security/code-scanning/troubleshooting-code-scanning).