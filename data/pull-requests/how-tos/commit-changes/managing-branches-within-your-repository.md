# Managing branches within your repository

Create new branches for development and delete unused branches directly on GitHub.

## Creating a branch

Create a branch for a separate place to work on changes before opening a pull request.

> \[!NOTE]
> You can only create a branch in a repository to which you have write access.

### Creating a branch via the branches overview

1. On GitHub, navigate to the main page of the repository.
2. From the file tree view on the left, select the <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-git-branch" aria-label="git-branch" role="img"><path d="M9.5 3.25a2.25 2.25 0 1 1 3 2.122V6A2.5 2.5 0 0 1 10 8.5H6a1 1 0 0 0-1 1v1.128a2.251 2.251 0 1 1-1.5 0V5.372a2.25 2.25 0 1 1 1.5 0v1.836A2.493 2.493 0 0 1 6 7h4a1 1 0 0 0 1-1v-.628A2.25 2.25 0 0 1 9.5 3.25Zm-6 0a.75.75 0 1 0 1.5 0 .75.75 0 0 0-1.5 0Zm8.25-.75a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5ZM4.25 12a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Z"></path></svg> branch dropdown menu, then click **View all branches**. You can also find the branch dropdown menu at the top of the integrated file editor.

   ![Screenshot of the file tree view for a repository. A dropdown menu for branches is expanded and outlined in dark orange.](/assets/images/help/repository/file-tree-view-branch-dropdown-expanded.png)
3. Click **New branch**.

   ![Screenshot of the "Branches" page for a repository. A green button, labeled "New branch", is highlighted with an orange outline.](/assets/images/help/branches/new-branch-button.png)
4. Under "Branch name", type a name for the branch.
5. Under "Branch source", choose the repository and branch to base your new branch on.
6. Click **Create branch**.

### Creating a branch using the branch dropdown

1. On GitHub, navigate to the main page of the repository.

2. Select the <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-git-branch" aria-label="git-branch" role="img"><path d="M9.5 3.25a2.25 2.25 0 1 1 3 2.122V6A2.5 2.5 0 0 1 10 8.5H6a1 1 0 0 0-1 1v1.128a2.251 2.251 0 1 1-1.5 0V5.372a2.25 2.25 0 1 1 1.5 0v1.836A2.493 2.493 0 0 1 6 7h4a1 1 0 0 0 1-1v-.628A2.25 2.25 0 0 1 9.5 3.25Zm-6 0a.75.75 0 1 0 1.5 0 .75.75 0 0 0-1.5 0Zm8.25-.75a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5ZM4.25 12a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Z"></path></svg> branch dropdown menu, in the file tree view or at the top of the integrated file editor.

   ![Screenshot of the file tree view for a repository. A dropdown menu for branches is outlined in dark orange.](/assets/images/help/branches/file-tree-view-branch-dropdown.png)

3. Optionally, to create the new branch from a branch other than the default branch of the repository, click another branch. Then, select the branch dropdown menu again.

4. In the "Find or create a branch..." text field, type a unique name for your new branch, then click **Create branch**.

   ![Screenshot of the branch selector dropdown menu. "Create branch: new-branch" is highlighted with an orange outline.](/assets/images/help/branches/create-branch-text.png)

### Creating a branch for an issue

You can create a branch to work on an issue directly from the issue page. See [Creating a branch to work on an issue](/en/issues/tracking-your-work-with-issues/using-issues/creating-a-branch-for-an-issue).

## Deleting a branch

Delete branches that you no longer need, such as branches for merged or closed work.

You can have head branches automatically deleted after pull requests are merged in your repository. See [Managing the automatic deletion of branches](/en/repositories/configuring-branches-and-merges-in-your-repository/configuring-pull-request-merges/managing-the-automatic-deletion-of-branches).

> \[!NOTE]
> If the branch you want to delete is the repository's default branch, choose a new default branch first. See [Changing the default branch](/en/repositories/configuring-branches-and-merges-in-your-repository/managing-branches-in-your-repository/changing-the-default-branch).

If the branch is associated with an open pull request, merge or close the pull request before deleting the branch.

1. On GitHub, navigate to the main page of the repository.
2. From the file tree view on the left, select the <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-git-branch" aria-label="git-branch" role="img"><path d="M9.5 3.25a2.25 2.25 0 1 1 3 2.122V6A2.5 2.5 0 0 1 10 8.5H6a1 1 0 0 0-1 1v1.128a2.251 2.251 0 1 1-1.5 0V5.372a2.25 2.25 0 1 1 1.5 0v1.836A2.493 2.493 0 0 1 6 7h4a1 1 0 0 0 1-1v-.628A2.25 2.25 0 0 1 9.5 3.25Zm-6 0a.75.75 0 1 0 1.5 0 .75.75 0 0 0-1.5 0Zm8.25-.75a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5ZM4.25 12a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Z"></path></svg> branch dropdown menu, then click **View all branches**. You can also find the branch dropdown menu at the top of the integrated file editor.

   ![Screenshot of the file tree view for a repository. A dropdown menu for branches is expanded and outlined in dark orange.](/assets/images/help/repository/file-tree-view-branch-dropdown-expanded.png)
3. Next to the branch that you want to delete, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-trash" aria-label="The trash icon" role="img"><path d="M11 1.75V3h2.25a.75.75 0 0 1 0 1.5H2.75a.75.75 0 0 1 0-1.5H5V1.75C5 .784 5.784 0 6.75 0h2.5C10.216 0 11 .784 11 1.75ZM4.496 6.675l.66 6.6a.25.25 0 0 0 .249.225h5.19a.25.25 0 0 0 .249-.225l.66-6.6a.75.75 0 0 1 1.492.149l-.66 6.6A1.748 1.748 0 0 1 10.595 15h-5.19a1.75 1.75 0 0 1-1.741-1.575l-.66-6.6a.75.75 0 1 1 1.492-.15ZM6.5 1.75V3h3V1.75a.25.25 0 0 0-.25-.25h-2.5a.25.25 0 0 0-.25.25Z"></path></svg> .

   ![Screenshot of a branch in the branch list. A trash icon is highlighted with an orange outline.](/assets/images/help/branches/branches-delete.png)
4. If the branch is associated with at least one open pull request, deleting the branch closes the pull requests. Read the warning, then click **Delete**.

If you delete a head branch after its pull request has been merged, GitHub checks for any open pull requests in the same repository that specify the deleted branch as their base branch. GitHub automatically updates any such pull requests, changing their base branch to the merged pull request's base branch.
See [Branches](/en/pull-requests/reference/branches).

## Further reading

* [Branches](/en/pull-requests/reference/branches)
* [Viewing branches in your repository](/en/repositories/configuring-branches-and-merges-in-your-repository/managing-branches-in-your-repository/viewing-branches-in-your-repository)
* [Deleting and restoring branches in a pull request](/en/repositories/configuring-branches-and-merges-in-your-repository/managing-branches-in-your-repository/deleting-and-restoring-branches-in-a-pull-request)