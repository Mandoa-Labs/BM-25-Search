# Configuring global security settings for your organization

Customize Advanced Security features for your organization by defining global settings that ensure consistent security standards and safeguard all your repositories.

## Accessing the global settings page for your organization

1. In the upper-right corner of GitHub, click your profile picture, then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-organization" aria-label="organization" role="img"><path d="M1.75 16A1.75 1.75 0 0 1 0 14.25V1.75C0 .784.784 0 1.75 0h8.5C11.216 0 12 .784 12 1.75v12.5c0 .085-.006.168-.018.25h2.268a.25.25 0 0 0 .25-.25V8.285a.25.25 0 0 0-.111-.208l-1.055-.703a.749.749 0 1 1 .832-1.248l1.055.703c.487.325.779.871.779 1.456v5.965A1.75 1.75 0 0 1 14.25 16h-3.5a.766.766 0 0 1-.197-.026c-.099.017-.2.026-.303.026h-3a.75.75 0 0 1-.75-.75V14h-1v1.25a.75.75 0 0 1-.75.75Zm-.25-1.75c0 .138.112.25.25.25H4v-1.25a.75.75 0 0 1 .75-.75h2.5a.75.75 0 0 1 .75.75v1.25h2.25a.25.25 0 0 0 .25-.25V1.75a.25.25 0 0 0-.25-.25h-8.5a.25.25 0 0 0-.25.25ZM3.75 6h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5ZM3 3.75A.75.75 0 0 1 3.75 3h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 3 3.75Zm4 3A.75.75 0 0 1 7.75 6h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 7 6.75ZM7.75 3h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5ZM3 9.75A.75.75 0 0 1 3.75 9h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 3 9.75ZM7.75 9h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5Z"></path></svg> Organizations**.
2. Under your organization name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> Settings**. If you cannot see the "Settings" tab, select the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="More" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>** dropdown menu, then click **Settings**.

   ![Screenshot of the tabs in an organization's profile. The "Settings" tab is outlined in dark orange.](/assets/images/help/discussions/org-settings-global-nav-update.png)
3. In the "Security" section of the sidebar, select the **Advanced Security** dropdown menu, then click **Global settings**.

## Configuring global Dependabot settings

You can customize several global settings for Dependabot:

* [Creating and managing Dependabot auto-triage rules](#creating-and-managing-dependabot-auto-triage-rules)
* [Grouping Dependabot security updates](#grouping-dependabot-security-updates)
* [Enabling dependency updates on GitHub Actions runners](#enabling-dependency-updates-on-github-actions-runners)
* [Configuring the runner type for Dependabot](#configuring-the-runner-type-for-dependabot)
* [Granting Dependabot access to private repositories](#granting-dependabot-access-to-private-repositories)

### Creating and managing Dependabot auto-triage rules

You can create and manage Dependabot auto-triage rules to instruct Dependabot to automatically dismiss or snooze Dependabot alerts, and even open pull requests to attempt to resolve them. To configure Dependabot auto-triage rules, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="Configure Dependabot rules" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg>, then create or edit a rule:

* You can create a new rule by clicking **New rule**, then entering the details for your rule and clicking **Create rule**.
* You can edit an existing rule by clicking <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-pencil" aria-label="Edit CURATED-OR-CUSTOM rule" role="img"><path d="M11.013 1.427a1.75 1.75 0 0 1 2.474 0l1.086 1.086a1.75 1.75 0 0 1 0 2.474l-8.61 8.61c-.21.21-.47.364-.756.445l-3.251.93a.75.75 0 0 1-.927-.928l.929-3.25c.081-.286.235-.547.445-.758l8.61-8.61Zm.176 4.823L9.75 4.81l-6.286 6.287a.253.253 0 0 0-.064.108l-.558 1.953 1.953-.558a.253.253 0 0 0 .108-.064Zm1.238-3.763a.25.25 0 0 0-.354 0L10.811 3.75l1.439 1.44 1.263-1.263a.25.25 0 0 0 0-.354Z"></path></svg>, then making the desired changes and clicking **Save rule**.

For more information on Dependabot auto-triage rules, see [Dependabot auto-triage rules](/en/code-security/concepts/supply-chain-security/about-dependabot-auto-triage-rules) and [Customizing auto-triage rules to prioritize Dependabot alerts](/en/code-security/how-tos/secure-your-supply-chain/manage-your-dependency-security/customizing-auto-triage-rules-to-prioritize-dependabot-alerts#adding-custom-auto-triage-rules-to-your-organization).

### Grouping Dependabot security updates

Dependabot can group all automatically suggested security updates into a single pull request. To enable grouped security updates, select **Grouped security updates**. For more information about grouped updates and customization options, see [Configuring Dependabot security updates](/en/code-security/how-tos/secure-your-supply-chain/secure-your-dependencies/configuring-dependabot-security-updates#grouping-dependabot-security-updates-into-a-single-pull-request).

### Enabling dependency updates on GitHub Actions runners

If both Dependabot and GitHub Actions are enabled for existing repositories in your organization, GitHub will automatically use GitHub-hosted runners to run dependency updates for those repositories.

Otherwise, to allow Dependabot to use GitHub Actions runners to perform dependency updates for all existing repositories in the organization, select "Dependabot on Actions runners".

For more information, see [Dependabot on GitHub Actions runners](/en/code-security/dependabot/working-with-dependabot/about-dependabot-on-github-actions-runners).

### Configuring the runner type for Dependabot

You can configure which type of runner Dependabot uses to scan for version and security updates. By default, Dependabot uses standard **GitHub-hosted runners**. You can configure Dependabot to use **self-hosted runners** with custom labels, which allows you to integrate with existing runner infrastructure such as Actions Runner Controller (ARC).

> \[!NOTE]
>
> * For security reasons, Dependabot uses GitHub-hosted runners for public repositories, even when you configure labeled runners.
> * Labeled runners **do not work** for public repositories.

To configure the runner type:

1. Under "Dependabot", next to "Runner type", select <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-pencil" aria-label="Edit runner type" role="img"><path d="M11.013 1.427a1.75 1.75 0 0 1 2.474 0l1.086 1.086a1.75 1.75 0 0 1 0 2.474l-8.61 8.61c-.21.21-.47.364-.756.445l-3.251.93a.75.75 0 0 1-.927-.928l.929-3.25c.081-.286.235-.547.445-.758l8.61-8.61Zm.176 4.823L9.75 4.81l-6.286 6.287a.253.253 0 0 0-.064.108l-.558 1.953 1.953-.558a.253.253 0 0 0 .108-.064Zm1.238-3.763a.25.25 0 0 0-.354 0L10.811 3.75l1.439 1.44 1.263-1.263a.25.25 0 0 0 0-.354Z"></path></svg>.
2. In the "Edit runner type for Dependabot" dialog, select the runner type you want Dependabot to use:
   * **Standard GitHub runner**.
   * **Labeled runner**: If you select this option, Dependabot will use self-hosted runners that match the label you specify.
3. If you selected **Labeled runner**:
   * In "Runner label", enter the label assigned to your self-hosted runners. Dependabot will use runners with this label. By default, the `dependabot` label is used, but you can specify a custom label to match your existing runner infrastructure.
   * Optionally, in "Runner group name", enter the name of a runner group if you want to target a specific group of runners.
4. Click **Save runner selection**.

For more information about configuring self-hosted runners for Dependabot, see [Configuring Dependabot on self-hosted runners](/en/code-security/dependabot/maintain-dependencies/managing-dependabot-on-self-hosted-runners).

### Granting Dependabot access to private repositories

To update private dependencies of repositories in your organization, Dependabot needs access to those repositories. To grant Dependabot access to the desired private repository, scroll down to the "Grant Dependabot access to private repositories" section, then use the search bar to find and select the desired repository. Be aware that granting Dependabot access to a repository means all users in your organization will have access to the contents of that repository through Dependabot updates. For more information about the supported ecosystems for private repositories, see [Dependabot supported ecosystems and repositories](/en/code-security/reference/supply-chain-security/supported-ecosystems-and-repositories).

## Configuring global code scanning settings

Code scanning is a feature that you use to analyze the code in a GitHub repository to find security vulnerabilities and coding errors. Any problems identified by the analysis are shown in your repository.

You can customize several global settings for code scanning:

* [Enabling Copilot Autofix for CodeQL](#enabling-copilot-autofix-for-codeql)
* [Recommending the extended query suite for default setup](#recommending-the-extended-query-suite-for-default-setup)
* [Expanding CodeQL analysis](#expanding-codeql-analysis)

### Recommending the extended query suite for default setup

Code scanning offers specific groups of CodeQL queries, called CodeQL query suites, to run against your code. By default, the "Default" query suite is run. GitHub also offers the "Extended" query suite, which contains all the queries in the "Default" query suite, plus additional queries with lower precision and severity. To suggest the "Extended" query suite across your organization, select **Recommend the extended query suite for repositories enabling default setup**. For more information on built-in query suites for CodeQL default setup, see [CodeQL query suites](/en/code-security/concepts/code-scanning/codeql/codeql-query-suites).

### Enabling Copilot Autofix for CodeQL

You can select **Copilot Autofix** to enable Copilot Autofix for all the repositories in your organization that use CodeQL default setup or CodeQL advanced setup. Copilot Autofix is an expansion of code scanning that suggests fixes for code scanning alerts. For more information, see [Application card: GitHub security and quality AI features](/en/code-security/code-scanning/managing-code-scanning-alerts/responsible-use-autofix-code-scanning).

### Expanding CodeQL analysis

You can expand CodeQL analysis coverage for all repositories in your organization that use default setup by configuring CodeQL model packs. Model packs extend the CodeQL analysis to recognize additional frameworks and libraries that are not included in the standard CodeQL libraries. This global configuration applies to repositories using default setup and allows you to specify model packs published via the container registry. For more information, see [Editing your configuration of default setup](/en/code-security/how-tos/scan-code-for-vulnerabilities/manage-your-configuration/editing-your-configuration-of-default-setup#extending-coverage-for-all-repositories-in-an-organization).

## Configuring global secret scanning settings

Secret scanning is a security tool that scans the entire Git history of repositories, as well as issues, pull requests, discussions, and wikis in those repositories, for leaked secrets that have been accidentally committed, such as tokens or private keys.

You can customize several global settings for secret scanning:

* [Adding a resource link for blocked commits](#adding-a-resource-link-for-blocked-commits)
* [Defining custom patterns](#defining-custom-patterns)
* [Specifying patterns to include in push protection](#specifying-patterns-to-include-in-push-protection)

### Adding a resource link for blocked commits

To provide context for developers when secret scanning blocks a commit, you can display a link with more information on why the commit was blocked. To include a link, select **Add a resource link in the CLI and the web UI when a commit is blocked**. In the text box, type the link to the desired resource, then click **Save Link**.

### Defining custom patterns

You can define custom patterns for secret scanning with regular expressions. Custom patterns can identify secrets that are not detected by the default patterns supported by secret scanning. To create a custom pattern, click **New pattern**, then enter the details for your pattern and click **Save and dry run**. For more information on custom patterns, see [Defining custom patterns for secret scanning](/en/code-security/how-tos/secure-your-secrets/customize-leak-detection/defining-custom-patterns-for-secret-scanning).

### Specifying patterns to include in push protection

> \[!NOTE]
> The configuration of patterns for push protection at enterprise and organization level is currently in public preview and subject to change.

You can customize which secret patterns are included in push protection, giving security teams greater control over what types of secrets are blocked in the repositories in your organization.

1. Under "Additional settings", in the "Secret scanning" section and to the right of "Pattern configurations", click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="The Gear icon" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg>**.
2. In the page that gets displayed, make the desired changes in the "Organization setting" column.

You can enable or disable push protection for individual patterns by using the toggle in the relevant column: "Enterprise setting" at the enterprise level, and "Organization setting" at the organization level.

The data is limited to the scope, therefore the alert volume, false positives, bypass rate, or availability of custom patterns is reflective of user / alert activity within the *enterprise* or *organization*.

The GitHub default may change over time as we increase precision and promote patterns.

> \[!NOTE] Organization administrators and security teams can override settings configured at the enterprise level.

For more information on how to read data on the secret scanning pattern configuration page, see [Secret scanning pattern configuration data](/en/code-security/reference/secret-security/secret-scanning-pattern-configuration-data).

## Creating security managers for your organization

The security manager role grants members of your organization the ability to manage security settings and alerts across your organization. Security managers can view data for all repositories in your organization through security overview.

To learn more about the security manager role, see [Managing security managers in your organization](/en/organizations/managing-peoples-access-to-your-organization-with-roles/managing-security-managers-in-your-organization).

To assign the security manager role, see [Using organization roles](/en/organizations/managing-peoples-access-to-your-organization-with-roles/using-organization-roles#assigning-an-organization-role).