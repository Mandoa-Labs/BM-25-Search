# Checking out pull requests locally

Check out pull requests locally to resolve merge conflicts, test changes, or modify code.

> \[!NOTE]
> Pull request authors can give upstream repository maintainers, or people with push access to the upstream repository, permission to make commits to their pull request's compare branch in a user-owned fork. See [Allowing changes to a pull request branch created from a fork](/en/pull-requests/how-tos/work-with-forks/allowing-changes-to-a-pull-request-branch-created-from-a-fork).

## Modifying an active pull request locally

<div class="ghd-tool webui">

1. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-git-pull-request" aria-label="git-pull-request" role="img"><path d="M1.5 3.25a2.25 2.25 0 1 1 3 2.122v5.256a2.251 2.251 0 1 1-1.5 0V5.372A2.25 2.25 0 0 1 1.5 3.25Zm5.677-.177L9.573.677A.25.25 0 0 1 10 .854V2.5h1A2.5 2.5 0 0 1 13.5 5v5.628a2.251 2.251 0 1 1-1.5 0V5a1 1 0 0 0-1-1h-1v1.646a.25.25 0 0 1-.427.177L7.177 3.427a.25.25 0 0 1 0-.354ZM3.75 2.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm0 9.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm8.25.75a.75.75 0 1 0 1.5 0 .75.75 0 0 0-1.5 0Z"></path></svg> Pull requests**.
2. In the list of pull requests, click the pull request you want to modify.
3. To choose where you want to open the pull request, select the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-code" aria-label="code" role="img"><path d="m11.28 3.22 4.25 4.25a.75.75 0 0 1 0 1.06l-4.25 4.25a.749.749 0 0 1-1.275-.326.749.749 0 0 1 .215-.734L13.94 8l-3.72-3.72a.749.749 0 0 1 .326-1.275.749.749 0 0 1 .734.215Zm-6.56 0a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042L2.06 8l3.72 3.72a.749.749 0 0 1-.326 1.275.749.749 0 0 1-.734-.215L.47 8.53a.75.75 0 0 1 0-1.06Z"></path></svg> Code** dropdown and click one of the tabs.

   ![Screenshot of a pull request title. A button with an arrow indicating a dropdown menu, labeled "Code," is outlined in dark orange.](/assets/images/help/pull_requests/open-with-button.png)

</div>

<div class="ghd-tool cli">

> \[!NOTE]
> To learn more about GitHub CLI, see [About GitHub CLI](/en/github-cli/github-cli/about-github-cli).

To check out a pull request locally, use the `gh pr checkout` subcommand. Replace `PULL-REQUEST` with the number, URL, or head branch of the pull request.

```shell
gh pr checkout PULL-REQUEST
```

</div>

## Modifying an inactive pull request locally

If a pull request’s author is unresponsive to requests or has deleted their fork, the changes proposed in that pull request can still be merged through a new pull request. However, if you want to make changes, you need to take additional steps to update the pull request.

After a pull request is opened, GitHub stores all of the changes remotely. Commits in a pull request are available in a repository even before the pull request is merged. You can fetch an open pull request and recreate it as your own.

Anyone can work with a previously opened pull request to continue working on it, test it, or open a new pull request with additional changes.

1. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-git-pull-request" aria-label="git-pull-request" role="img"><path d="M1.5 3.25a2.25 2.25 0 1 1 3 2.122v5.256a2.251 2.251 0 1 1-1.5 0V5.372A2.25 2.25 0 0 1 1.5 3.25Zm5.677-.177L9.573.677A.25.25 0 0 1 10 .854V2.5h1A2.5 2.5 0 0 1 13.5 5v5.628a2.251 2.251 0 1 1-1.5 0V5a1 1 0 0 0-1-1h-1v1.646a.25.25 0 0 1-.427.177L7.177 3.427a.25.25 0 0 1 0-.354ZM3.75 2.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm0 9.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm8.25.75a.75.75 0 1 0 1.5 0 .75.75 0 0 0-1.5 0Z"></path></svg> Pull requests**.

2. In the **Pull Requests** list, click the pull request you want to merge.

3. Find the ID number of the inactive pull request. This is the sequence of digits right after the pull request's title.

   ![Screenshot of the title of a pull request. The pull request's ID number is outlined in dark orange.](/assets/images/help/pull_requests/pull-request-id-number.png)

4. Open your terminal or Git Bash.

5. Fetch the reference to the pull request based on its ID number. This creates a new branch. Use the pull request ID and the name of the local branch you want to create in the command.

   ```shell
   git fetch origin pull/ID/head:BRANCH_NAME
   ```

6. Switch to the new branch that's based on this pull request:

   ```shell
   [main] $ git switch BRANCH_NAME
   > Switched to a new branch 'BRANCH_NAME'
   ```

7. Make any needed changes to this branch. You can run local tests or merge other branches into the branch.

8. When you're ready, push the new branch:

   ```shell
   [pull-inactive-pull-request] $ git push origin BRANCH_NAME
   > Counting objects: 32, done.
   > Delta compression using up to 8 threads.
   > Compressing objects: 100% (26/26), done.
   > Writing objects: 100% (29/29), 74.94 KiB | 0 bytes/s, done.
   > Total 29 (delta 8), reused 0 (delta 0)
   > To https://github.com/USERNAME/REPOSITORY.git
   >  * [new branch]      BRANCH_NAME -> BRANCH_NAME
   ```

9. Create a new pull request with your new branch.

## Error: Failed to push some refs

The remote `refs/pull/` namespace is *read-only*. If you try to push commits there, you'll see this error:

```shell
! [remote rejected] HEAD -> refs/pull/1/head (deny updating a hidden ref)
error: failed to push some refs to 'git@github.local:USERNAME/REPOSITORY.git'
```

> \[!TIP]
> When you remove or rename a remote reference, calls to `git-remote` do not affect your local `refs/pull/origin/` namespace.