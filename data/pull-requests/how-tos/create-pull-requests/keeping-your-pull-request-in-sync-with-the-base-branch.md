# Keeping your pull request in sync with the base branch

Update your pull request branch with changes from the base branch to resolve conflicts and ensure compatibility before merging.

## About keeping your pull request in sync

Before merging, update your pull request branch with changes from the base branch to catch conflicts or test failures early. You can update the branch from the pull request page when there are no merge conflicts and the branch is behind the base branch.

> \[!NOTE]
> You may not be able to use the `Update branch` button if the HEAD branch of your pull request is a protected branch. See [About protected branches](/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches).

If changes to the base branch cause merge conflicts in your pull request branch, resolve the conflicts before updating the branch. See [Merge conflicts](/en/pull-requests/reference/merge-conflicts).

From the pull request page, you can update by merging the base branch into your head branch or by rebasing your changes onto the latest base branch. Rebasing creates a linear history without a merge commit. See [Branches](/en/pull-requests/reference/branches#three-dot-and-two-dot-git-diff-comparisons).

## Updating your pull request branch

1. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-git-pull-request" aria-label="git-pull-request" role="img"><path d="M1.5 3.25a2.25 2.25 0 1 1 3 2.122v5.256a2.251 2.251 0 1 1-1.5 0V5.372A2.25 2.25 0 0 1 1.5 3.25Zm5.677-.177L9.573.677A.25.25 0 0 1 10 .854V2.5h1A2.5 2.5 0 0 1 13.5 5v5.628a2.251 2.251 0 1 1-1.5 0V5a1 1 0 0 0-1-1h-1v1.646a.25.25 0 0 1-.427.177L7.177 3.427a.25.25 0 0 1 0-.354ZM3.75 2.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm0 9.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm8.25.75a.75.75 0 1 0 1.5 0 .75.75 0 0 0-1.5 0Z"></path></svg> Pull requests**.
2. In the "Pull requests" list, click the pull request you want to update.
3. In the merge section near the bottom of the page, choose how to update the branch:
   * Click **Update branch** to perform a traditional merge.

     ![Screenshot of the merge section for a pull request.](/assets/images/help/pull_requests/pull-request-update-branch-with-dropdown.png)

   * Click the update branch dropdown menu, click **Update with rebase**, then click **Rebase branch** to update by rebasing on the base branch.

     ![Screenshot of the merge section of a pull request. The dropdown menu is expanded, showing "Update with merge commit" and "Update with rebase" options.](/assets/images/help/pull_requests/pull-request-update-branch-rebase-option.png)

## Further reading

* [Pull requests](/en/pull-requests/reference/pull-requests)
* [Changing the stage of a pull request](/en/pull-requests/how-tos/create-pull-requests/changing-the-stage-of-a-pull-request)