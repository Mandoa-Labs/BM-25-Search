# Allowing changes to a pull request branch created from a fork

Enable collaboration by allowing repository maintainers to commit changes to pull request branches created from forks in your personal account.

When someone creates a pull request from their fork, they usually decide whether other people can commit to the pull request's compare branch. For greater collaboration, the author can give maintainers of the upstream repository—that is, anyone with push access to the upstream repository—permission to commit to the compare branch. See [Forks](/en/pull-requests/reference/forks).

Pull request authors can set these permissions when they create a pull request from a fork in a personal account. They can also update an existing pull request to let repository maintainers commit to the branch. See [Creating a pull request from a fork](/en/pull-requests/how-tos/create-pull-requests/creating-a-pull-request-from-a-fork).

## Enabling repository maintainer permissions on existing pull requests

1. On GitHub, navigate to the main page of the upstream repository of your pull request.

2. Under the upstream repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-git-pull-request" aria-label="git-pull-request" role="img"><path d="M1.5 3.25a2.25 2.25 0 1 1 3 2.122v5.256a2.251 2.251 0 1 1-1.5 0V5.372A2.25 2.25 0 0 1 1.5 3.25Zm5.677-.177L9.573.677A.25.25 0 0 1 10 .854V2.5h1A2.5 2.5 0 0 1 13.5 5v5.628a2.251 2.251 0 1 1-1.5 0V5a1 1 0 0 0-1-1h-1v1.646a.25.25 0 0 1-.427.177L7.177 3.427a.25.25 0 0 1 0-.354ZM3.75 2.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm0 9.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm8.25.75a.75.75 0 1 0 1.5 0 .75.75 0 0 0-1.5 0Z"></path></svg> Pull requests**.

   ![Screenshot of the main page of a repository. In the horizontal navigation bar, a tab, labeled "Pull requests," is outlined in dark orange.](/assets/images/help/repository/repo-tabs-pull-requests-global-nav-update.png)

3. In the list of pull requests, navigate to the pull request that you'd like to allow commits on.

4. On user-owned forks, if you want to allow anyone with push access to the upstream repository to make changes to your pull request, select **Allow edits from maintainers**.

   > \[!WARNING]
   > If your fork contains GitHub Actions workflows, the option is **Allow edits and access to secrets by maintainers**. Allowing edits on a fork's branch that contains GitHub Actions workflows also allows a maintainer to edit the forked repository's workflows, which can potentially reveal values of secrets and grant access to other branches.

   ![Screenshot of a pull request. On the bottom right, the "Allow edits and access to secrets by maintainers" checkbox is enabled and outlined in orange.](/assets/images/help/pull_requests/allow-edits-and-access-by-maintainers.png)

## Further reading

* [Committing changes to a pull request branch created from a fork](/en/pull-requests/how-tos/commit-changes/committing-changes-to-a-pull-request-branch-created-from-a-fork)