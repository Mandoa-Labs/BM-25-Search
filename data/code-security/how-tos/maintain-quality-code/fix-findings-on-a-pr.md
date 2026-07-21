# Fixing code quality findings on a pull request

Keep quality issues out of your default branch by applying autofixes, delegating remediation work to Copilot, or dismissing irrelevant findings.

> \[!TIP]
> If you're new to Code Quality, see [Preventing code quality issues from reaching your default branch](/en/code-security/tutorials/improve-code-quality/catch-issues-before-merge?utm_campaign=code-quality-ga-july-2026\&utm_medium=docs\&utm_source=docs-fix-pr-findings-walkthrough-tip) for a guided walkthrough of how Code Quality works on pull requests.

## How Code Quality works on pull requests

When you open a pull request, Code Quality runs **two types of analysis** and posts findings as comments on the pull request.

1. **`github-code-quality[bot]` findings**: Code Quality uses CodeQL to perform a rule-based scan of your changes. These findings are posted as comments by `github-code-quality[bot]` and include a suggested autofix. Findings are labeled by severity (**Error**, **Warning**, **Note**), and administrators can set quality gates to block merges based on the severity of these findings.

2. **Copilot findings**:  If your organization has Copilot licenses and AI features are enabled for your enterprise, Code Quality uses **Copilot code review** to identify quality issues that rules-based analysis may not detect. These findings are posted as comments by **Copilot**, and include a suggested autofix. See [About GitHub Copilot code review](/en/copilot/concepts/agents/code-review).

## Resolving a finding

1. On GitHub, navigate to your open pull request.
2. On the **Files Changed** tab, scroll to a comment left by **`github-code-quality[bot]`** or **Copilot**.
3. Carefully review the comment and the suggested autofix for logic, security, and style.
4. If you agree with the suggestion and you want to apply the fix, click **Commit suggestion**, or **Add suggestion to batch**.
5. Alternatively, if the finding isn't relevant or actionable, you can dismiss the finding. For example, you might dismiss a finding that is in legacy code no longer maintained, is a known exception to your team's coding standards, or is a false positive that doesn't pose a real quality risk.
   * For comments left by `github-code-quality[bot]`, click **Dismiss finding**.
   * For comments left by Copilot, click **Resolve**.

## Delegating remediation work to Copilot

If you have a Copilot license, you can delegate the remediation work to Copilot cloud agent. Comment on the pull request mentioning `@Copilot` and request that Copilot fix the detected issues.

![Screenshot showing a PR comment that invoked Copilot cloud agent.](/assets/images/help/code-quality/invoke-cloud-agent.png)

Copilot responds with an eyes emoji (👀) to your comment, starts a new agent session, and opens a pull request with the necessary fixes.

You can track Copilot cloud agent's work:

* In the pull request, the summary is updated as work progresses.
* Using the [agents page](https://github.com/copilot/agents?ref_product=copilot\&ref_type=engagement\&ref_style=text) or session logs, see [Managing agent sessions](/en/copilot/how-tos/copilot-on-github/use-copilot-agents/manage-and-track-agents).

You need a Copilot license to invoke Copilot cloud agent. <br><a href="https://github.com/features/copilot/plans?ref_product=copilot&ref_type=purchase&ref_style=button&utm_campaign=code-quality-ga-july-2026&utm_medium=docs&utm_source=docs-fix-findings-pr-copilot-signup" target="_blank" class="btn btn-primary mt-3 mr-3 no-underline"><span>Sign up for Copilot</span> <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-link-external" aria-label="link external icon" role="img"><path d="M3.75 2h3.5a.75.75 0 0 1 0 1.5h-3.5a.25.25 0 0 0-.25.25v8.5c0 .138.112.25.25.25h8.5a.25.25 0 0 0 .25-.25v-3.5a.75.75 0 0 1 1.5 0v3.5A1.75 1.75 0 0 1 12.25 14h-8.5A1.75 1.75 0 0 1 2 12.25v-8.5C2 2.784 2.784 2 3.75 2Zm6.854-1h4.146a.25.25 0 0 1 .25.25v4.146a.25.25 0 0 1-.427.177L13.03 4.03 9.28 7.78a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042l3.75-3.75-1.543-1.543A.25.25 0 0 1 10.604 1Z"></path></svg></a>

## Next steps

* [Viewing code coverage on pull requests](/en/code-security/how-tos/maintain-quality-code/view-coverage-on-prs)