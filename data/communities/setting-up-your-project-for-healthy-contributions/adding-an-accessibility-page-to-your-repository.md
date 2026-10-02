# Adding an accessibility page to your repository

Add an ACCESSIBILITY.md file to make your project's accessibility information easy to find and give people a clear way to report barriers.

When a repository contains an `ACCESSIBILITY.md` file, GitHub displays an **Accessibility** tab on the repository overview and links to the page from the repository's **About** section.

GitHub looks for the file in the `.github` directory, the repository root, and the `docs` directory, in that order. If the repository does not contain an accessibility page, it can inherit one from a repository named `.github` that is owned by the organization.

An accessibility page can describe your project's accessibility priorities, supported environments, known barriers, contributor expectations, reporting process, ownership, and maintenance.

## Adding an accessibility page from Community Standards

For a public repository, you can start with the accessibility page template.

1. On GitHub, navigate to the main page of the repository.

2. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-graph" aria-label="graph" role="img"><path d="M1.5 1.75V13.5h13.75a.75.75 0 0 1 0 1.5H.75a.75.75 0 0 1-.75-.75V1.75a.75.75 0 0 1 1.5 0Zm14.28 2.53-5.25 5.25a.75.75 0 0 1-1.06 0L7 7.06 4.28 9.78a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042l3.25-3.25a.75.75 0 0 1 1.06 0L10 7.94l4.72-4.72a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042Z"></path></svg> Insights**.

   ![Screenshot of the main page of a repository. In the horizontal navigation bar, a tab, labeled with a graph icon and "Insights," is outlined in orange.](/assets/images/help/repository/repo-nav-insights-tab.png)

3. In the left sidebar, click **Community Standards**.

4. Under "Additional community file," find "Accessibility," then click **Add** or **Propose**.

5. Replace the instructions in the template with accessibility-related information for your project. The instructions are stored in comments and do not appear when GitHub renders the file.

6. Click **Commit changes...**

7. In the "Commit message" field, type a short, meaningful commit message that describes the change you made to the file. You can attribute the commit to more than one author in the commit message. For more information, see [Creating a commit with multiple authors or on behalf of an organization](/en/pull-requests/how-tos/commit-changes/creating-a-commit-with-multiple-authors).

8. Below the commit message fields, decide whether to add your commit to the current branch or to a new branch. If your current branch is the default branch, you should choose to create a new branch for your commit and then create a pull request. For more information, see [Creating a pull request](/en/pull-requests/how-tos/create-pull-requests/creating-a-pull-request).

   ![Screenshot of a GitHub pull request showing a radio button to commit directly to the main branch or to create a new branch. New branch is selected.](/assets/images/help/repository/choose-commit-branch.png)

9. Click **Commit changes** or **Propose changes**.

## Creating an accessibility page manually

1. On GitHub, navigate to the main page of the repository.

2. Above the list of files, select the **Add file** <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-triangle-down" aria-label="The downwards-facing triangle icon" role="img"><path d="m4.427 7.427 3.396 3.396a.25.25 0 0 0 .354 0l3.396-3.396A.25.25 0 0 0 11.396 7H4.604a.25.25 0 0 0-.177.427Z"></path></svg> dropdown menu, then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-plus" aria-label="plus" role="img"><path d="M7.75 2a.75.75 0 0 1 .75.75V7h4.25a.75.75 0 0 1 0 1.5H8.5v4.25a.75.75 0 0 1-1.5 0V8.5H2.75a.75.75 0 0 1 0-1.5H7V2.75A.75.75 0 0 1 7.75 2Z"></path></svg> Create new file**.

   Alternatively, you can click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-plus" aria-label="The plus sign icon" role="img"><path d="M7.75 2a.75.75 0 0 1 .75.75V7h4.25a.75.75 0 0 1 0 1.5H8.5v4.25a.75.75 0 0 1-1.5 0V8.5H2.75a.75.75 0 0 1 0-1.5H7V2.75A.75.75 0 0 1 7.75 2Z"></path></svg> in the file tree view on the left.

   ![Screenshot of the main page of a repository highlighting both the "Add file" and the "plus sign" icon, described above, with an orange outline.](/assets/images/help/repository/add-file-buttons.png)

3. In the file name field, type *ACCESSIBILITY.md*. To store the file in the `.github` or `docs` directory, type *.github/ACCESSIBILITY.md* or *docs/ACCESSIBILITY.md*.

4. On the **Edit new file** tab, add accessibility-related information.

5. Click **Commit changes...**

6. In the "Commit message" field, type a short, meaningful commit message that describes the change you made to the file. You can attribute the commit to more than one author in the commit message. For more information, see [Creating a commit with multiple authors or on behalf of an organization](/en/pull-requests/how-tos/commit-changes/creating-a-commit-with-multiple-authors).

7. If you have more than one email address associated with your account on GitHub, click the email address drop-down menu and select the email address to use as the Git author email address. Only verified email addresses appear in this drop-down menu. If you enabled email address privacy, then a no-reply will be the default commit author email address. For more information about the exact form the no-reply email address can take, see [Setting your commit email address](/en/account-and-profile/how-tos/email-preferences/setting-your-commit-email-address).

   ![Screenshot of a GitHub pull request showing a dropdown menu with options to choose the commit author email address. octocat@github.com is selected.](/assets/images/help/repository/choose-commit-email-address.png)

8. Below the commit message fields, decide whether to add your commit to the current branch or to a new branch. If your current branch is the default branch, you should choose to create a new branch for your commit and then create a pull request. For more information, see [Creating a pull request](/en/pull-requests/how-tos/create-pull-requests/creating-a-pull-request).

   ![Screenshot of a GitHub pull request showing a radio button to commit directly to the main branch or to create a new branch. New branch is selected.](/assets/images/help/repository/choose-commit-branch.png)

9. Click **Commit changes** or **Propose changes**.