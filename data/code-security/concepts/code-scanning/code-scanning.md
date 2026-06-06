# Code scanning

You can use code scanning to find security vulnerabilities and errors in the code for your project on GitHub.

Code scanning is a feature that you use to analyze the code in a GitHub repository to find security vulnerabilities and coding errors. Any problems identified by the analysis are shown in your repository.

You can use code scanning to find, triage, and prioritize fixes for existing problems in your code. Code scanning also prevents developers from introducing new problems. You can schedule scans for specific days and times, or trigger scans when a specific event occurs in the repository, such as a push.

If code scanning finds a potential vulnerability or error in your code, GitHub displays an alert in the repository. After you fix the code that triggered the alert, GitHub closes the alert. For more information, see [Resolving code scanning alerts](/en/code-security/code-scanning/managing-code-scanning-alerts/resolving-code-scanning-alerts).

GitHub Copilot Autofix will suggest fixes for alerts from code scanning analysis, allowing developers to prevent and reduce vulnerabilities with less effort. For more information, see [Application card: GitHub security and quality AI features](/en/code-security/code-scanning/managing-code-scanning-alerts/responsible-use-autofix-code-scanning).

To monitor results from code scanning across your repositories or your organization, you can use webhooks and the code scanning API. For information about the webhooks for code scanning, see
[Webhook events and payloads](/en/webhooks-and-events/webhooks/webhook-events-and-payloads#code_scanning_alert). For information about API endpoints, see [REST API endpoints for code scanning](/en/rest/code-scanning/code-scanning).

Code scanning uses GitHub Actions, with each workflow run consuming GitHub Actions minutes. If you want to use code scanning on private repositories, you need a GitHub Code Security license. For more information, see [GitHub Actions billing](/en/billing/managing-billing-for-github-actions/about-billing-for-github-actions). For information about how you can try GitHub Enterprise with GitHub Advanced Security for free, see [Setting up a trial of GitHub Enterprise Cloud](/en/enterprise-cloud@latest/admin/overview/setting-up-a-trial-of-github-enterprise-cloud) and [Setting up a trial of GitHub Advanced Security](/en/enterprise-cloud@latest/billing/managing-billing-for-your-products/managing-billing-for-github-advanced-security/setting-up-a-trial-of-github-advanced-security#setting-up-your-trial-of-github-advanced-security) in the GitHub Enterprise Cloud documentation.

If you want to assess your organization's exposure to vulnerabilities before purchasing a license, you can run a free code security risk assessment. See [Code security risk assessment](/en/code-security/concepts/code-scanning/code-security-risk-assessment).

To get started with code scanning, see [Configuring default setup for code scanning](/en/code-security/code-scanning/enabling-code-scanning/configuring-default-setup-for-code-scanning).

## About tools for code scanning

You can configure code scanning to use the CodeQL product maintained by GitHub or a third-party code scanning tool.

### About CodeQL analysis

CodeQL is the code analysis engine developed by GitHub to automate security checks. You can analyze your code using CodeQL and display the results as code scanning alerts. For more information about CodeQL, see [Code scanning with CodeQL](/en/code-security/code-scanning/introduction-to-code-scanning/about-code-scanning-with-codeql).

### About third-party code scanning tools

Code scanning is interoperable with third-party code scanning tools that output Static Analysis Results Interchange Format (SARIF) data. SARIF is an open standard. For more information, see [SARIF support for code scanning](/en/code-security/code-scanning/integrating-with-code-scanning/sarif-support-for-code-scanning).

You can run third-party analysis tools within GitHub using actions or within an external CI system. For more information, see [Configuring advanced setup for code scanning](/en/code-security/code-scanning/creating-an-advanced-setup-for-code-scanning/configuring-advanced-setup-for-code-scanning#configuring-code-scanning-using-third-party-actions) or [Uploading a SARIF file to GitHub](/en/code-security/code-scanning/integrating-with-code-scanning/uploading-a-sarif-file-to-github).

## About the tool status page

The tool status page shows useful information about all of your code scanning tools. If code scanning is not working as you'd expect, the tool status page is a good starting point for debugging problems. For more information, see [Use the tool status page for code scanning](/en/code-security/code-scanning/managing-your-code-scanning-configuration/about-the-tool-status-page).