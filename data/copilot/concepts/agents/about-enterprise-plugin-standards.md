# About enterprise-managed plugin standards

Enterprise administrators can centrally define plugin policies for users, ensuring consistent plugin availability.

> \[!NOTE] This feature is in public preview and subject to change.

Enterprise-managed plugin standards allow administrators to **define and enforce policies for plugin availability**. By configuring a `settings.json` file in the enterprise's `.github-private` repository, administrators can specify which plugin marketplaces are available to users and which plugins are installed automatically.

## Where plugin standards apply

Plugin standards apply to all users on the enterprise's Copilot plan, across the following clients:

* **Copilot CLI**: see [About plugins for GitHub Copilot CLI](/en/copilot/concepts/agents/copilot-cli/about-cli-plugins)
* **VS Code** (version 1.122 and later): see [Agent plugins in VS Code](https://code.visualstudio.com/docs/agent-customization/agent-plugins) in the VS Code documentation

Users must upgrade to a supported client version for these standards to be applied.

## How plugin standards work

Enterprise plugin standards use a configuration file stored in your enterprise's `.github-private` repository. The configuration is defined in a `settings.json` file at the following path: `.github/copilot/settings.json`.

For plugin standards, the file can define:

* **Known marketplaces**. Plugin marketplaces that are available to users for browsing and installing plugins.
* **Default-enabled plugins**. Specific plugins that are automatically installed when users authenticate.

When a user authenticates to Copilot in a supported client, the client queries an API endpoint that reads the `settings.json` from the enterprise's `.github-private` repository. The policies defined in the file are then applied to the user's session.

## Why use enterprise-managed plugin standards

Enterprise-managed plugin standards help administrators address several common challenges:

* **Consistency across clients**. Ensure that all developers have access to the same plugins and marketplaces.
* **Centralized governance**. Manage plugin availability from a single configuration file, rather than relying on individual developers to install the correct plugins.
* **Version-controlled policies**. Because the configuration lives in a Git repository, all changes to plugin standards are tracked, auditable, and reviewable through pull requests.
* **Reduced onboarding friction**. New developers automatically receive the enterprise's standard plugins when they authenticate, without any manual setup.

## Next step

To configure enterprise plugin standards, see [Configuring enterprise plugin standards](/en/copilot/how-tos/administer-copilot/manage-for-enterprise/manage-agents/configure-enterprise-plugin-standards).