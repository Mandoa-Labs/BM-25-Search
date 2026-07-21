# Fixing code quality findings in recently merged files

Apply autofixes or delegate remediation work to Copilot for quality issues detected by AI-powered analysis of recently merged code.

> \[!TIP]
> If you're new to Code Quality, see [Raising your repository's code quality score](/en/code-security/tutorials/improve-code-quality/raise-your-quality-rating?utm_campaign=code-quality-ga-july-2026\&utm_medium=docs\&utm_source=docs-fix-recent-merges-walkthrough-tip) for a guided walkthrough of reviewing and improving your repository's quality scores.

## How Code Quality analyzes recently merged files

Code Quality runs an AI-powered scan on recently changed files after code is merged to your default branch. This scan uses a large language model to report up to 5 findings per file in up to 5 files—across all languages, without being limited to predefined rules.

> \[!NOTE]
> The "AI findings" page for recently changed files is currently in public preview and subject to change.

## Viewing recent suggestions

1. Navigate to the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab of your repository.
2. Click to expand **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-code-review" aria-label="code review" role="img"><path d="M1.75 1h12.5c.966 0 1.75.784 1.75 1.75v8.5A1.75 1.75 0 0 1 14.25 13H8.061l-2.574 2.573A1.458 1.458 0 0 1 3 14.543V13H1.75A1.75 1.75 0 0 1 0 11.25v-8.5C0 1.784.784 1 1.75 1ZM1.5 2.75v8.5c0 .138.112.25.25.25h2a.75.75 0 0 1 .75.75v2.19l2.72-2.72a.749.749 0 0 1 .53-.22h6.5a.25.25 0 0 0 .25-.25v-8.5a.25.25 0 0 0-.25-.25H1.75a.25.25 0 0 0-.25.25Zm5.28 1.72a.75.75 0 0 1 0 1.06L5.31 7l1.47 1.47a.751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018l-2-2a.75.75 0 0 1 0-1.06l2-2a.75.75 0 0 1 1.06 0Zm2.44 0a.75.75 0 0 1 1.06 0l2 2a.75.75 0 0 1 0 1.06l-2 2a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042L10.69 7 9.22 5.53a.75.75 0 0 1 0-1.06Z"></path></svg> Code quality**, then click **AI findings**.

   On the **AI findings** page, each file is listed with the number of quality problems identified and when the file was pushed to the default branch. Click a file name to view the quality problems and their suggested fixes.

   ![Screenshot of the "AI findings" view for code quality.](/assets/images/help/code-quality/ai-suggestions-repo.png)

> \[!NOTE]
> This view is empty if the repository is inactive or if LLM analysis could not suggest ways to improve code quality in recent pushes to the default branch.

## Resolving a finding

You can delegate remediation work to Copilot or open a pull request yourself.

### Delegate to Copilot

You need a Copilot license to assign work to Copilot cloud agent. <br><a href="https://github.com/features/copilot/plans?ref_product=copilot&ref_type=purchase&ref_style=button&utm_campaign=code-quality-ga-july-2026&utm_medium=docs&utm_source=docs-fix-findings-merge-copilot-signup" target="_blank" class="btn btn-primary mt-3 mr-3 no-underline"><span>Sign up for Copilot</span> <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-link-external" aria-label="link external icon" role="img"><path d="M3.75 2h3.5a.75.75 0 0 1 0 1.5h-3.5a.25.25 0 0 0-.25.25v8.5c0 .138.112.25.25.25h8.5a.25.25 0 0 0 .25-.25v-3.5a.75.75 0 0 1 1.5 0v3.5A1.75 1.75 0 0 1 12.25 14h-8.5A1.75 1.75 0 0 1 2 12.25v-8.5C2 2.784 2.784 2 3.75 2Zm6.854-1h4.146a.25.25 0 0 1 .25.25v4.146a.25.25 0 0 1-.427.177L13.03 4.03 9.28 7.78a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042l3.75-3.75-1.543-1.543A.25.25 0 0 1 10.604 1Z"></path></svg></a>

1. Select the file or files you want to include for the fix, then click **Assign to Copilot**.
2. There is a delay while Copilot sets up the work. When the pull request is open and work is in progress, a banner is displayed with a link to the pull request.
3. Track Copilot's work:
   * In the pull request, the summary is updated as work progresses.
   * Using the [agents page](https://github.com/copilot/agents?ref_product=copilot\&ref_type=engagement\&ref_style=text\&utm_campaign=code-quality-ga-july-2026\&utm_medium=docs\&utm_source=docs-fix-findings-merge-agent-page) or session logs. See [Managing agent sessions](/en/copilot/how-tos/copilot-on-github/use-copilot-agents/manage-and-track-agents).

### Open a pull request

1. Click the file name to view details of the quality problems detected.

2. Review the problems and suggested fixes.

3. Expand the drop-down and then click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-git-pull-request" aria-label="Pull request" role="img"><path d="M1.5 3.25a2.25 2.25 0 1 1 3 2.122v5.256a2.251 2.251 0 1 1-1.5 0V5.372A2.25 2.25 0 0 1 1.5 3.25Zm5.677-.177L9.573.677A.25.25 0 0 1 10 .854V2.5h1A2.5 2.5 0 0 1 13.5 5v5.628a2.251 2.251 0 1 1-1.5 0V5a1 1 0 0 0-1-1h-1v1.646a.25.25 0 0 1-.427.177L7.177 3.427a.25.25 0 0 1 0-.354ZM3.75 2.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm0 9.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm8.25.75a.75.75 0 1 0 1.5 0 .75.75 0 0 0-1.5 0Z"></path></svg> **Open pull request**.

   ![Screenshot of the "AI findings" view for code quality.](/assets/images/help/code-quality/ai-suggestions-repo-fixes.png)

4. Click **Open pull request** to open a dialog of commit options.

5. Click **Commit change** to create a pull request with the fixes.

> \[!NOTE]
> When you open a pull request yourself, you can only commit fixes to one file at a time. To fix multiple files at once, you must delegate the work to Copilot.

## Further reading

* [Fixing code quality findings in your repository backlog](/en/code-security/how-tos/maintain-quality-code/fix-backlog-findings)