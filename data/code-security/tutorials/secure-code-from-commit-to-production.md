# Secure code from an agent's first commit to production

AI agents ship code faster than security teams can review it by hand. GitHub closes that gap with security built into every stage of the software development lifecycle, from local review to organization-wide detection and automated remediation, all without leaving GitHub.

## Links

### Review an agent's changes before you push

* [Scanning for secrets with the GitHub MCP server](/en/code-security/how-tos/use-ghas-with-ai-coding-agents/scan-for-secrets-with-github-mcp-server)

  Detect exposed secrets in real time from your AI coding agent, before they ever reach your repository.

* [Viewing and fixing security alerts in the GitHub Copilot app](/en/copilot/how-tos/github-copilot-app/view-and-fix-security-alerts)

  Work through code scanning alerts alongside your code using the GitHub security extension for the GitHub Copilot app.

### Stop leaked credentials before they reach your repository

* [Push protection](/en/code-security/concepts/secret-security/push-protection)

  Secure your secrets by stopping them from ever reaching your repository with push protection.

* [Enabling push protection for AI-detected secrets](/en/code-security/how-tos/secure-your-secrets/prevent-future-leaks/enable-ai-push-protection)

  Block pushes that contain passwords and other unstructured secrets found using AI.

### Detect vulnerabilities at scale with hybrid detection

* [Code scanning](/en/code-security/concepts/code-scanning/code-scanning)

  You can use code scanning to find security vulnerabilities and errors in the code for your project on GitHub.

* [AI Scan for a repository's backlog](/en/code-security/concepts/code-scanning/ai-scan-for-repositories)

  Find additional security vulnerabilities across languages and manage the results in your existing code scanning backlog.

* [AI Scan for pull requests](/en/code-security/concepts/code-scanning/ai-powered-security-detections)

  AI Scan uses an AI-based scanning engine to find security vulnerabilities in pull requests for languages and frameworks not covered by CodeQL.

* [Running the code security risk assessment for your organization](/en/code-security/how-tos/secure-at-scale/configure-organization-security/configure-specific-tools/assess-your-vulnerability-risk)

  Determine your organization's exposure to vulnerabilities by generating a code security risk assessment report.

### Define and enforce the rules for merging code

* [Managing custom properties for repositories in your organization](/en/organizations/managing-organization-settings/managing-custom-properties-for-repositories-in-your-organization)

  With custom properties, you can add metadata to repositories in your organization. You can use those properties to target repositories with rulesets.

* [Set code scanning merge protection](/en/code-security/how-tos/find-and-fix-code-vulnerabilities/manage-your-configuration/set-merge-protection)

  Secure your codebase by blocking pull requests that fail code scanning checks.

### Resolve alerts with draft pull requests

* [About autofix for code scanning](/en/code-security/concepts/code-scanning/autofix-for-code-scanning)

  Autofix generates potential fixes for code scanning alerts, helping you remediate existing vulnerabilities.

* [Resolving code scanning alerts](/en/code-security/how-tos/manage-security-alerts/manage-code-scanning-alerts/resolve-alerts)

  From the security view, you can view, fix, or dismiss alerts for potential vulnerabilities or errors in your project's code.

* [About security campaigns](/en/code-security/concepts/security-at-scale/about-security-campaigns)

  You can fix security alerts at scale by creating security campaigns and collaborating with developers to burn down your security backlog.

### Go beyond security to code quality

* [About GitHub Code Quality](/en/get-started/learning-about-github/about-github-code-quality)

  Decide whether GitHub Code Quality meets your team's needs, how it complements other GitHub products, and what to consider before purchasing.

* [Enabling GitHub Code Quality](/en/code-security/how-tos/maintain-quality-code/enable-code-quality)

  Turn on Code Quality to give your teams a consistent quality baseline: automatically catching, fixing, and reporting code quality issues in pull requests and on your default branch.