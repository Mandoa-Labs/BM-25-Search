# CodeQL CLI

You can use the CodeQL CLI to run CodeQL processes locally on software projects or to generate code scanning results for upload to GitHub.

Software developers and security researchers can secure their code
using CodeQL analysis. For more information about CodeQL, see [Code scanning with CodeQL](/en/code-security/code-scanning/introduction-to-code-scanning/about-code-scanning-with-codeql#about-codeql).

The CodeQL CLI is a standalone, command-line tool that you can use to analyze code. Its main purpose is to generate a database representation of a codebase, a CodeQL database. Once the database is ready, you can query it interactively, or run a suite of queries to generate a set of results in SARIF format and upload the results to GitHub.

You can use the CodeQL CLI to:

* Run CodeQL analyses using queries provided by GitHub engineers and the open source community
* Generate code scanning alerts that you can upload to display in GitHub
* Create CodeQL databases to use in the CodeQL for Visual Studio Code extension.
* Develop and test custom CodeQL queries to use in your own analyses

The CodeQL CLI can analyze:

* Dynamic languages, for example, JavaScript and Python.
* Compiled languages, for example, C/C++, C#, Go, Java, Kotlin, Rust, and Swift
* Codebases written in a mixture of languages.

## About using the CodeQL CLI for code scanning

You can use the CodeQL CLI to run code scanning on code that you're processing in a third-party continuous integration (CI) system. Code scanning is a feature that you use to analyze the code in a GitHub repository to find security vulnerabilities and coding errors. Any problems identified by the analysis are shown in your repository. For an overview of using code scanning with external CI systems, see [Using code scanning with your existing CI system](/en/code-security/code-scanning/integrating-with-code-scanning/using-code-scanning-with-your-existing-ci-system). For recommended specifications (RAM, CPU cores, and disk) for running CodeQL analysis, see [Recommended hardware resources for running CodeQL](/en/code-security/code-scanning/creating-an-advanced-setup-for-code-scanning/recommended-hardware-resources-for-running-codeql).

Alternatively, you can use GitHub Actions or Azure DevOps pipelines to scan code using the CodeQL CLI. For more information, see [Configuring default setup for code scanning](/en/code-security/code-scanning/enabling-code-scanning/configuring-default-setup-for-code-scanning) or [Configure GitHub Advanced Security for Azure DevOps](https://learn.microsoft.com/en-us/azure/devops/repos/security/configure-github-advanced-security-features) in Microsoft Learn.

For an overview of all the options for using CodeQL analysis for code scanning, see [Code scanning with CodeQL](/en/code-security/code-scanning/introduction-to-code-scanning/about-code-scanning-with-codeql).

> \[!NOTE]
>
> * The CodeQL CLI is free to use on public repositories. The CodeQL CLI is also available in private repositories owned by organizations that use GitHub Team or GitHub Enterprise Cloud and have a license for GitHub Code Security. For information, see [GitHub CodeQL Terms and Conditions](https://securitylab.github.com/tools/codeql/license) and [CodeQL CLI](https://codeql.github.com/docs/codeql-cli/).
> * The CodeQL CLI is currently not compatible with non-glibc Linux distributions such as (musl-based) Alpine Linux.

## About generating code scanning results with the CodeQL CLI

If you choose to run the CodeQL CLI directly, you first have to install the CodeQL CLI locally. If you are planning to use the CodeQL CLI with an external CI system, you need to make the CodeQL CLI available to servers in your CI system.

Once the CodeQL CLI is set up, you can use three different commands to generate results and upload them to GitHub:

1. `database create` to create a CodeQL database to represent the hierarchical structure of each supported programming language in the repository. For more information, see [Preparing your code for CodeQL analysis](/en/code-security/codeql-cli/getting-started-with-the-codeql-cli/preparing-your-code-for-codeql-analysis).
2. `database analyze` to run queries to analyze each CodeQL database and summarize the results in a SARIF file. For more information, see [Analyzing your code with CodeQL queries](/en/code-security/codeql-cli/getting-started-with-the-codeql-cli/analyzing-your-code-with-codeql-queries).
3. `github upload-results` to upload the resulting SARIF files to GitHub where the results are matched to a branch or pull request and displayed as code scanning alerts. For more information, see [Uploading CodeQL analysis results to GitHub](/en/code-security/codeql-cli/getting-started-with-the-codeql-cli/uploading-codeql-analysis-results-to-github).

> \[!NOTE]
> Uploading SARIF data to display as code scanning results in GitHub is supported for organization-owned repositories with GitHub Code Security enabled, and public repositories on GitHub.com. For more information, see [Managing security and analysis settings for your repository](/en/repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-security-and-analysis-settings-for-your-repository).

### Example CI configuration for CodeQL analysis

This is an example of the full series of commands for the CodeQL CLI that you might use to analyze a codebase with two supported languages and then upload the results to GitHub.

```shell
# Create CodeQL databases for Java and Python in the 'codeql-dbs' directory
# Call the normal build script for the codebase: 'myBuildScript'

codeql database create codeql-dbs --source-root=src \
    --db-cluster --language=java,python --command=./myBuildScript

# Analyze the CodeQL database for Java, 'codeql-dbs/java'
# Tag the data as 'java' results and store in: 'java-results.sarif'

codeql database analyze codeql-dbs/java java-code-scanning.qls \
    --format=sarif-latest --sarif-category=java --output=java-results.sarif

# Analyze the CodeQL database for Python, 'codeql-dbs/python'
# Tag the data as 'python' results and store in: 'python-results.sarif'

codeql database analyze codeql-dbs/python python-code-scanning.qls \
    --format=sarif-latest --sarif-category=python --output=python-results.sarif

# Upload the SARIF file with the Java results: 'java-results.sarif'
# The GitHub App or personal access token created for authentication
# with GitHub's REST API is available in the `GITHUB_TOKEN` environment variable.

codeql github upload-results \
    --repository=my-org/example-repo \
    --ref=refs/heads/main --commit=deb275d2d5fe9a522a0b7bd8b6b6a1c939552718 \
    --sarif=java-results.sarif

# Upload the SARIF file with the Python results: 'python-results.sarif'

codeql github upload-results \
    --repository=my-org/example-repo \
    --ref=refs/heads/main --commit=deb275d2d5fe9a522a0b7bd8b6b6a1c939552718 \
    --sarif=python-results.sarif
```

### Database extraction

The CodeQL CLI uses special programs, called extractors, to extract information from the source code of a software system into a database that can be queried. You can customize the behavior of extractors by setting extractor configuration options through the CodeQL CLI. See [Extractor options](/en/code-security/reference/code-scanning/codeql/codeql-cli/extractor-options).

## About the GitHub CodeQL license

**License notice:** If you don’t have a license for GitHub Code Security then, by installing this product, you are agreeing to the [GitHub CodeQL Terms and Conditions](https://github.com/github/codeql-cli-binaries/blob/main/LICENSE.md).

For information about how you can try GitHub Enterprise with GitHub Advanced Security for free, see [Setting up a trial of GitHub Enterprise Cloud](/en/enterprise-cloud@latest/admin/overview/setting-up-a-trial-of-github-enterprise-cloud) and [Setting up a trial of GitHub Advanced Security](/en/enterprise-cloud@latest/billing/managing-billing-for-your-products/managing-billing-for-github-advanced-security/setting-up-a-trial-of-github-advanced-security#setting-up-your-trial-of-github-advanced-security) in the GitHub Enterprise Cloud documentation.

## About CodeQL CLI database bundles

The CodeQL CLI database bundle command can be used to create a relocatable archive of a CodeQL database.

A copy of a database bundle can be used to share troubleshooting information with your team members or with GitHub Support. See [Creating CodeQL CLI database bundles](/en/code-security/how-tos/scan-code-for-vulnerabilities/scan-from-the-command-line/creating-database-bundle-for-troubleshooting).

## Getting started

For the simplest way to get started, see [Setting up the CodeQL CLI](/en/code-security/codeql-cli/getting-started-with-the-codeql-cli/setting-up-the-codeql-cli).

More advanced setup options are available if you need them. For example, if you:

* Want to contribute to open source shared CodeQL queries and prefer working with the CodeQL source code directly. See [Checking out the CodeQL CLI source code](/en/code-security/how-tos/scan-code-for-vulnerabilities/scan-from-the-command-line/check-out-source-code).
* Need to install multiple versions of the CodeQL CLI side by side. For example, if one codebase requires a specific version while another uses the latest. You can download each version and unpack both CLI archives in the same parent directory.
* Are researching or developing queries and want to download databases from GitHub.com. See [Downloading CodeQL databases from GitHub](/en/code-security/how-tos/scan-code-for-vulnerabilities/scan-from-the-command-line/download-databases).