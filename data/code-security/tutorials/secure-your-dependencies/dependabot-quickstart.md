# Dependabot quickstart guide

Find and fix vulnerable dependencies you rely on with Dependabot.

## About Dependabot

This quickstart guide walks you through setting up and enabling Dependabot, viewing Dependabot alerts, and updating your repository to use a secure version of the dependency.

Dependabot consists of three different features that help you manage your dependencies:

* Dependabot alerts: Inform you about vulnerabilities in the dependencies that you use in your repository.
* Dependabot security updates: Automatically raise pull requests to update the dependencies you use that have known security vulnerabilities.
* Dependabot version updates: Automatically raise pull requests to keep your dependencies up-to-date.

## Prerequisites

For the purpose of this guide, we're going to use a demo repository to illustrate how Dependabot finds vulnerabilities in dependencies, where you can see Dependabot alerts on GitHub, and how you can explore, fix, or dismiss these alerts.

You need to start by forking the demo repository.

1. Navigate to [https://github.com/dependabot/demo](https://github.com/dependabot/demo?ref_product=supply-chain-security\&ref_type=engagement\&ref_style=text).
2. At the top of the page, on the right, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-repo-forked" aria-label="repo-forked" role="img"><path d="M5 5.372v.878c0 .414.336.75.75.75h4.5a.75.75 0 0 0 .75-.75v-.878a2.25 2.25 0 1 1 1.5 0v.878a2.25 2.25 0 0 1-2.25 2.25h-1.5v2.128a2.251 2.251 0 1 1-1.5 0V8.5h-1.5A2.25 2.25 0 0 1 3.5 6.25v-.878a2.25 2.25 0 1 1 1.5 0ZM5 3.25a.75.75 0 1 0-1.5 0 .75.75 0 0 0 1.5 0Zm6.75.75a.75.75 0 1 0 0-1.5.75.75 0 0 0 0 1.5Zm-3 8.75a.75.75 0 1 0-1.5 0 .75.75 0 0 0 1.5 0Z"></path></svg> Fork**.
3. Select an owner (you can select your GitHub personal account) and type a repository name. For more information about forking repositories, see [Fork a repository](/en/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo#forking-a-repository).
4. Click **Create fork**.

## Enabling Dependabot for your repository

You need to follow the steps below on the repository you forked in [Prerequisites](#prerequisites).

1. On GitHub, navigate to the main page of the repository.
2. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> Settings**. If you cannot see the "Settings" tab, select the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="More" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>** dropdown menu, then click **Settings**.

   ![Screenshot of a repository header showing the tabs. The "Settings" tab is highlighted by a dark orange outline.](/assets/images/help/repository/repo-actions-settings.png)
3. In the "Security" section of the sidebar, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-codescan" aria-label="codescan" role="img"><path d="M8.47 4.97a.75.75 0 0 0 0 1.06L9.94 7.5 8.47 8.97a.75.75 0 1 0 1.06 1.06l2-2a.75.75 0 0 0 0-1.06l-2-2a.75.75 0 0 0-1.06 0ZM6.53 6.03a.75.75 0 0 0-1.06-1.06l-2 2a.75.75 0 0 0 0 1.06l2 2a.75.75 0 1 0 1.06-1.06L5.06 7.5l1.47-1.47Z"></path><path d="M12.246 13.307a7.501 7.501 0 1 1 1.06-1.06l2.474 2.473a.749.749 0 0 1-.326 1.275.749.749 0 0 1-.734-.215ZM1.5 7.5a6.002 6.002 0 0 0 3.608 5.504 6.002 6.002 0 0 0 6.486-1.117.748.748 0 0 1 .292-.293A6 6 0 1 0 1.5 7.5Z"></path></svg> Advanced Security**.
4. Under "Dependabot", click **Enable** for Dependabot alerts, Dependabot security updates, and Dependabot version updates.
5. If you clicked **Enable** for Dependabot version updates, you can edit the default `dependabot.yml` configuration file that GitHub creates for you in the `/.github` directory of your repository.
   To enable Dependabot version updates for your repository, you typically configure this file to suit your needs by editing the default file, and committing your changes. You can refer to the snippet provided in [Configuring Dependabot version updates](/en/code-security/dependabot/dependabot-version-updates/configuring-dependabot-version-updates#example-dependabotyml-file) for an example.

> \[!NOTE]
> If the dependency graph is not already enabled for the repository, GitHub will enable it automatically when you enable Dependabot.

For more information about configuring each of these Dependabot features, see [Configuring Dependabot alerts](/en/code-security/dependabot/dependabot-alerts/configuring-dependabot-alerts), [Configuring Dependabot security updates](/en/code-security/dependabot/dependabot-security-updates/configuring-dependabot-security-updates), and [Configuring Dependabot version updates](/en/code-security/dependabot/dependabot-version-updates/configuring-dependabot-version-updates).

## Viewing Dependabot alerts for your repository

If Dependabot alerts are enabled for a repository, you can view Dependabot alerts on the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab for the repository. You can use the forked repository that you enabled Dependabot alerts on in the previous section.

1. On GitHub, navigate to the main page of the repository.

2. Under the repository name, click the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab. If you cannot see the "<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality" tab, select the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="kebab-horizontal" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>** dropdown menu, and then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality**.

3. In the "Findings" section of the sidebar, select the <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-dependabot" aria-label="dependabot" role="img"><path d="M5.75 7.5a.75.75 0 0 1 .75.75v1.5a.75.75 0 0 1-1.5 0v-1.5a.75.75 0 0 1 .75-.75Zm5.25.75a.75.75 0 0 0-1.5 0v1.5a.75.75 0 0 0 1.5 0v-1.5Z"></path><path d="M6.25 0h2A.75.75 0 0 1 9 .75V3.5h3.25a2.25 2.25 0 0 1 2.25 2.25V8h.75a.75.75 0 0 1 0 1.5h-.75v2.75a2.25 2.25 0 0 1-2.25 2.25h-8.5a2.25 2.25 0 0 1-2.25-2.25V9.5H.75a.75.75 0 0 1 0-1.5h.75V5.75A2.25 2.25 0 0 1 3.75 3.5H7.5v-2H6.25a.75.75 0 0 1 0-1.5ZM3 5.75v6.5c0 .414.336.75.75.75h8.5a.75.75 0 0 0 .75-.75v-6.5a.75.75 0 0 0-.75-.75h-8.5a.75.75 0 0 0-.75.75Z"></path></svg> **Dependabot** <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-chevron-down" aria-label="chevron-down" role="img"><path d="M12.78 5.22a.749.749 0 0 1 0 1.06l-4.25 4.25a.749.749 0 0 1-1.06 0L3.22 6.28a.749.749 0 1 1 1.06-1.06L8 8.939l3.72-3.719a.749.749 0 0 1 1.06 0Z"></path></svg> dropdown menu, then click **Vulnerabilities**.

4. Review the open alerts on the Dependabot alerts page. By default, the page displays the **Open** tab, listing the open alerts. (You'll be able to view any closed alerts by clicking **Closed**.)

   ![Screenshot showing the list of Dependabot alerts for the demo repository.](/assets/images/help/repository/dependabot-alerts-list-demo-repo.png)

   You can filter Dependabot alerts in the list, using a variety of filters or labels. For more information, see [Viewing and updating Dependabot alerts](/en/code-security/dependabot/dependabot-alerts/viewing-and-updating-dependabot-alerts#prioritizing-dependabot-alerts). You can also use Dependabot auto-triage rules to filter out false positive alerts or alerts you're not interested in. For more information, see [Dependabot auto-triage rules](/en/code-security/dependabot/dependabot-auto-triage-rules/about-dependabot-auto-triage-rules).

5. Click the "Command Injection in lodash" alert on the `javascript/package-lock.json` file. The details page for the alert will show the following information (note that some information may not apply to all alerts):

   * Whether Dependabot created a pull request that will fix the vulnerability. You can review the suggested security update by clicking **Review security update**.
   * Package involved
   * Affected versions
   * Patched version
   * Brief description of the vulnerability

   ![Screenshot of the detailed page of an alert in the demo repository, showing the main information.](/assets/images/help/repository/alert-details-page-demo-repo.png)

6. Optionally, you can also explore the information on the right-side of the page. Some of the information shown in the screenshot may not apply to every alert.

   * Severity
   * CVSS metrics: We use CVSS levels to assign severity levels. For more information, see [GitHub Advisory database](/en/code-security/security-advisories/working-with-global-security-advisories-from-the-github-advisory-database/about-the-github-advisory-database#about-cvss-levels).
   * Tags
   * Weaknesses: List of CWEs related to the vulnerability, if applicable
   * CVE ID: Unique CVE identifier for the vulnerability, if applicable
   * GHSA ID: Unique identifier of the corresponding advisory on the GitHub Advisory Database. For more information, see [GitHub Advisory database](/en/code-security/security-advisories/working-with-global-security-advisories-from-the-github-advisory-database/about-the-github-advisory-database#about-ghsa-ids).
   * Option to navigate to the advisory on the GitHub Advisory Database
   * Option to see all of your repositories that are affected by this vulnerability
   * Option to suggest improvements for this advisory on the GitHub Advisory Database

   ![Screenshot of the detailed page of an alert in the demo repository, showing the information displayed on the right-side of the page.](/assets/images/help/repository/more-alert-details-demo-repo.png)

For more information about viewing, prioritizing, and sorting Dependabot alerts, see [Viewing and updating Dependabot alerts](/en/code-security/dependabot/dependabot-alerts/viewing-and-updating-dependabot-alerts).

## Fixing or dismissing a Dependabot alert

You can fix or dismiss Dependabot alerts on GitHub. Let's continue to use the forked repository as an example, and the "Command Injection in lodash" alert described in the previous section.

1. Navigate to the Dependabot tab for the repository. For more information, see the [Viewing Dependabot alerts for your repository](#viewing-dependabot-alerts-for-your-repository) section above.
2. Click an alert.
3. Click the "Command Injection in lodash" alert on the `javascript/package-lock.json` file.
4. Review the alert. You can:
   * Review the suggested security update by clicking **Review security update**. This will open the pull request generated by Dependabot with the security fix.

     ![Screenshot of the pull request generated by Dependabot to fix the security vulnerability highlighted by the selected alert.](/assets/images/help/repository/dependabot-pull-request-demo-repo.png)

     * On the pull request description, you can click **Commits** to explore the commits included in the pull request.
     * You can also click **Dependabot commands and options** to learn about the commands that you can use to interact with the pull request.
     * When you're ready to update your dependency and resolve the vulnerability, merge the pull request.
   * If you decide that you want to dismiss the alert
     * Go back to the alert details page.

     * On the top-right corner, click **Dismiss alert**.

       ![Screenshot of the alert details page with the Dismiss alert button, dropdown menu options, and dismissal comment box outlined in orange.](/assets/images/help/repository/dismiss-alert-demo-repo.png)

     * Select a reason for dismissing the alert.

     * Optionally, add a dismissal comment. The dismissal comment will be added to the alert timeline and can be used as justification during auditing and reporting.

     * Click **Dismiss alert**. The alert won't appear anymore in the **Open** tab of the alert list, and you are able to view it in the **Closed** tab.

For more information about reviewing and updating Dependabot alerts, see [Viewing and updating Dependabot alerts](/en/code-security/dependabot/dependabot-alerts/viewing-and-updating-dependabot-alerts#reviewing-and-fixing-alerts).

## Troubleshooting

You may need to do some troubleshooting if:

* Dependabot is blocked from creating a pull request to fix an alert, or
* The information reported by Dependabot is not what you expect.

For more information, see [Dependabot errors](/en/code-security/dependabot/troubleshooting-dependabot/troubleshooting-dependabot-errors) and [Vulnerable dependency detection](/en/code-security/dependabot/troubleshooting-dependabot/troubleshooting-the-detection-of-vulnerable-dependencies), respectively.

## Next steps

For more information about configuring Dependabot updates, see [Configuring Dependabot security updates](/en/code-security/dependabot/dependabot-security-updates/configuring-dependabot-security-updates) and [Configuring Dependabot version updates](/en/code-security/dependabot/dependabot-version-updates/configuring-dependabot-version-updates).

For more information about configuring Dependabot for an organization, see [Configuring Dependabot alerts](/en/code-security/dependabot/dependabot-alerts/configuring-dependabot-alerts#managing-dependabot-alerts-for-your-organization).

For more information about viewing pull requests opened by Dependabot, see [Managing pull requests for dependency updates](/en/code-security/dependabot/working-with-dependabot/managing-pull-requests-for-dependency-updates#viewing-dependabot-pull-requests).

For more information about the security advisories that contribute to Dependabot alerts, see [Browsing security advisories in the GitHub Advisory Database](/en/code-security/security-advisories/working-with-global-security-advisories-from-the-github-advisory-database/browsing-security-advisories-in-the-github-advisory-database).

For more information about configuring notifications about Dependabot alerts, see [Configuring notifications for Dependabot alerts](/en/code-security/dependabot/dependabot-alerts/configuring-notifications-for-dependabot-alerts).