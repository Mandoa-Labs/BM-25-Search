# Merging a pull request with a merge queue

Use merge queues in GitHub to streamline pull request merging, ensure required checks pass, and manage queue operations effectively.

## About merge queues

A merge queue helps merge pull requests into a busy protected branch after required checks pass. See [Managing a merge queue](/en/repositories/configuring-branches-and-merges-in-your-repository/configuring-pull-request-merges/managing-a-merge-queue).

## Adding a pull request to a merge queue

<div class="ghd-tool webui">

> \[!NOTE]
> You can use GitHub CLI to add a pull request to a merge queue. For more information, click the "GitHub CLI" tab at the top of this article.

1. On GitHub, navigate to the main page of the repository.

2. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-git-pull-request" aria-label="git-pull-request" role="img"><path d="M1.5 3.25a2.25 2.25 0 1 1 3 2.122v5.256a2.251 2.251 0 1 1-1.5 0V5.372A2.25 2.25 0 0 1 1.5 3.25Zm5.677-.177L9.573.677A.25.25 0 0 1 10 .854V2.5h1A2.5 2.5 0 0 1 13.5 5v5.628a2.251 2.251 0 1 1-1.5 0V5a1 1 0 0 0-1-1h-1v1.646a.25.25 0 0 1-.427.177L7.177 3.427a.25.25 0 0 1 0-.354ZM3.75 2.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm0 9.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm8.25.75a.75.75 0 1 0 1.5 0 .75.75 0 0 0-1.5 0Z"></path></svg> Pull requests**.

3. In the "Pull Requests" list, click the pull request you want to add to a merge queue.

4. Click **Merge when ready** to add the pull request to the merge queue. Alternatively, if you are an administrator, you can:

   * Directly merge the pull request by checking **Merge without waiting for requirements to be met (bypass branch protections)**, if allowed by branch protection settings, and follow the standard flow.

   ![Screenshot of the merge queue options for a pull request.](/assets/images/help/pull_requests/merge-queue-options.png)

   > \[!NOTE]
   > You can click **Merge when ready** before all requirements pass. GitHub adds the pull request to the queue when requirements are met.

5. Confirm you want to add the pull request to the merge queue by clicking **Confirm merge when ready**.

</div>

<div class="ghd-tool cli">

With GitHub CLI, use the `gh pr merge` command to add a pull request to a merge queue. If you are targeting a branch that requires a merge queue, this command automatically adds the pull request to the queue if required checks have passed. If required checks have not passed, this command enables auto-merge for the pull request. See [`gh pr merge`](https://cli.github.com/manual/gh_pr_merge) in the GitHub CLI manual.

</div>

## Removing a pull request from a merge queue

<div class="ghd-tool cli">

To remove a pull request from a merge queue, you must navigate to the repository's page on GitHub.com. You cannot use GitHub CLI to remove a pull request from a merge queue.

</div>

1. On GitHub, navigate to the main page of the repository.

2. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-git-pull-request" aria-label="git-pull-request" role="img"><path d="M1.5 3.25a2.25 2.25 0 1 1 3 2.122v5.256a2.251 2.251 0 1 1-1.5 0V5.372A2.25 2.25 0 0 1 1.5 3.25Zm5.677-.177L9.573.677A.25.25 0 0 1 10 .854V2.5h1A2.5 2.5 0 0 1 13.5 5v5.628a2.251 2.251 0 1 1-1.5 0V5a1 1 0 0 0-1-1h-1v1.646a.25.25 0 0 1-.427.177L7.177 3.427a.25.25 0 0 1 0-.354ZM3.75 2.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm0 9.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm8.25.75a.75.75 0 1 0 1.5 0 .75.75 0 0 0-1.5 0Z"></path></svg> Pull requests**.

3. In the "Pull Requests" list, click the pull request you want to remove from a merge queue.

4. To remove the pull request from the queue, click **Remove from queue**.

   ![Screenshot of the merge queue message at the bottom of a pull request. The "Remove from queue" button is outlined in dark orange.](/assets/images/help/pull_requests/remove-from-queue-button.png)

Alternatively, you can navigate to the merge queue page for the base branch, click **...** next to the pull request you want to remove, and select **Remove from queue**. For information about getting to the merge queue page for the base branch, see the section below.

## Viewing merge queues

<div class="ghd-tool cli">

You can view the merge queue for a base branch in various places on GitHub. You cannot use GitHub CLI to view a merge queue.

</div>

<div class="ghd-tool webui">

You can view the merge queue for a base branch in various places on GitHub.

</div>

* On the **Branches** page for the repository. We recommend this route if you don't have or don't know about a pull request already in a queue, and if you want to see what's in that queue. See [Viewing branches in your repository](/en/repositories/configuring-branches-and-merges-in-your-repository/managing-branches-in-your-repository/viewing-branches-in-your-repository).

  ![Screenshot of the "Branches" page for a repository. A link, labeled "33 pull requests queued to merge," is outlined in dark orange.](/assets/images/help/pull_requests/merge-queue-branches-page.png)

* On the pull request page, when a merge queue is required for merging, scroll to the bottom of the timeline and click the **merge queue** link.

  ![Screenshot of the merge queue message at the bottom of a pull request. The "merge queue" link is outlined in dark orange.](/assets/images/help/pull_requests/merge-queue-link.png)

* The merge queue view shows the pull requests that are currently in the queue, with your pull requests clearly marked.

  ![Screenshot of the merge queue for a repository.](/assets/images/help/pull_requests/merge-queue-view.png)

## Understanding why your pull request was removed from the merge queue

A pull request can be removed from the merge queue if it no longer meets merge requirements or if a queue check fails.

There are a number of reasons a pull request can be removed from a merge queue:

* Configured CI service is reporting test failures for a merge group
* Timed out awaiting a successful CI result based off the configured timeout setting
* User requesting a removal via the API or merge queue interface
* Branch protection failure that could not automatically be resolved