# Configuring the dependency review action

You can use the dependency review action to catch vulnerabilities before they are added to your project.

The "dependency review action" refers to the specific action that can report on differences in a pull request within the GitHub Actions context. It can also add enforcement mechanisms to the GitHub Actions workflow. For more information, see [Dependency review](/en/code-security/concepts/supply-chain-security/about-dependency-review#about-the-dependency-review-action).

For a list of common configuration options, see [Dependency review](https://github.com/marketplace/actions/dependency-review#configuration-options) on the GitHub Marketplace.

## Configuring the dependency review action

There are two methods of configuring the dependency review action:

* Inlining the configuration options in your workflow file.
* Referencing a configuration file in your workflow file.

Notice that all of the examples use a short version number for the action (`v3`) instead of a semver release number (for example, `v3.0.8`). This ensures that you use the most recent minor version of the action.

### Using inline configuration to set up the dependency review action

1. Add a new YAML workflow to your `.github/workflows` folder.

   ```yaml copy
   name: 'Dependency Review'
   on: [pull_request]

   permissions:
     contents: read

   jobs:
     dependency-review:
       runs-on: ubuntu-latest
       steps:
        - name: 'Checkout Repository'
          uses: actions/checkout@v6
        - name: Dependency Review
          uses: actions/dependency-review-action@v4
   ```

2. Specify your settings.

   This dependency review action example file illustrates how you can use the available configuration options.

   <!-- markdownlint-disable search-replace -->

   ```yaml copy
   name: 'Dependency Review'
   on: [pull_request]

   permissions:
     contents: read

   jobs:
     dependency-review:
       runs-on: ubuntu-latest
       steps:
       - name: 'Checkout Repository'
         uses: actions/checkout@v6
       - name: Dependency Review
         uses: actions/dependency-review-action@v4
         with:
           # Possible values: "critical", "high", "moderate", "low"
           fail-on-severity: critical

           
           # You can only include one of these two options: `allow-licenses` and `deny-licenses`
           # ([String]). Only allow these licenses (optional)
           # Possible values: Any SPDX-compliant license identifiers or expressions from https://spdx.org/licenses/
           allow-licenses: GPL-3.0, BSD-3-Clause, MIT
           # ([String]). Block the pull request on these licenses (optional)
           # Possible values: Any SPDX-compliant license identifiers or expressions from https://spdx.org/licenses/
           deny-licenses: LGPL-2.0, BSD-2-Clause
           
           # ([String]). Skip these GitHub Advisory Database IDs during detection (optional)
           # Possible values: Any valid GitHub Advisory Database ID from https://github.com/advisories
           allow-ghsas: GHSA-abcd-1234-5679, GHSA-efgh-1234-5679
           # ([String]). Block pull requests that introduce vulnerabilities in the scopes that match this list (optional)
           # Possible values: "development", "runtime", "unknown"
           fail-on-scopes: development, runtime
   ```

   <!-- markdownlint-enable search-replace -->

### Using a configuration file to set up dependency review action

1. Add a new YAML workflow to your `.github/workflows` folder and use `config-file` to specify that you are using a configuration file.

   ```yaml copy
   name: 'Dependency Review'
   on: [pull_request]

   permissions:
    contents: read

   jobs:
     dependency-review:
       runs-on: ubuntu-latest
       steps:
       - name: 'Checkout Repository'
         uses: actions/checkout@v6
       - name: Dependency Review
         uses: actions/dependency-review-action@v4
         with:
          # ([String]). Representing a path to a configuration file local to the repository or in an external repository.
          # Possible values: An absolute path to a local file or an external file.
          config-file: './.github/dependency-review-config.yml'
          # Optional alternative syntax for an external file: OWNER/REPOSITORY/FILENAME@BRANCH (uncomment if preferred)
          # config-file: 'github/octorepo/dependency-review-config.yml@main'

          # ([Token]) Use if your configuration file resides in a private external repository.
          # Possible values: Any GitHub token with read access to the private external repository.
          external-repo-token: 'ghp_123456789abcde'
   ```

2. Create the configuration file in the path you have specified.

   This YAML example file illustrates how you can use the available configuration options.

   <!-- markdownlint-disable search-replace -->

   ```yaml copy
     # Possible values: "critical", "high", "moderate", "low"
     fail-on-severity: critical

     # You can only include one of these two options: `allow-licenses` and `deny-licenses`
     # ([String]). Only allow these licenses (optional)
     # Possible values: Any SPDX-compliant license identifiers or expressions from https://spdx.org/licenses/
     allow-licenses:
       - GPL-3.0
       - BSD-3-Clause
       - MIT
      # ([String]). Block the pull request on these licenses (optional)
      # Possible values: Any SPDX-compliant license identifiers or expressions from https://spdx.org/licenses/
     deny-licenses:
       - LGPL-2.0
       - BSD-2-Clause

      # ([String]). Skip these GitHub Advisory Database IDs during detection (optional)
      # Possible values: Any valid GitHub Advisory Database ID from https://github.com/advisories
     allow-ghsas:
       - GHSA-abcd-1234-5679
       - GHSA-efgh-1234-5679
      # ([String]). Block pull requests that introduce vulnerabilities in the scopes that match this list (optional)
      # Possible values: "development", "runtime", "unknown"
     fail-on-scopes:
       - development
       - runtime
   ```

   <!-- markdownlint-enable search-replace -->

For further details about the configuration options, see [`dependency-review-action`](https://github.com/actions/dependency-review-action#readme).

## Further reading

* [Customizing your dependency review action configuration](/en/code-security/supply-chain-security/understanding-your-software-supply-chain/customizing-your-dependency-review-action-configuration)