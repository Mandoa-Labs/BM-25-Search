# Installing CodeQL for Visual Studio Code

To get started with CodeQL for Visual Studio Code, you need to install and set up the extension.

## Prerequisites

The CodeQL extension requires a minimum of Visual Studio Code 1.82.0. Older versions are not supported.

## Installing the extension

You can install the CodeQL for Visual Studio Code extension using one of several different methods:

* Using the Visual Studio Code Marketplace in a browser.

* Searching in the "Extensions" view in Visual Studio Code.

* Using a VSIX file.

### Using the Visual Studio Code Marketplace

1. In your browser, go to the ["CodeQL" page](https://marketplace.visualstudio.com/items?itemName=GitHub.vscode-codeql) in the Visual Studio Code Marketplace.

2. Click **Install**, then follow the on-screen prompts.

### Searching in the "Extensions" view

1. In VS Code, open the "Extensions" view.

2. Search for "CodeQL", then click **Install**.

### Using the CodeQL VSIX file

1. Download the [CodeQL VSIX file](https://github.com/github/vscode-codeql/releases?ref_product=code-scanning\&ref_type=engagement\&ref_style=text) from the `github/vscode-codeql` repository on GitHub.

2. In VS Code, open the "Extensions" view.

3. At the top right of the sidebar, click the ellipsis then click **Install from VSIX...**.

4. Select the CodeQL VSIX file downloaded in step 1.

5. Follow the on-screen prompts to complete the installation.

## Next steps

To learn how to work with CodeQL databases in the extension, see [Managing CodeQL databases](/en/code-security/codeql-for-vs-code/getting-started-with-codeql-for-vs-code/managing-codeql-databases).

If you have already found, downloaded, or created a CodeQL database, you can learn how to use the extension to run queries on CodeQL databases and view the results. For more information, see [Running CodeQL queries](/en/code-security/codeql-for-vs-code/getting-started-with-codeql-for-vs-code/running-codeql-queries).

To learn how to model additional dependencies of a codebase and improve your code scanning results, see [Using the CodeQL model editor](/en/code-security/codeql-for-vs-code/using-the-advanced-functionality-of-the-codeql-for-vs-code-extension/using-the-codeql-model-editor).

To learn how to configure access to a different version of the CodeQL CLI than the one installed with the extension, see [Managing the CodeQL CLI in the VS Code extension](/en/code-security/codeql-for-vs-code/using-the-advanced-functionality-of-the-codeql-for-vs-code-extension/configuring-access-to-the-codeql-cli).

To learn how to set up a CodeQL workspace, see [Setting up a CodeQL workspace](/en/code-security/codeql-for-vs-code/using-the-advanced-functionality-of-the-codeql-for-vs-code-extension/setting-up-a-codeql-workspace).