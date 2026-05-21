# Cloning an issue

To quickly create a similar issue, you can clone an existing open issue into the same repository or a different one.

To clone an open issue, you must have triage access to the repository that contains the original issue and to the destination repository. The destination repository must allow blank issues. See [Repository roles for an organization](/en/organizations/managing-user-access-to-your-organizations-repositories/managing-repository-roles/repository-roles-for-an-organization).

When you clone an issue, a new issue is created with the original issue's title, description, assignees, type, labels, milestones, and projects prefilled, as long as those fields exist or are available in the destination repository. Labels and milestones are retained if they are present in the target repository, with labels matching by name and milestones matching by both name and due date. The original issue remains unchanged.

People or teams mentioned in the original issue will not receive notifications about the cloning. The new issue will have its own URL and can be edited before being created. If you attempt to clone an issue to a repository where you do not have triage access, the option will not be available.

## Cloning an open issue

1. On GitHub, navigate to the main page of the repository.

2. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-issue-opened" aria-label="issue-opened" role="img"><path d="M8 9.5a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path><path d="M8 0a8 8 0 1 1 0 16A8 8 0 0 1 8 0ZM1.5 8a6.5 6.5 0 1 0 13 0 6.5 6.5 0 0 0-13 0Z"></path></svg> Issues**.

   ![Screenshot of the main page of a repository. In the horizontal navigation bar, a tab, labeled "Issues," is outlined in dark orange.](/assets/images/help/repository/repo-tabs-issues-global-nav-update.png)

3. In the list of issues, click the issue you'd like to clone.

4. In the right sidebar, click **Clone issue**.

5. In the **Choose a repository** dropdown, select the destination repository. You can choose the same repository or a different one.

6. Edit the prefilled issue details as needed.

7. Click **Create issue**.

## Further reading

* [About issues](/en/issues/tracking-your-work-with-issues/about-issues)