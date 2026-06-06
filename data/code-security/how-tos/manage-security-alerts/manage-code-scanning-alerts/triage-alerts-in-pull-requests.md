# Triaging code scanning alerts in pull requests

When code scanning identifies a problem in a pull request, you can review the highlighted code and resolve the alert.

Depending on your configuration, code scanning results may appear as check results and annotations on pull requests. For more information, see [Code scanning alerts](/en/code-security/concepts/code-scanning/about-code-scanning-alerts#about-alerts-in-pull-requests).

## Viewing results of the code scanning check

For all configurations of code scanning, the check that contains the results of code scanning is: **Code scanning results**. The results for each analysis tool used are shown separately. Any new alerts on lines of code changed in the pull request are shown as annotations.

To see the full set of alerts for the analyzed branch, click **View all branch alerts**. This opens the full alert view where you can filter all the alerts on the branch by type, severity, tag, etc. For more information, see [Assessing code scanning alerts for your repository](/en/code-security/code-scanning/managing-code-scanning-alerts/assessing-code-scanning-alerts-for-your-repository#filtering-and-searching-for-code-scanning-alerts).

![Screenshot of the Code scanning results check on a pull request. The "View all branch alerts" link is highlighted with a dark orange outline.](/assets/images/help/repository/code-scanning-results-check.png)

## Managing severity levels for check failures

If the code scanning results check finds any problems with a severity of `error`, `critical`, or `high`, the check fails and the error is reported in the check results. If all the results found by code scanning have lower severities, the alerts are treated as warnings or notes and the check succeeds.

![Screenshot of the merge box for a pull request. The "Code scanning results / CodeQL" check has "1 new alert including 1 high severity security v..."](/assets/images/help/repository/code-scanning-check-failure.png)

You can override the default behavior in your repository settings, by specifying the level of severities and security severities that will cause a pull request check failure. For more information, see [Workflow configuration options for code scanning](/en/code-security/code-scanning/creating-an-advanced-setup-for-code-scanning/customizing-your-advanced-setup-for-code-scanning#defining-the-severities-causing-pull-request-check-failure).

## Diagnosing issues with your code scanning configuration

Depending on your configuration, you may see additional checks running on pull requests with code scanning configured. These are usually workflows that analyze the code or that upload code scanning results. These checks are useful for troubleshooting when there are problems with the analysis.

For example, if the repository uses the CodeQL analysis workflow a **CodeQL / Analyze (LANGUAGE)** check is run for each language before the results check runs. The analysis check may fail if there are configuration problems, or if the pull request breaks the build for a language that the analysis compiles (for example, C/C++, C#, Go, Java, Kotlin, Rust, and Swift).

As with other pull request checks, you can see full details of the check failure on the **Checks** tab. For more information about configuring and troubleshooting, see [Workflow configuration options for code scanning](/en/code-security/code-scanning/creating-an-advanced-setup-for-code-scanning/customizing-your-advanced-setup-for-code-scanning) or [Troubleshooting code scanning analysis errors](/en/code-security/code-scanning/troubleshooting-code-scanning).

## Viewing an alert on your pull request

You can see any code scanning alerts that are inside the diff of the changes introduced in a pull request by viewing the **Conversation** tab. Code scanning posts a pull request review that shows each alert as an annotation on the lines of code that triggered the alert. You can comment on the alerts, dismiss the alerts, and view paths for the alerts, directly from the annotations. You can view the full details of an alert by clicking the "Show more details" link, which will take you to the alert details page.

![Screenshot of an alert annotation on the "Conversations" tab of a pull request. The "Show more details" link is outlined in dark orange.](/assets/images/help/repository/code-scanning-pr-conversation-tab.png)

You can also view all code scanning alerts that are inside the diff of the changes introduced in the pull request in the **Files changed** tab.

If you add a new code scanning configuration in your pull request, you will see a comment on your pull request directing you to the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab of the repository so you can view all the alerts on the pull request branch. For more information about viewing the alerts for a repository, see [Assessing code scanning alerts for your repository](/en/code-security/code-scanning/managing-code-scanning-alerts/assessing-code-scanning-alerts-for-your-repository#viewing-the-alerts-for-a-repository).

If you have write permission for the repository, some annotations contain links with extra context for the alert. In the example above, from CodeQL analysis, you can click **user-provided value** to see where the untrusted data enters the data flow (this is referred to as the source). In this case you can also view the full path from the source to the code that uses the data (the sink) by clicking **Show paths**. This makes it easy to check whether the data is untrusted or if the analysis failed to recognize a data sanitization step between the source and the sink. For information about analyzing data flow using CodeQL, see [About data flow analysis](https://codeql.github.com/docs/writing-codeql-queries/about-data-flow-analysis/).

To see more information about an alert, users with write permission can click the **Show more details** link shown in the annotation. This allows you to see all of the context and metadata provided by the tool in an alert view. In the example below, you can see tags showing the severity, type, and relevant common weakness enumerations (CWEs) for the problem. The view also shows which commit introduced the problem.

The status and details on the alert page only reflect the state of the alert on the default branch of the repository, even if the alert exists in other branches. You can see the status of the alert on non-default branches in the **Affected branches** section on the right-hand side of the alert page. If an alert doesn't exist in the default branch, the status of the alert will display as "in pull request" or "in branch" and will be colored grey. The **Development** section shows linked branches and pull requests that will fix the alert.

In the detailed view for an alert, some code scanning tools, like CodeQL analysis, also include a description of the problem and a **Show more** link for guidance on how to fix your code.

![Screenshot showing the description for a code scanning alert. A link labeled "Show more" is highlighted with a dark orange outline.](/assets/images/help/repository/code-scanning-pr-alert.png)

## Commenting on an alert in a pull request

You can comment on any code scanning alert that appears in a pull request. Alerts appear as annotations in the **Conversation** tab of a pull request, as part of a pull request review, and also are shown in the **Files changed** tab.

You can choose to require all conversations in a pull request, including those on code scanning alerts, to be resolved before a pull request can be merged. For more information, see [About protected branches](/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches#require-conversation-resolution-before-merging).

To track remediation work in your team's workflow without leaving GitHub, you can link alerts to issues. See [Linking code scanning alerts to GitHub issues](/en/code-security/how-tos/manage-security-alerts/manage-code-scanning-alerts/linking-code-scanning-alerts-to-github-issues).

## Fixing an alert on your pull request

Anyone with push access to a pull request can fix a code scanning alert that's identified on that pull request. If you commit changes to the pull request this triggers a new run of the pull request checks. If your changes fix the problem, the alert is closed and the annotation removed.

## Working with Copilot Autofix suggestions for alerts on a pull request

GitHub Copilot Autofix is an expansion of code scanning that provides you with targeted recommendations to help you fix code scanning alerts (including CodeQL alerts) in pull requests. The potential fixes are generated automatically by large language models (LLMs) using data from the codebase, the pull request, and from code scanning analysis.

> \[!NOTE]
> You do not need a subscription to GitHub Copilot to use GitHub Copilot Autofix. Copilot Autofix is available to all public repositories on GitHub.com, as well as internal or private repositories owned by organizations and enterprises that have a license for GitHub Code Security.

![Screenshot of the check failure for a code scanning alert in a pull request. Part of the "autofix" suggestion is outlined in dark orange.](/assets/images/help/code-scanning/alert+autofix.png)

### Generating Copilot Autofix suggestions and publishing to a pull request

When Copilot Autofix is enabled for a repository, alerts are displayed in pull requests as normal and information from any alerts found by code scanning is automatically sent to the LLM for processing. When LLM analysis is complete, any results are published as comments on relevant alerts. For more information, see [Application card: GitHub security and quality AI features](/en/code-security/code-scanning/managing-code-scanning-alerts/responsible-use-autofix-code-scanning).

> \[!NOTE]
>
> * Copilot Autofix supports a subset of CodeQL queries. For information about the availability of Copilot Autofix, see the query tables linked from [Queries for CodeQL analysis](/en/code-security/code-scanning/reference/code-ql-built-in-queries).
> * When analysis is complete, all relevant results are published to the pull request at once. If at least one alert in your pull request has an Copilot Autofix suggestion, you should assume that the LLM has finished identifying potential fixes for your code.
> * On alerts generated from queries that are not supported by Copilot Autofix, you will see a note telling you that the query is not supported. If a suggestion for a supported query fails to generate, you will see a note on the alert prompting you to try pushing another commit or to contact support.
> * Copilot Autofix for code scanning alerts won't be able to generate a fix for every alert in every situation. The feature operates on a best-effort basis and is not guaranteed to succeed 100% of the time. For information about the limitations of automatically generated fixes, see [Limitations of suggestions](/en/code-security/code-scanning/managing-code-scanning-alerts/about-autofix-for-codeql-code-scanning#limitations-of-suggestions).

Usually, when you suggest changes to a pull request, your comment contains changes for a single file that is changed in the pull request. The following screenshot shows an Copilot Autofix comment that suggests changes to the `index.js` file where the alert is displayed. Since the potential fix requires a new dependency on `escape-html`, the comment also suggests adding this dependency to the `package.json` file, even though the original pull request makes no changes to this file.

![Screenshot of Copilot Autofix suggestion to edit the current file. A suggested change in "package.json" is outlined in dark orange.](/assets/images/help/code-scanning/autofix-example.png)

### Assessing and committing an Copilot Autofix suggestion

Each Copilot Autofix suggestion demonstrates a potential solution for a code scanning alert in your codebase. You must assess the suggested changes to determine whether they are a good solution for your codebase and to ensure that they maintain the intended behavior. For information about the limitations of Copilot Autofix suggestions, see [Limitations of suggestions](/en/code-security/code-scanning/managing-code-scanning-alerts/responsible-use-autofix-code-scanning#limitations-of-suggestions) and [Mitigating the limitations of suggestions](/en/code-security/code-scanning/managing-code-scanning-alerts/responsible-use-autofix-code-scanning#mitigating-the-limitations-of-suggestions) in "Responsible use of Copilot Autofix for code scanning."

1. Click **Edit** to display the editing options and select your preferred method.
   * Under **Edit with GitHub CLI**, follow the instructions for checking out the pull request locally and applying the suggested fix.
   * Select **Edit FILENAME** to edit the file directly on GitHub with the suggested fix applied.
2. Optionally, if you prefer to apply the fix on a local repository or branch, select the <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copy" aria-label="copy" role="img"><path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path></svg> dropdown menu on the suggestion.
   * Select **View autofix patch** to display instructions for applying the suggested fix to any local repository or branch.
   * Select **Copy modified line LINE\_NUMBER** to copy a specific line of the suggestion.
3. Test and modify the suggested fix as needed.
4. When you have finished testing your changes, commit the changes, and push them to your branch.
5. Pushing the changes to your branch will trigger all the usual tests for your pull request. Confirm that your unit tests still pass and that the code scanning alert is now fixed.

### Dismissing a Copilot Autofix suggestion

If you decide to reject a Copilot Autofix suggestion, click **Dismiss suggestion** in the comment to dismiss the suggested fix.

## Dismissing an alert on your pull request

An alternative way of closing an alert is to dismiss it. You can dismiss an alert if you don't think it needs to be fixed. For example, an error in code that's used only for testing, or when the effort of fixing the error is greater than the potential benefit of improving the code. If you have write permission for the repository, a **Dismiss alert** button is available in code annotations and in the alerts summary. When you click **Dismiss alert** you will be prompted to choose a reason for closing the alert.

![Screenshot of a check failure for code scanning. The "Dismiss alert" button is highlighted in dark orange. The "Dismiss alert" drop-down is shown.](/assets/images/help/repository/code-scanning-alert-dropdown-reason.png)

It's important to choose the appropriate reason from the drop-down menu as this may affect whether a query continues to be included in future analysis. Optionally, you can comment on a dismissal to record the context of an alert dismissal. The dismissal comment is added to the alert timeline and can be used as justification during auditing and reporting. You can retrieve or set a comment by using the code scanning REST API. The comment is contained in `dismissed_comment` for the `alerts/{alert_number}` endpoint. For more information, see [REST API endpoints for code scanning](/en/rest/code-scanning/code-scanning#update-a-code-scanning-alert).

If you dismiss a CodeQL alert as a false positive result, for example because the code uses a sanitization library that isn't supported, consider contributing to the CodeQL repository and improving the analysis. For more information about CodeQL, see [Contributing to CodeQL](https://github.com/github/codeql/blob/main/CONTRIBUTING.md).

For more information about dismissing alerts, see [Resolving code scanning alerts](/en/code-security/code-scanning/managing-code-scanning-alerts/resolving-code-scanning-alerts#dismissing--alerts).