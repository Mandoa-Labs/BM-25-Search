# Automatically merging a pull request

Enable or disable auto-merge for pull requests to streamline your workflow and automatically merge changes once all requirements are met.

## About auto-merge

Auto-merge merges a pull request automatically after all required reviews and status checks pass. Before you use auto-merge, it must be enabled for the repository. See [Managing auto-merge for pull requests in your repository](/en/repositories/configuring-branches-and-merges-in-your-repository/configuring-pull-request-merges/managing-auto-merge-for-pull-requests-in-your-repository).

Auto-merge is disabled if someone without write permissions pushes new changes to the head branch or switches the base branch.

## Enabling auto-merge

> \[!NOTE]
> The option to enable auto-merge is shown only on pull requests that cannot be merged immediately. For example, when a branch protection rule enforces "Require pull request reviews before merging" or "Require status checks to pass before merging" and these conditions are not yet met. For more information, see [Managing a branch protection rule](/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/managing-a-branch-protection-rule).

People with write permissions to a repository can enable auto-merge for a pull request.

1. On GitHub, navigate to the main page of the repository.

2. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-git-pull-request" aria-label="git-pull-request" role="img"><path d="M1.5 3.25a2.25 2.25 0 1 1 3 2.122v5.256a2.251 2.251 0 1 1-1.5 0V5.372A2.25 2.25 0 0 1 1.5 3.25Zm5.677-.177L9.573.677A.25.25 0 0 1 10 .854V2.5h1A2.5 2.5 0 0 1 13.5 5v5.628a2.251 2.251 0 1 1-1.5 0V5a1 1 0 0 0-1-1h-1v1.646a.25.25 0 0 1-.427.177L7.177 3.427a.25.25 0 0 1 0-.354ZM3.75 2.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm0 9.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm8.25.75a.75.75 0 1 0 1.5 0 .75.75 0 0 0-1.5 0Z"></path></svg> Pull requests**.

3. In the "Pull Requests" list, click the pull request you want to auto-merge.

4. Optionally, select the <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-triangle-down" aria-label="Select the merge method" role="img"><path d="m4.427 7.427 3.396 3.396a.25.25 0 0 0 .354 0l3.396-3.396A.25.25 0 0 0 11.396 7H4.604a.25.25 0 0 0-.177.427Z"></path></svg> dropdown menu, then click a merge method. See [Pull request merges](/en/pull-requests/reference/pull-request-merges).

   ![Screenshot of the merge box of a pull request. A dropdown menu, labeled with a downward-facing triangle, is outlined in dark orange.](/assets/images/help/pull_requests/enable-auto-merge-drop-down.png)

5. Click **Enable auto-merge**.

6. If you chose the merge or squash and merge methods, type a commit message and description and choose the email address you want to author the merge commit.

   > \[!NOTE]
   > The email dropdown menu is not available if you have email privacy enabled or if you only have one verified and visible email associated with your GitHub account.

7. Click **Confirm auto-merge**.

## Disabling auto-merge

People with write permissions to a repository and pull request authors can disable auto-merge for a pull request.

1. On GitHub, navigate to the main page of the repository.
2. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-git-pull-request" aria-label="git-pull-request" role="img"><path d="M1.5 3.25a2.25 2.25 0 1 1 3 2.122v5.256a2.251 2.251 0 1 1-1.5 0V5.372A2.25 2.25 0 0 1 1.5 3.25Zm5.677-.177L9.573.677A.25.25 0 0 1 10 .854V2.5h1A2.5 2.5 0 0 1 13.5 5v5.628a2.251 2.251 0 1 1-1.5 0V5a1 1 0 0 0-1-1h-1v1.646a.25.25 0 0 1-.427.177L7.177 3.427a.25.25 0 0 1 0-.354ZM3.75 2.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm0 9.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm8.25.75a.75.75 0 1 0 1.5 0 .75.75 0 0 0-1.5 0Z"></path></svg> Pull requests**.
3. In the "Pull Requests" list, click the pull request for which you want to disable auto-merge.
4. In the merge box, click **Disable auto-merge**.