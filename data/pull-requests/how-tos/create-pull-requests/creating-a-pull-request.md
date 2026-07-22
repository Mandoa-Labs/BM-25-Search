# Creating a pull request

Create a pull request to propose changes to the code in a repository.

If you want to create a new branch for your pull request but don't have write permissions to the repository, you can fork the repository first. See [Creating a pull request from a fork](/en/pull-requests/how-tos/create-pull-requests/creating-a-pull-request-from-a-fork) and [Forks](/en/pull-requests/reference/forks).

When you create your pull request, you can specify which branch you want to merge your changes into. Pull requests can only be opened between two different branches.

> \[!NOTE]
> To open a pull request in a public repository, you must have write access to the head or the source branch or, for organization-owned repositories, you must be a member of the organization that owns the repository to open a pull request.

You can link a pull request to an issue to show that a fix is in progress and automatically close the issue when the pull request is merged. For more information, see [Linking a pull request to an issue](/en/issues/tracking-your-work-with-issues/using-issues/linking-a-pull-request-to-an-issue).

## Creating the pull request

<div class="ghd-tool webui">

1. On GitHub, navigate to the main page of the repository.

2. In the "Branch" menu, choose the branch that contains your commits.

   ![Screenshot of the branch dropdown menu on the main page of a repository.](/assets/images/help/pull_requests/branch-dropdown.png)

3. Above the list of files, in the yellow banner, click **Compare & pull request** to create a pull request for the associated branch.

   ![Screenshot of the banner above the list of files.](/assets/images/help/pull_requests/pull-request-compare-pull-request.png)

4. Use the *base* branch dropdown menu to select the branch where you want to merge your changes. Then, use the *compare* branch dropdown menu to choose the topic branch where you made your changes.

5. Type a title and description for your pull request.

