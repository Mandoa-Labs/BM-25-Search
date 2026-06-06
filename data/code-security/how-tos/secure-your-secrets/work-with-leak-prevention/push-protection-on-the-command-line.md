# Working with push protection from the command line

Learn your options for unblocking your push from the command line to GitHub if secret scanning detects a secret in your changes.

## Resolving a blocked push

To resolve a blocked push, you must remove the secret from all of the commits it appears in.

* If the secret was introduced by your latest commit, see [Removing a secret introduced by the latest commit on your branch](#removing-a-secret-introduced-by-the-latest-commit-on-your-branch).
* If the secret appears in earlier commits, see [Removing a secret introduced by an earlier commit on your branch](#removing-a-secret-introduced-by-an-earlier-commit-on-your-branch).

### Removing a secret introduced by the latest commit on your branch

1. Remove the secret from your code.
2. To commit the changes, run `git commit --amend --all`. This updates the original commit that introduced the secret instead of creating a new commit.
3. Push your changes with `git push`.

### Removing a secret introduced by an earlier commit on your branch

1. Examine the error message that displayed when you tried to push your branch, which lists all of the commits that contain the secret.

   ```text
   remote:   —— GitHub Personal Access Token ——————————————————————
   remote:    locations:
   remote:      - commit: 8728dbe67
   remote:        path: README.md:4
   remote:      - commit: 03d69e5d3
   remote:        path: README.md:4
   remote:      - commit: 8053f7b27
   remote:        path: README.md:4
   ```

2. Next, run `git log` to see a full history of all the commits on your branch, along with their corresponding timestamps.

   ```text
   test-repo (test-branch)]$ git log
   commit 8053f7b27 (HEAD -> main)
   Author: Octocat <1000+octocat@users.noreply.github.com
   Date:   Tue Jan 30 13:03:37 2024 +0100

     my fourth commit message

   commit 03d69e5d3
   Author: Octocat <1000+octocat@users.noreply.github.com>
   Date:   Tue Jan 30 13:02:59 2024 +0100

     my third commit message

   commit 8728dbe67
   Author: Octocat <1000+octocat@users.noreply.github.com
   Date:   Tue Jan 30 13:01:36 2024 +0100

     my second commit message

   commit 6057cbe51
   Author: Octocat <1000+octocat@users.noreply.github.com
   Date:   Tue Jan 30 12:58:24 2024 +0100

     my first commit message

   ```

3. Focusing only on the commits that contain the secret, use the output of `git log` to identify which commit comes *earliest* in your Git history.
   * In the example, commit `8728dbe67` was the first commit to contain the secret.

4. Start an interactive rebase with `git rebase -i <COMMIT-ID>~1`.
   * For `<COMMIT-ID>`, use the commit identified in step 3. For example, `git rebase -i 8728dbe67~1`.

5. In the editor, choose to edit the commit identified in step 3 by changing `pick` to `edit` on the first line of the text.

   ```text
   edit 8728dbe67 my second commit message
   pick 03d69e5d3 my third commit message
   pick 8053f7b27 my fourth commit message
   ```

6. Save and close the editor to start the interactive rebase.

7. Remove the secret from your code.

8. Add your changes to the staging area using `git add .`.

   > \[!NOTE] The full command is `git add .`:
   >
   > * There is a space between `add` and `.`.
   > * The period following the space is part of the command.

9. Commit your changes using `git commit --amend`.

10. Run `git rebase --continue` to finish the rebase.

11. Push your changes with `git push`.

## Bypassing push protection

> \[!NOTE] If you don't see the option to bypass a block, you should remove the secret from the commit, or submit a request for "bypass privileges" in order to push the blocked secret. See [Requesting bypass privileges](#requesting-bypass-privileges).

1. Visit the URL returned by GitHub when your push was blocked, **as the same user that performed the push**. If a different user attempts to visit this URL, they will receive a `404` error.

2. Choose the option that best describes why you should be able to push the secret.
   * If the secret is only used in tests and poses no threat, click **It's used in tests**.

   * If the detected string is not a secret, click **It's a false positive**.

   * If the secret is real but you intend to fix it later, click **I'll fix it later**.
   > \[!NOTE]
   > You are required to specify a reason for bypassing push protection if the repository has secret scanning enabled.
   >
   > When pushing to a *public* repository that doesn't have secret scanning enabled, you are still protected from accidentally pushing secrets thanks to *push protection for users*, which is on by default for your user account.
   >
   > With push protection for users, GitHub will automatically block pushes to public repositories if these pushes contain supported secrets, but you won't need to specify a reason for allowing the secret, and GitHub won't generate an alert. For more information, see [Managing push protection for users](/en/code-security/secret-scanning/working-with-secret-scanning-and-push-protection/push-protection-for-users).

3. Click **Allow me to push this secret**.

4. Reattempt the push on the command line within three hours. If you have not pushed within three hours, you will need to repeat this process.

## Requesting bypass privileges

1. Visit the URL returned by GitHub when your push was blocked, **as the same user that performed the push**. If a different user attempts to visit this URL, they will receive a `404` error.
2. Under "Or request bypass privileges", add a comment. For example, you might explain why you believe the secret is safe to push, or provide context about the request to bypass the block.
3. Click **Submit request**.
4. Check your email notifications for a response to your request. Once your request has been reviewed, you will receive an email notifying you of the decision.

   * If your request is **approved**, you can push the commit (or commits) containing the secret to the repository, as well as any future commits that contain the same secret.
   * If your request is **denied**, you need to remove the secret from all commits before pushing again. For information on how to remove a blocked secret, see [Resolving a blocked push](#resolving-a-blocked-push).

## Further reading

* [Working with push protection in the GitHub UI](/en/code-security/secret-scanning/working-with-secret-scanning-and-push-protection/working-with-push-protection-in-the-github-ui)
* [Working with push protection from the REST API](/en/code-security/secret-scanning/working-with-secret-scanning-and-push-protection/working-with-push-protection-from-the-rest-api)