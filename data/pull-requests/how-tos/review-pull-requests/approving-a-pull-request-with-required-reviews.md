# Approving a pull request with required reviews

Approve pull requests with required reviews, including setting approval rules, reviewing changes, and submitting feedback before merging.

You can comment on a pull request, approve the changes, or request improvements before approving. See [Reviewing proposed changes in a pull request](/en/pull-requests/how-tos/review-pull-requests/reviewing-proposed-changes-in-a-pull-request).

You can find a pull request where you or a team you're a member of is requested for review with the search qualifier `review-requested:[USERNAME]` or `team-review-requested:[TEAMNAME]`. For more information, see [Searching issues and pull requests](/en/search-github/searching-on-github/searching-issues-and-pull-requests).

> \[!TIP]
> If a pull request you approved has changed significantly, you can dismiss your review. The pull request will need a new review before it can be merged. See [Dismissing a pull request review](/en/pull-requests/how-tos/review-pull-requests/dismissing-a-pull-request-review).

1. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-git-pull-request" aria-label="git-pull-request" role="img"><path d="M1.5 3.25a2.25 2.25 0 1 1 3 2.122v5.256a2.251 2.251 0 1 1-1.5 0V5.372A2.25 2.25 0 0 1 1.5 3.25Zm5.677-.177L9.573.677A.25.25 0 0 1 10 .854V2.5h1A2.5 2.5 0 0 1 13.5 5v5.628a2.251 2.251 0 1 1-1.5 0V5a1 1 0 0 0-1-1h-1v1.646a.25.25 0 0 1-.427.177L7.177 3.427a.25.25 0 0 1 0-.354ZM3.75 2.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm0 9.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm8.25.75a.75.75 0 1 0 1.5 0 .75.75 0 0 0-1.5 0Z"></path></svg> Pull requests**.
2. In the list of pull requests, click the pull request you'd like to review.
3. On the pull request, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-file-diff" aria-label="file-diff" role="img"><path d="M1 1.75C1 .784 1.784 0 2.75 0h7.586c.464 0 .909.184 1.237.513l2.914 2.914c.329.328.513.773.513 1.237v9.586A1.75 1.75 0 0 1 13.25 16H2.75A1.75 1.75 0 0 1 1 14.25Zm1.75-.25a.25.25 0 0 0-.25.25v12.5c0 .138.112.25.25.25h10.5a.25.25 0 0 0 .25-.25V4.664a.25.25 0 0 0-.073-.177l-2.914-2.914a.25.25 0 0 0-.177-.073ZM8 3.25a.75.75 0 0 1 .75.75v1.5h1.5a.75.75 0 0 1 0 1.5h-1.5v1.5a.75.75 0 0 1-1.5 0V7h-1.5a.75.75 0 0 1 0-1.5h1.5V4A.75.75 0 0 1 8 3.25Zm-3 8a.75.75 0 0 1 .75-.75h4.5a.75.75 0 0 1 0 1.5h-4.5a.75.75 0 0 1-.75-.75Z"></path></svg> Files changed**.

   ![Screenshot of the tabs for a pull request. The "Files changed" tab is outlined in dark orange.](/assets/images/help/pull_requests/pull-request-tabs-changed-files.png)
4. Review the changes in the pull request. Optionally, comment on specific lines or files. See [Reviewing proposed changes in a pull request](/en/pull-requests/how-tos/review-pull-requests/reviewing-proposed-changes-in-a-pull-request#starting-a-review).
5. Above the changed code, click **Review changes**.

   ![Screenshot of the "Files changed" tab of a pull request. The "Review changes" button is outlined in dark orange.](/assets/images/help/pull_requests/review-changes-button.png)
6. Type a comment summarizing your feedback on the proposed changes.
7. Select **Approve** to approve merging the proposed changes.
8. Click **Submit review**.

> \[!TIP]
>
> * The **Request changes** option is purely informational and will not prevent merging unless a ruleset or classic branch protection rule is configured with the "require a pull request" option. If configured and a collaborator with `admin`, `owner`, or `write` access to the repository submits a review requesting changes, the pull request cannot be merged until the same collaborator submits another review approving the changes in the pull request.
> * Repository owners and administrators can merge a pull request even if it hasn't received an approving review, or if a reviewer who requested changes has left the organization or is unavailable.
> * If both required reviews and stale review dismissal are enabled and a code-modifying commit is pushed to the branch of an approved pull request, the approval is dismissed. The pull request must be reviewed and approved again before it can be merged.
> * When several open pull requests each have a head branch pointing to the same commit, you won’t be able to merge them if one or both have a pending or rejected review.
> * If your repository requires approving reviews from people with write or admin permissions, the reviewers sidebar groups approvals by permission level. Approvals can appear in two sections:
>   * The **top section** mostly contains approvals from people with write or admin permissions that count toward merge requirements. Approvals by GitHub Copilot also appear in this section even though GitHub Copilot reviews do not count toward those requirements.
>   * The **collapsible section (if present)** shows approvals from reviewers whose reviews do not affect whether the pull request can be merged.
> * Pull request authors cannot approve their own pull requests. You will also not be able to approve a pull request that was raised by GitHub Copilot if it was you who assigned Copilot to the issue to which the pull request relates.

## Further reading

* [About protected branches](/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches#require-pull-request-reviews-before-merging)
* [Reviewing proposed changes in a pull request](/en/pull-requests/how-tos/review-pull-requests/reviewing-proposed-changes-in-a-pull-request)
* [Commenting on a pull request](/en/pull-requests/how-tos/review-pull-requests/commenting-on-a-pull-request)