6. To create a pull request that is ready for review, click **Create Pull Request**.
   To create a draft pull request, use the drop-down and select **Create Draft Pull Request**, then click **Draft Pull Request**. If you are the member of an organization, you may need to request access to draft pull requests from an organization owner. See [Pull requests](/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests#draft-pull-requests).

> \[!TIP]
> After you create a pull request, you can ask a specific person to review your proposed changes. See [Requesting a pull request review](/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/requesting-a-pull-request-review).

After your pull request has been reviewed, it can be merged into the repository. See [Merging a pull request](/en/pull-requests/how-tos/merge-and-close-pull-requests/merging-a-pull-request).

</div>

<div class="ghd-tool cli">

> \[!NOTE]
> To learn more about GitHub CLI, see [About GitHub CLI](/en/github-cli/github-cli/about-github-cli).

To create a pull request, use the `gh pr create` subcommand.

```shell
gh pr create
```

To assign a pull request to an individual, use the `--assignee` or `-a` flags. You can use `@me` to self-assign the pull request.

```shell
gh pr create --assignee "@octocat"
```

To specify the branch into which you want the pull request merged, use the `--base` or `-B` flags. To specify the branch that contains commits for your pull request, use the `--head` or `-H` flags.

```shell
gh pr create --base my-base-branch --head my-changed-branch
```

To include a title and body for the new pull request, use the `--title` and `--body` flags.

```shell
gh pr create --title "The bug is fixed" --body "Everything works again"
```

To mark a pull request as a draft, use the `--draft` flag.

```shell
gh pr create --draft
```

To add labels or milestones to the new pull request, use the `--label` and `--milestone` flags.

```shell
gh pr create --label "bug,help wanted" --milestone octocat-milestone
```

To add the new pull request to a specific project, use the `--project` flag.

```shell
gh pr create --project octocat-project
```

To assign an individual or team as reviewers, use the `--reviewer` flag.

```shell
gh pr create --reviewer monalisa,hubot --reviewer myorg/team-name
```

To create the pull request in your default web browser, use the `--web` flag.

```shell
gh pr create --web
```

</div>

<div class="ghd-tool desktop">

1. Click **Preview Pull Request**. GitHub Desktop opens a preview dialog that shows the diff of the changes between your current branch and the base branch.

   Alternatively, to go straight to GitHub to create your pull request, select the dropdown icon and click **Create Pull Request**.

2. Confirm that the branch in the **base:** dropdown menu is the branch where you want to merge your changes.

   ![Screenshot of the "Open a Pull Request" dialog window. A button with a dropdown icon, labeled "base: development", is outlined in orange.](/assets/images/help/desktop/base-branch-selection.png)

   GitHub Desktop tells you whether the current branch can be automatically merged into the base branch.

   ![Screenshot of the "Open a Pull Request" dialog window. A status label stating "Can't automatically merge" is highlighted with an orange outline.](/assets/images/help/desktop/preview-dialog-merge-status.png)

3. Click **Create Pull Request**. GitHub Desktop opens your default browser and takes you to GitHub.

4. Type a title and description for your pull request.

5. To create a pull request that is ready for review, click **Create Pull Request**.
   To create a draft pull request, use the drop-down and select **Create Draft Pull Request**, then click **Draft Pull Request**. If you are the member of an organization, you may need to request access to draft pull requests from an organization owner. See [Pull requests](/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests#draft-pull-requests).

</div>

<div class="ghd-tool codespaces">

1. After you commit changes to your local copy of the repository, click the **Create Pull Request** icon.
   ![Screenshot of the top of the "Source Control" side bar. The pull request icon is highlighted with a dark orange outline.](/assets/images/help/codespaces/codespaces-commit-pr-button.png)
2. Check that the local branch and repository you're merging from, and the remote branch and repository you're merging into, are correct. Then, give the pull request a title and a description.
   ![Screenshot of the "GitHub Pull Request" side bar with a form for creating a pull request, including "Title" and "Description" fields.](/assets/images/help/codespaces/codespaces-commit-pr.png)
3. Click **Create**.

For more information on creating pull requests in GitHub Codespaces, see [Using GitHub Codespaces for pull requests](/en/codespaces/developing-in-a-codespace/using-github-codespaces-for-pull-requests).

</div>

## Making changes to files in your pull request

After you open your pull request, you can continue changing files by adding new commits to your head branch.

<div class="ghd-tool webui">

You can also make changes to files on the GitHub website.

1. On GitHub, navigate to a pull request in a repository.
2. On the pull request, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-file-diff" aria-label="file-diff" role="img"><path d="M1 1.75C1 .784 1.784 0 2.75 0h7.586c.464 0 .909.184 1.237.513l2.914 2.914c.329.328.513.773.513 1.237v9.586A1.75 1.75 0 0 1 13.25 16H2.75A1.75 1.75 0 0 1 1 14.25Zm1.75-.25a.25.25 0 0 0-.25.25v12.5c0 .138.112.25.25.25h10.5a.25.25 0 0 0 .25-.25V4.664a.25.25 0 0 0-.073-.177l-2.914-2.914a.25.25 0 0 0-.177-.073ZM8 3.25a.75.75 0 0 1 .75.75v1.5h1.5a.75.75 0 0 1 0 1.5h-1.5v1.5a.75.75 0 0 1-1.5 0V7h-1.5a.75.75 0 0 1 0-1.5h1.5V4A.75.75 0 0 1 8 3.25Zm-3 8a.75.75 0 0 1 .75-.75h4.5a.75.75 0 0 1 0 1.5h-4.5a.75.75 0 0 1-.75-.75Z"></path></svg> Files changed**.

   ![Screenshot of the tabs for a pull request. The "Files changed" tab is outlined in dark orange.](/assets/images/help/pull_requests/pull-request-tabs-changed-files.png)
3. Scroll down to the file you want to make changes to.
   * If the pull request has a lot of files, you can use the filter to locate the file.
4. Above the file you want to change, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="Show options" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>.
   ![Screenshot of the options above a file on the "File changed" tab. The "Show options" button is highlighted with an orange rectangle.](/assets/images/help/pull_requests/menu-on-pull-request-file.png)
5. In the menu, click **Edit file**.
6. Make your changes in the editor. When you commit your change, choose to commit directly back to your head branch.

</div>

## Further reading

* [Creating a pull request from a fork](/en/pull-requests/how-tos/create-pull-requests/creating-a-pull-request-from-a-fork)
* [Keeping your pull request in sync with the base branch](/en/pull-requests/how-tos/create-pull-requests/keeping-your-pull-request-in-sync-with-the-base-branch)
* [Changing the base branch of a pull request](/en/pull-requests/how-tos/create-pull-requests/changing-the-base-branch-of-a-pull-request)
* [Creating an issue](/en/issues/tracking-your-work-with-issues/using-issues/creating-an-issue)
* [Assigning issues and pull requests to other GitHub users](/en/issues/tracking-your-work-with-issues/using-issues/assigning-issues-and-pull-requests-to-other-github-users)
* [Writing on GitHub](/en/get-started/writing-on-github)