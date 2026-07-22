# Resolving a merge conflict on GitHub

Resolve simple merge conflicts directly on GitHub using the conflict editor or handle complex cases via the command line.

You can resolve simple competing line change conflicts on GitHub. For other conflicts, use the command line. See [Resolving a merge conflict using the command line](/en/pull-requests/how-tos/merge-and-close-pull-requests/resolving-a-merge-conflict-using-the-command-line).

If Copilot cloud agent is enabled for the repository, you can click **Fix with Copilot** in the merge box to have Copilot resolve conflicts automatically. See [Using Copilot cloud agent on GitHub](/en/copilot/how-tos/use-copilot-agents/cloud-agent/use-cloud-agent-on-github#resolving-merge-conflicts).

> \[!WARNING]
> Resolving conflicts on GitHub merges the entire [base branch](/en/get-started/learning-about-github/github-glossary#base-branch) into the [head branch](/en/get-started/learning-about-github/github-glossary#head-branch). If the head branch is the default or protected branch, you may be prompted to create a new head branch. See [About protected branches](/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches).

1. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-git-pull-request" aria-label="git-pull-request" role="img"><path d="M1.5 3.25a2.25 2.25 0 1 1 3 2.122v5.256a2.251 2.251 0 1 1-1.5 0V5.372A2.25 2.25 0 0 1 1.5 3.25Zm5.677-.177L9.573.677A.25.25 0 0 1 10 .854V2.5h1A2.5 2.5 0 0 1 13.5 5v5.628a2.251 2.251 0 1 1-1.5 0V5a1 1 0 0 0-1-1h-1v1.646a.25.25 0 0 1-.427.177L7.177 3.427a.25.25 0 0 1 0-.354ZM3.75 2.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm0 9.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm8.25.75a.75.75 0 1 0 1.5 0 .75.75 0 0 0-1.5 0Z"></path></svg> Pull requests**.

2. In the "Pull Requests" list, click the pull request with a merge conflict that you want to resolve.

3. Near the bottom of your pull request, click **Resolve conflicts**.

   ![Screenshot of a warning that a pull request has a merge conflict. The "Resolve merge conflicts" button is outlined in dark orange.](/assets/images/help/pull_requests/resolve-merge-conflicts-button.png)

   > \[!NOTE]
   > If **Resolve conflicts** is deactivated, resolve the conflict using another Git client or the command line. See [Resolving a merge conflict using the command line](/en/pull-requests/how-tos/merge-and-close-pull-requests/resolving-a-merge-conflict-using-the-command-line).

4. Decide if you want to keep only your branch's changes, keep only the other branch's changes, or make a brand new change, which may incorporate changes from both branches. Delete the conflict markers `<<<<<<<`, `=======`, `>>>>>>>` and make the changes you want in the final merge.

5. If your file has more than one merge conflict, scroll down to the next set of conflict markers and repeat steps four and five to resolve the conflict.

6. After you've resolved all the conflicts in the file, click **Mark as resolved**.

   ![Screenshot of the editor to resolve a merge conflict in a pull request. The "Mark as resolved" button is outlined in dark orange.](/assets/images/help/pull_requests/mark-as-resolved-button.png)

7. If more than one file has a conflict, select the next file you want to edit on the left side of the page under "conflicting files" and repeat steps four through seven until you've resolved all merge conflicts in your pull request.

8. After you've resolved all your merge conflicts, click **Commit merge**. This merges the entire base branch into your head branch.

   ![Screenshot of the editor to resolve a merge conflict in a pull request. The "Commit merge" button is outlined in dark orange.](/assets/images/help/pull_requests/merge-conflict-commit-changes.png)

9. If prompted, review the branch that you are committing to. You can update the head branch or, if available, create a new branch for the pull request. If the head branch is protected, you must create a new branch.

   Click **Create branch and update my pull request** or **I understand, continue updating BRANCH**.

10. To merge your pull request, click **Merge pull request**. See [Merging a pull request](/en/pull-requests/how-tos/merge-and-close-pull-requests/merging-a-pull-request).

## Further reading

* [Pull request merges](/en/pull-requests/reference/pull-request-merges)