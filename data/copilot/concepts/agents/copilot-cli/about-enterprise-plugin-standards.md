# About enterprise-managed plugin standards for Copilot CLI

Enterprise administrators can centrally define plugin policies for Copilot CLI, ensuring consistent plugin availability across their enterprise.

> \[!NOTE] This feature is in public preview and subject to change.

Enterprise-managed plugin standards allow administrators to **define and enforce policies for plugin availability** in Copilot CLI across their enterprise. By configuring a `settings.json` file in the enterprise's `.github-private` repository, administrators can specify which plugin marketplaces are available to users and which plugins are automatically installed for all enterprise users.

## How plugin standards work

Enterprise plugin standards use a configuration file stored in your enterprise's `.github-private` repository. The configuration is defined in a `settings.json` file at the following path: `.github/copilot/settings.json`.

For plugin standards, the file can define:

* **Known marketplaces**. Plugin marketplaces that are available to users for browsing and installing plugins.
* **Default-enabled plugins**. Specific plugins that are automatically installed for all enterprise users when they authenticate with the CLI.

When a user signs in to Copilot CLI, the client queries an API endpoint that reads the `settings.json` from the enterprise's `.github-private` repository. The policies defined in the file are then applied to the user's CLI session.

## Why use enterprise-managed plugin standards

Enterprise-managed plugin standards help administrators address several common challenges:

* **Consistency across clients**. Ensure that all developers using Copilot CLI with an enterprise-assigned Copilot license have access to the same plugins and marketplaces.
* **Centralized governance**. Manage plugin availability from a single configuration file, rather than relying on individual developers to install the correct plugins.
* **Version-controlled policies**. Because the configuration lives in a Git repository, all changes to plugin standards are tracked, auditable, and reviewable through pull requests.
* **Reduced onboarding friction**. New developers automatically receive the enterprise's standard plugins when they authenticate, without any manual setup.

## Next step

To configure enterprise plugin standards for Copilot CLI, see [Configuring enterprise plugin standards for Copilot CLI](/en/copilot/how-tos/administer-copilot/manage-for-enterprise/manage-agents/configure-enterprise-plugin-standards).