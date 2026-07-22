# Changing the stage of a pull request

Mark a draft pull request as ready for review or convert an open pull request back to a draft to manage your workflow effectively.

## Marking a pull request as ready for review

When you're ready to get feedback on your pull request, you can mark your draft pull request as ready for review. Marking a pull request as ready for review will request reviews from any code owners.

> \[!TIP]
> You can also mark a pull request as ready for review using the GitHub CLI. See [`gh pr ready`](https://cli.github.com/manual/gh_pr_ready) in the GitHub CLI documentation.

1. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-git-pull-request" aria-label="git-pull-request" role="img"><path d="M1.5 3.25a2.25 2.25 0 1 1 3 2.122v5.256a2.251 2.251 0 1 1-1.5 0V5.372A2.25 2.25 0 0 1 1.5 3.25Zm5.677-.177L9.573.677A.25.25 0 0 1 10 .854V2.5h1A2.5 2.5 0 0 1 13.5 5v5.628a2.251 2.251 0 1 1-1.5 0V5a1 1 0 0 0-1-1h-1v1.646a.25.25 0 0 1-.427.177L7.177 3.427a.25.25 0 0 1 0-.354ZM3.75 2.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm0 9.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm8.25.75a.75.75 0 1 0 1.5 0 .75.75 0 0 0-1.5 0Z"></path></svg> Pull requests**.
2. In the "Pull requests" list, click the pull request you want to mark as ready for review.
3. In the merge box, click **Ready for review**.

   ![Screenshot of the merge box in a pull request. The "Ready for review" button is outlined in dark orange.](/assets/images/help/pull_requests/ready-for-review-button.png)

## Converting a pull request to a draft

You can convert a pull request to a draft at any time. For example, if you accidentally opened a pull request instead of a draft, or if you've received feedback on your pull request that you need to address, you can convert the pull request to a draft to indicate further changes are needed.

No one can merge the pull request until you mark the pull request as ready for review again. People who are already subscribed to notifications for the pull request will not be unsubscribed when you convert the pull request to a draft.

1. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-git-pull-request" aria-label="git-pull-request" role="img"><path d="M1.5 3.25a2.25 2.25 0 1 1 3 2.122v5.256a2.251 2.251 0 1 1-1.5 0V5.372A2.25 2.25 0 0 1 1.5 3.25Zm5.677-.177L9.573.677A.25.25 0 0 1 10 .854V2.5h1A2.5 2.5 0 0 1 13.5 5v5.628a2.251 2.251 0 1 1-1.5 0V5a1 1 0 0 0-1-1h-1v1.646a.25.25 0 0 1-.427.177L7.177 3.427a.25.25 0 0 1 0-.354ZM3.75 2.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm0 9.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm8.25.75a.75.75 0 1 0 1.5 0 .75.75 0 0 0-1.5 0Z"></path></svg> Pull requests**.

2. In the "Pull requests" list, click the pull request you want to convert to a draft.

3. In the right sidebar, under "Reviewers," click **Convert to draft**.

   ![Screenshot of the "Reviewers" section in the right sidebar of a pull request. The "Convert to draft" link is outlined in dark orange.](/assets/images/help/pull_requests/convert-to-draft-link.png)

4. Click **Convert to draft**.

## Further reading

* [Pull requests](/en/pull-requests/reference/pull-requests)