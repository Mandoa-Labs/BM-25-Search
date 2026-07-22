# Changing a commit message

Amend unclear, incorrect, or sensitive commit messages locally and push updated commits to GitHub, including steps for editing recent or older commits.

## Rewriting the most recent commit message

Changing a commit message creates a new commit ID. If the commit has already been pushed, you must force push the rewritten history.

## Commit has not been pushed online

If the commit only exists in your local repository, amend the commit message locally.

1. On the command line, navigate to the repository that contains the commit you want to amend.

2. Type `git commit --amend` and press **Enter**.

3. In your text editor, edit the commit message, and save the commit.
   * To add a co-author, add a trailer to the commit. See [Creating a commit with multiple authors or on behalf of an organization](/en/pull-requests/how-tos/commit-changes/creating-a-commit-with-multiple-authors).

   * To create commits on behalf of your organization, add a trailer to the commit. See [Creating a commit with multiple authors or on behalf of an organization](/en/pull-requests/how-tos/commit-changes/creating-a-commit-with-multiple-authors#creating-a-commit-on-behalf-of-an-organization).

4. Push the commit to GitHub.com.

## Amending older or multiple commit messages

If you have already pushed the commit, use caution before rewriting history. Force pushing can disrupt collaborators who have based work on the old commits.

### Changing the message of the most recently pushed commit

1. Follow the steps in [Commit has not been pushed online](#commit-has-not-been-pushed-online) to amend the commit message.
2. Force push over the old commit.

   ```shell
   git push --force-with-lease origin EXAMPLE-BRANCH
   ```

### Changing the message of older or multiple commit messages

Use interactive rebase to change older or multiple commit messages.

1. On the command line, navigate to the repository that contains the commits you want to amend.

2. Start an interactive rebase for the last `n` commits.

   ```shell
   git rebase -i HEAD~n
   ```

3. In the commit list, replace `pick` with `reword` before each commit message you want to change.

   ```shell
   pick e499d89 Delete CNAME
   reword 0c39034 Better README
   reword f7fde4a Change the commit message
   ```

4. Save and close the commit list file.

5. In each commit message file that opens, enter the new message, then save and close the file.

6. Force push the rewritten history.

   ```shell
   git push --force-with-lease origin EXAMPLE-BRANCH
   ```

See [Interactive mode](https://git-scm.com/docs/git-rebase#_interactive_mode) in the Git manual.

> \[!WARNING]
> If a commit message included sensitive information, force pushing an amended commit might not remove the original commit from GitHub. Contact us through the [GitHub Support portal](https://support.github.com) with the old commit ID to have it purged from the remote repository.

## Further reading

* [Signing commits](/en/authentication/managing-commit-signature-verification/signing-commits)