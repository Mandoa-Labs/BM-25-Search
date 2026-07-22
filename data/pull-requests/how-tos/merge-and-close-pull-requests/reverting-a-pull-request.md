# Reverting a pull request

Create a new pull request to revert a previously merged pull request and address merge conflicts if they arise.

## About reverting a pull request

Reverting a merged pull request creates a new pull request that reverts the original merge commit. You must have [write permissions](/en/organizations/managing-user-access-to-your-organizations-repositories/managing-repository-roles/repository-roles-for-an-organization) in the repository.

## Reverting a pull request

> \[!NOTE]
> You may need to revert individual commits if reverting the pull request causes merge conflicts or if the original pull request was not merged on GitHub. See [Git revert](https://git-scm.com/docs/git-revert.html) in the Git documentation.

1. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-git-pull-request" aria-label="git-pull-request" role="img"><path d="M1.5 3.25a2.25 2.25 0 1 1 3 2.122v5.256a2.251 2.251 0 1 1-1.5 0V5.372A2.25 2.25 0 0 1 1.5 3.25Zm5.677-.177L9.573.677A.25.25 0 0 1 10 .854V2.5h1A2.5 2.5 0 0 1 13.5 5v5.628a2.251 2.251 0 1 1-1.5 0V5a1 1 0 0 0-1-1h-1v1.646a.25.25 0 0 1-.427.177L7.177 3.427a.25.25 0 0 1 0-.354ZM3.75 2.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm0 9.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm8.25.75a.75.75 0 1 0 1.5 0 .75.75 0 0 0-1.5 0Z"></path></svg> Pull requests**.

2. In the "Pull Requests" list, click the pull request you want to revert.

3. Near the bottom of the pull request, click **Revert**. If the **Revert** option isn't displayed, you need to ask the repository administrator for write permissions.

   ![Screenshot of a pull request's timeline. The "Revert" button is outlined in dark orange.](/assets/images/help/pull_requests/revert-pull-request-link.png)

4. Merge the resulting pull request. See [Merging a pull request](/en/pull-requests/how-tos/merge-and-close-pull-requests/merging-a-pull-request).