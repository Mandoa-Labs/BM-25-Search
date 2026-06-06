# Excluding folders and files from secret scanning

You can customize secret scanning to automatically close alerts for secrets found in specific directories or files by configuring a secret_scanning.yml file in your repository.

You may have a reason to commit a secret to a repository, such as when you want to provide a fake secret in documentation, or in an example application. In these scenarios, you can quickly dismiss the alert and document the reasons. However, there may be cases where you want to ignore a directory entirely to avoid creating false positive alerts at scale. For example, you might have a monolithic application with several integrations containing a file of dummy keys that could set off numerous false alerts to triage.

You can configure a `secret_scanning.yml` file to automatically close alerts found in specific directories from secret scanning, and exclude these directories included in push protection. These alerts are closed as "ignored by configuration".

## Excluding directories from secret scanning alerts for users

1. On GitHub, navigate to the main page of the repository.
2. Above the list of files, select the **Add file** <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-triangle-down" aria-label="The downwards-facing triangle icon" role="img"><path d="m4.427 7.427 3.396 3.396a.25.25 0 0 0 .354 0l3.396-3.396A.25.25 0 0 0 11.396 7H4.604a.25.25 0 0 0-.177.427Z"></path></svg> dropdown menu, then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-plus" aria-label="plus" role="img"><path d="M7.75 2a.75.75 0 0 1 .75.75V7h4.25a.75.75 0 0 1 0 1.5H8.5v4.25a.75.75 0 0 1-1.5 0V8.5H2.75a.75.75 0 0 1 0-1.5H7V2.75A.75.75 0 0 1 7.75 2Z"></path></svg> Create new file**.

   Alternatively, you can click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-plus" aria-label="The plus sign icon" role="img"><path d="M7.75 2a.75.75 0 0 1 .75.75V7h4.25a.75.75 0 0 1 0 1.5H8.5v4.25a.75.75 0 0 1-1.5 0V8.5H2.75a.75.75 0 0 1 0-1.5H7V2.75A.75.75 0 0 1 7.75 2Z"></path></svg> in the file tree view on the left.

   ![Screenshot of the main page of a repository highlighting both the "Add file" and the "plus sign" icon, described above, with an orange outline.](/assets/images/help/repository/add-file-buttons.png)
3. In the file name field, enter ".github/secret\_scanning.yml".
4. Under **Edit new file**, type `paths-ignore:` followed by the paths you want to exclude from secret scanning.

   ```yaml copy
   paths-ignore:
     - "docs/**"
   ```

   This tells secret scanning to automatically close alerts for everything in the `docs` directory. You can use this example file as a template to add the files and folders you’d like to exclude from your own repositories.

   You can also use special characters, such as `*` to filter paths. For more information about filter patterns, see [Workflow syntax for GitHub Actions](/en/actions/reference/workflow-syntax-for-github-actions#filter-pattern-cheat-sheet).

   ```yaml copy
   paths-ignore:
     - "foo/bar/*.js"
   ```

   > \[!NOTE]
   >
   > * If there are more than 1,000 entries in `paths-ignore`, secret scanning will only exclude the first 1,000 directories from scans.
   > * If `secret_scanning.yml` is larger than 1 MB, secret scanning will ignore the entire file.

## Verifying that the folder is excluded from secret scanning

1. Open a file in a directory that you have excluded from secret scanning
2. Paste a pre-invalidated secret, or a test secret.
3. Commit the change.
4. On GitHub, navigate to the main page of the repository.
5. Under the repository name, click the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab. If you cannot see the "<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality" tab, select the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="kebab-horizontal" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>** dropdown menu, and then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality**. There should be no new open alerts for the secret you just introduced into the file.

## Best practices

Best practices include:

* Minimizing the number of directories excluded and being as precise as possible when defining exclusions. This ensures that the instructions are as clear as possible, and that exclusions work as intended.
* Explaining why a particular file or folder is excluded in a comment in the `secret_scanning.yml` file. As with regular code, using comments clarifies your intention, making it easier for others to understand the desired behavior.
* Reviewing the `secret_scanning.yml` file on a regular basis. Some exclusions may no longer apply with time, and it is good practice to keep the file clean and current. The use of comments, as advised above, can help with this.
* Informing the security team what files and folders you've excluded, and why. Good communication is vital in ensuring that everyone is on the same page, and understands why specific folders or files are excluded.