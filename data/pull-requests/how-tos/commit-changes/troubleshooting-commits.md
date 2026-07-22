# Troubleshooting commits

Resolve common commit issues like incorrect user links, missing local commits, and push protection blocks.

## Commits are linked to the wrong user

GitHub links a commit to a user by matching the email address in the commit header to an email address on a GitHub account. If your commits are linked to the wrong user or no user, update your Git email settings and add the email address to your account.

> \[!NOTE]
> If your commits are linked to another user, that does not give them access to your repository.

### Commits are linked to another user

1. Change the email address in your local Git configuration by following [Setting your commit email address](/en/account-and-profile/how-tos/email-preferences/setting-your-commit-email-address#setting-your-commit-email-address-in-git). If you work on multiple machines, change this setting on each one.
2. Add the email address to your account by following [Adding an email address to your GitHub account](/en/account-and-profile/how-tos/email-preferences/adding-an-email-address-to-your-github-account).

Future commits that use the email address will be linked to your account.

### Commits are not linked to any user

To find out why a commit is not linked, inspect the commit on GitHub.

1. On GitHub, navigate to the main page of the repository.
2. On the main page of the repository, above the file list, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-history" aria-label="history" role="img"><path d="m.427 1.927 1.215 1.215a8.002 8.002 0 1 1-1.6 5.685.75.75 0 1 1 1.493-.154 6.5 6.5 0 1 0 1.18-4.458l1.358 1.358A.25.25 0 0 1 3.896 6H.25A.25.25 0 0 1 0 5.75V2.104a.25.25 0 0 1 .427-.177ZM7.75 4a.75.75 0 0 1 .75.75v2.992l2.028.812a.75.75 0 0 1-.557 1.392l-2.5-1A.751.751 0 0 1 7 8.25v-3.5A.75.75 0 0 1 7.75 4Z"></path></svg> commits**.

   ![Screenshot of the main page for a repository. A clock icon and "178 commits" is highlighted with an orange outline.](/assets/images/help/commits/commits-page.png)
3. To navigate to a specific commit, click the commit message for that commit.

   ![Screenshot of a commit in the commit list for a repository. "Update README.md" is highlighted with an orange outline.](/assets/images/help/commits/commit-message-link.png)
4. Hover over the blue <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-question" aria-label="Question mark" role="img"><path d="M0 8a8 8 0 1 1 16 0A8 8 0 0 1 0 8Zm8-6.5a6.5 6.5 0 1 0 0 13 6.5 6.5 0 0 0 0-13ZM6.92 6.085h.001a.749.749 0 1 1-1.342-.67c.169-.339.436-.701.849-.977C6.845 4.16 7.369 4 8 4a2.756 2.756 0 0 1 1.637.525c.503.377.863.965.863 1.725 0 .448-.115.83-.329 1.15-.205.307-.47.513-.692.662-.109.072-.22.138-.313.195l-.006.004a6.24 6.24 0 0 0-.26.16.952.952 0 0 0-.276.245.75.75 0 0 1-1.248-.832c.184-.264.42-.489.692-.661.103-.067.207-.132.313-.195l.007-.004c.1-.061.182-.11.258-.161a.969.969 0 0 0 .277-.245C8.96 6.514 9 6.427 9 6.25a.612.612 0 0 0-.262-.525A1.27 1.27 0 0 0 8 5.5c-.369 0-.595.09-.74.187a1.01 1.01 0 0 0-.34.398ZM9 11a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> to the right of the username.
5. Use the message to decide what to update:
   * **Unrecognized author (with email address):** Add the shown email address to your GitHub account.
   * **Unrecognized author (no email address):** Set your commit email address in Git, then add that address to your GitHub account.
   * **Invalid email:** Set a valid commit email address in Git, then add that address to your GitHub account.

Old commits might not be linked after you update your email settings. See [Setting your commit email address](/en/account-and-profile/how-tos/email-preferences/setting-your-commit-email-address).

## A commit exists on GitHub but not in your local clone

If `git show COMMIT-SHA` returns an error locally but the commit is visible on GitHub, your local clone may be out of date or the commit may no longer be referenced by a branch.

### The local repository is out of date

Fetch information from the remote repository.

```shell
git fetch REMOTE
```

Use `git fetch upstream` for a fork's upstream repository, or `git fetch origin` for the repository you cloned.

### The branch that contained the commit was deleted

If the branch was deleted or force pushed, ask a collaborator who still has the commit locally to push it to a new branch.

```shell
git branch recover-B B
git push upstream B:recover-B
```

Then, fetch the recovered branch.

```shell
git fetch upstream recover-B
```

### Avoid force pushes

Avoid force pushing unless necessary, especially when more than one person can push to the repository. Force pushing rewrites repository history and can disrupt collaborators or corrupt pull requests.

## A commit is blocked by push protection

Push protection blocks commits, uploads, or API requests that contain supported secrets.

### Understanding why push protection has blocked your commit

If push protection blocks your work, GitHub detected a supported secret in your commit or request. Remove the secret before trying again.

### Resolving a push protection block

1. Review the push protection message to identify the secret and where it appears.
2. Remove the secret from the commit, file upload, or API request.
3. Try the push, commit, upload, or request again.
4. If you believe the secret is safe to push, follow the bypass steps for your workflow:
   * [Working with push protection from the command line](/en/code-security/how-tos/secure-your-secrets/work-with-leak-prevention/push-protection-on-the-command-line)
   * [Working with push protection in the GitHub UI](/en/code-security/how-tos/secure-your-secrets/work-with-leak-prevention/push-protection-in-the-github-ui)
   * [Working with push protection from the REST API](/en/code-security/concepts/secret-security/push-protection-from-the-rest-api)

## Further reading

* [Searching commits](/en/search-github/searching-on-github/searching-commits)
* [Push protection](/en/code-security/concepts/secret-security/push-protection)
* [Supported secret scanning patterns](/en/code-security/reference/secret-security/supported-secret-scanning-patterns)