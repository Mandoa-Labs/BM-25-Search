# Changing the base branch of a pull request

Modify the base branch of an open pull request to compare changes against a different branch and ensure accurate updates.

> \[!WARNING]
> When you change the base branch of your pull request, some commits may be removed from the timeline. Review comments may also become outdated because the line of code that the comment referenced may no longer be part of the changes in the pull request.

1. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-git-pull-request" aria-label="git-pull-request" role="img"><path d="M1.5 3.25a2.25 2.25 0 1 1 3 2.122v5.256a2.251 2.251 0 1 1-1.5 0V5.372A2.25 2.25 0 0 1 1.5 3.25Zm5.677-.177L9.573.677A.25.25 0 0 1 10 .854V2.5h1A2.5 2.5 0 0 1 13.5 5v5.628a2.251 2.251 0 1 1-1.5 0V5a1 1 0 0 0-1-1h-1v1.646a.25.25 0 0 1-.427.177L7.177 3.427a.25.25 0 0 1 0-.354ZM3.75 2.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm0 9.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm8.25.75a.75.75 0 1 0 1.5 0 .75.75 0 0 0-1.5 0Z"></path></svg> Pull requests**.

2. In the "Pull Requests" list, click the pull request you want to modify.

3. Next to the pull request title, click **Edit title** <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-pencil" aria-label="Edit title" role="img"><path d="M11.013 1.427a1.75 1.75 0 0 1 2.474 0l1.086 1.086a1.75 1.75 0 0 1 0 2.474l-8.61 8.61c-.21.21-.47.364-.756.445l-3.251.93a.75.75 0 0 1-.927-.928l.929-3.25c.081-.286.235-.547.445-.758l8.61-8.61Zm.176 4.823L9.75 4.81l-6.286 6.287a.253.253 0 0 0-.064.108l-.558 1.953 1.953-.558a.253.253 0 0 0 .108-.064Zm1.238-3.763a.25.25 0 0 0-.354 0L10.811 3.75l1.439 1.44 1.263-1.263a.25.25 0 0 0 0-.354Z"></path></svg>.

4. In the base branch drop-down menu, select the base branch you'd like to [compare changes against](/en/pull-requests/how-tos/commit-changes/comparing-commits#comparing-branches).

   ![Screenshot of a pull request title. The dropdown to change the base branch is outlined in dark orange.](/assets/images/help/pull_requests/pull-request-edit-base-branch.png)

5. Read the information about changing the base branch and click **Change base**.

> \[!TIP]
> When you open a pull request, GitHub sets the base to the commit that branch references. If the branch is updated in the future, GitHub does not update the base branch's commit.

## Further reading

* [Creating a pull request](/en/pull-requests/how-tos/create-pull-requests/creating-a-pull-request)
* [Pull requests](/en/pull-requests/reference/pull-requests)
* [Reviewing proposed changes in a pull request](/en/pull-requests/how-tos/review-pull-requests/reviewing-proposed-changes-in-a-pull-request)