# Uploading CodeQL analysis results to GitHub

You can use the CodeQL CLI to upload CodeQL analysis results to GitHub.

After analyzing a CodeQL database using the CodeQL CLI, you will have a SARIF file that contains the results. You can then use the CodeQL CLI to upload results to GitHub.

If you used a method other than the CodeQL CLI to generate results, you can use other upload methods. For more information, see [Uploading a SARIF file to GitHub](/en/code-security/code-scanning/integrating-with-code-scanning/uploading-a-sarif-file-to-github).

## Generating a token for authentication with GitHub

Before you can upload your results to GitHub, you will first need to generate a personal access token. See [Managing your personal access tokens](/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token).

* **Personal access token (classic)** requires "Code scanning alerts" **Read and write** access for the required repositories.
* **Fine-grained personal access token** requires "repo" **security\_events** access.

If you have installed the CodeQL CLI in a third-party CI system, you can also use a GitHub App to upload results to GitHub. See [Using code scanning with your existing CI system](/en/code-security/code-scanning/integrating-with-code-scanning/using-code-scanning-with-your-existing-ci-system#generating-a-token-for-authentication-with-github).

## Uploading results to GitHub

1. Check that the SARIF properties have the supported size for upload and that the file is compatible with code scanning. For more information, see [SARIF support for code scanning](/en/code-security/code-scanning/integrating-with-code-scanning/sarif-support-for-code-scanning#file-compatibility).

2. Determine the best way to pass the GitHub App or personal access token you created in the previous section to the CodeQL CLI. We recommend that you review your CI system's guidance on the secure use of a secret store. The CodeQL CLI supports:

   * Interfacing with a secret store using the `--github-auth-stdin` option (recommended).
   * Saving the secret in the environment variable `GITHUB_TOKEN` and running the CLI without including the `--github-auth-stdin` option.
   * For testing purposes you can pass the `--github-auth-stdin` command-line option and supply a temporary token via standard input.

3. When you have decided on the most secure and reliable method for your configuration, run `codeql github upload-results` on each SARIF results file and include `--github-auth-stdin` unless the token is available in the environment variable `GITHUB_TOKEN`.

   ```shell
   # GitHub App or personal access token available from a secret store
   <call-to-retrieve-secret> | codeql github upload-results \
       --repository=<repository-name> \
       --ref=<ref> --commit=<commit> \
       --sarif=<file> --github-auth-stdin

   # GitHub App or personal access token available in GITHUB_TOKEN
   codeql github upload-results \
       --repository=<repository-name> \
       --ref=<ref> --commit=<commit> \
       --sarif=<file> 
   ```

| Option                                                                     |                                                                                                                                                                                                            Required                                                                                                                                                                                                            | Usage                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| -------------------------------------------------------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <code><span style="white-space: nowrap;">--repository</span></code>        |                                                     <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Required" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg>                                                    | Specify the *OWNER/NAME* of the repository to upload data to. The owner must be an organization within an enterprise, or on a GitHub Team plan, with GitHub Code Security enabled for the repository, unless the repository is public. For more information, see [Managing security and analysis settings for your repository](/en/repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-security-and-analysis-settings-for-your-repository). |
| <code><span style="white-space: nowrap;">--ref</span></code>               |                                                     <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Required" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg>                                                    | Specify the name of the `ref` you checked out and analyzed so that the results can be matched to the correct code. For a branch use: `refs/heads/BRANCH-NAME`, for the head commit of a pull request use `refs/pull/NUMBER/head`, or for the GitHub-generated merge commit of a pull request use `refs/pull/NUMBER/merge`.                                                                                                                                                                          |
| <code><span style="white-space: nowrap;">--commit</span></code>            |                                                     <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Required" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg>                                                    | Specify the full SHA of the commit you analyzed.                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| <code><span style="white-space: nowrap;">--sarif</span></code>             |                                                     <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-check" aria-label="Required" role="img"><path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path></svg>                                                    | Specify the SARIF file to load.                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|                                                                            |                                                                                                                                                                                                                                                                                                                                                                                                                                |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| <code><span style="white-space: nowrap;">--github-auth-stdin</span></code> | <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-x" aria-label="Optional" role="img"><path d="M3.72 3.72a.75.75 0 0 1 1.06 0L8 6.94l3.22-3.22a.749.749 0 0 1 1.275.326.749.749 0 0 1-.215.734L9.06 8l3.22 3.22a.749.749 0 0 1-.326 1.275.749.749 0 0 1-.734-.215L8 9.06l-3.22 3.22a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042L6.94 8 3.72 4.78a.75.75 0 0 1 0-1.06Z"></path></svg> | Pass the CLI the GitHub App or personal access token created for authentication with GitHub's REST API from your secret store via standard input. This is not needed if the command has access to a `GITHUB_TOKEN` environment variable set with this token.                                                                                                                                                                                                                                        |

For more information, see [github upload-results](/en/code-security/codeql-cli/codeql-cli-manual/github-upload-results).

> \[!NOTE]
> If you analyzed more than one CodeQL database for a single commit, you must have specified a SARIF category for each set of results generated by this command. When you upload the results to GitHub, code scanning uses this category to store the results for each language separately. If you forget to do this, each upload overwrites the previous results. For more information, see [Analyzing your code with CodeQL queries](/en/code-security/codeql-cli/getting-started-with-the-codeql-cli/analyzing-your-code-with-codeql-queries#running-codeql-database-analyze).

### Basic example of uploading results to GitHub

The following example uploads results from the SARIF file `temp/example-repo-js.sarif` to the repository `my-org/example-repo`. It tells the code scanning API that the results are for the commit `deb275d2d5fe9a522a0b7bd8b6b6a1c939552718` on the `main` branch. The example assumes that the GitHub App or personal access token created for authentication with GitHub's REST API uses the `GITHUB_TOKEN` environment variable.

```shell
codeql github upload-results \
    --repository=my-org/example-repo \
    --ref=refs/heads/main --commit=deb275d2d5fe9a522a0b7bd8b6b6a1c939552718 \
    --sarif=/temp/example-repo-js.sarif 
```

There is no output from this command unless the upload was unsuccessful. The command prompt returns when the upload is complete and data processing has begun. On smaller codebases, you should be able to explore the code scanning alerts in GitHub shortly afterward. You can see alerts directly in the pull request or on the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab for branches, depending on the code you checked out.

## Uploading diagnostic information to GitHub if the analysis fails

When CodeQL CLI finishes analyzing a database successfully, it gathers diagnostic information such as file coverage, warnings, and errors, and includes it in the SARIF file with the results. When you upload the SARIF file to GitHub the diagnostic information is displayed on the code scanning tool status page for the repository to make it easy to see how well CodeQL is working and debug any problems. For more information, see [Use the tool status page for code scanning](/en/code-security/code-scanning/managing-your-code-scanning-configuration/about-the-tool-status-page).

However, if `codeql database analyze` fails for any reason there is no SARIF file to upload to GitHub and no diagnostic information to show on the code scanning tool status page for the repository. This makes it difficult for users to troubleshoot analysis unless they have access to log files in your CI system.

We recommend that you configure your CI workflow to export and upload diagnostic information to GitHub when an analysis fails. You can do this using the following simple commands to export diagnostic information and upload it to GitHub.

### Exporting diagnostic information if the analysis fails

You can create a SARIF file for the failed analysis using [database export-diagnostics](/en/code-security/codeql-cli/codeql-cli-manual/database-export-diagnostics), for example:

```shell
$ codeql database export-diagnostics codeql-dbs/example-repo \
    --sarif-category=javascript-typescript --format=sarif-latest \
    --output=/temp/example-repo-js.sarif
```

This SARIF file will contain diagnostic information for the failed analysis, including any file coverage information, warnings, and errors generated during the analysis.

### Uploading diagnostic information if the analysis fails

You can make this diagnostic information available on the tool status page by uploading the SARIF file to GitHub using [github upload-results](/en/code-security/codeql-cli/codeql-cli-manual/github-upload-results), for example:

```shell
codeql github upload-results \
    --repository=my-org/example-repo \
    --ref=refs/heads/main --commit=deb275d2d5fe9a522a0b7bd8b6b6a1c939552718 \
    --sarif=/temp/example-repo-js.sarif 
```

This is the same as the process for uploading SARIF files from successful analyses.