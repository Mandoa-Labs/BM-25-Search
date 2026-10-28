# Using plugins in Visual Studio Code

Add reusable capabilities to Visual Studio Code by installing plugins from a marketplace or a local source.

Plugins package related customizations so you can install them together. For an overview, see [Plugins for GitHub Copilot](/en/copilot/concepts/customizations/plugins).

To browse and install plugins in Visual Studio Code:

1. Open **Customize** from the Chat side panel or Agents window.
2. On the **Browse** page, search for a plugin, then select **Install**.

You can also [open Browse in Visual Studio Code](vscode://chat-customizations/open?page=discover). <!-- markdownlint-disable-line GHD003 -->

To add a marketplace and browse its plugins:

1. Run **Chat: Manage Plugin Marketplaces** from the Command Palette.
2. Select **Add Marketplace...**, then enter the marketplace source.
3. Open **Customize**, search for a plugin from the marketplace, then select **Install**.

For instructions on creating and publishing a GitHub-hosted marketplace, see [Creating and sharing a plugin marketplace on GitHub](/en/copilot/how-tos/copilot-on-github/customize-copilot/create-and-share-plugin-marketplaces).

## Install a plugin from a source

You can install a plugin directly from a Git repository or local folder without adding its marketplace.

1. Run **Chat: Install Plugin from Source** from the Command Palette.
2. Enter the repository or local folder path.

## Turn off a plugin

You can turn off an installed plugin, including one enabled by repository defaults.

1. Open **Customize** from the Chat side panel or Agents window.
2. Select **Plugins**.
3. In the list of installed plugins, turn off the toggle next to the plugin. To turn the plugin back on, turn on the toggle.

If the toggle is unavailable, enterprise managed settings require or block the plugin, and it appears as managed by policy. You cannot change it.

## Further reading

* [Creating and sharing a plugin marketplace on GitHub](/en/copilot/how-tos/copilot-on-github/customize-copilot/create-and-share-plugin-marketplaces)
* [Finding and installing plugins for GitHub Copilot CLI](/en/copilot/how-tos/copilot-cli/customize-copilot/plugins-finding-installing)
* [Agent Plugins reference](https://code.visualstudio.com/docs/agents/reference/agent-plugin-reference)