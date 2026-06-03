# Configuring local sandbox settings

Use the /sandbox slash command in Copilot CLI to control how the local sandbox restricts filesystem access, network connectivity, and system capabilities.

> \[!NOTE]
> Cloud and local sandboxes for GitHub Copilot is in public preview and subject to change.

## About local sandbox configuration

When you enable local sandboxing in Copilot CLI, shell commands that Copilot runs on your behalf execute inside an isolated sandbox. You can fine-tune the sandbox's behavior—controlling filesystem paths, network access, and general settings—using the `/sandbox` slash command.

Settings are stored in `settings.json` under the `sandbox` key in your Copilot CLI configuration directory. For more information about the configuration directory, see [GitHub Copilot CLI configuration directory](/en/copilot/reference/copilot-cli-reference/cli-config-dir-reference).

For a conceptual overview of cloud and local sandboxes for GitHub Copilot, see [About cloud and local sandboxes for GitHub Copilot](/en/copilot/concepts/about-cloud-and-local-sandboxes).

## Opening the sandbox configuration

1. Start a Copilot CLI session.
2. Enter the `/sandbox` slash command.

   This opens an interactive configuration interface with three tabs: **General**, **Filesystem**, and **Network**. Use <kbd>Tab</kbd> to switch between tabs. Press <kbd>Esc</kbd> to save your changes and close the configuration.

## Configuring general settings

The **General** tab controls the top-level sandbox behavior.

| Setting                   | Description                                                                                                                                                                                                                           |
| ------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Sandboxing enabled**    | When turned on, shell commands that Copilot executes run inside the sandbox. You can also toggle this with `/sandbox enable` and `/sandbox disable`.                                                                                  |
| **Allow keychain access** | When turned on, sandboxed commands can use the macOS Keychain—for example, to access credentials used by `git` and `gh` credential helpers. Turn this off if you want to prevent sandboxed processes from reading stored credentials. |

## Configuring filesystem settings

The **Filesystem** tab controls which directories and files the sandboxed process can access. By default, the sandbox restricts filesystem access to prevent unintended reads or writes outside your project.

| Setting                       | Description                                                                                                                                                                                                                         |
| ----------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Include working directory** | When turned on, the current working directory is automatically added to the list of read/write paths. This means sandboxed commands can read and write files in your project directory without manually adding it to the path list. |
| **Clear policy on exit**      | When turned on, all filesystem permissions are reset when the sandbox exits. This ensures that each session starts with a clean set of permissions.                                                                                 |

### Adding filesystem path rules

You can add specific path rules to grant the sandbox read-only or read/write access to directories and files outside the working directory.

1. In the **Filesystem** tab, press <kbd>A</kbd> to add a new path rule.
2. Enter the file or directory path.
3. Set the permission level for the path.

Use <kbd>Enter</kbd> to edit an existing path rule, and <kbd>D</kbd> to delete one.

## Configuring network settings

The **Network** tab controls whether sandboxed processes can make network connections.

| Setting                        | Description                                                                                                                                  |
| ------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------- |
| **Allow outbound connections** | When turned on, the sandboxed process can reach external hosts on the internet. Turn this off to fully isolate the sandbox from the network. |
| **Allow local network**        | When turned on, the sandboxed process can reach hosts on your local network (for example, `localhost` or other devices on your LAN).         |

### Adding network host rules

You can add specific host rules to allow or block access to individual hosts when outbound connections are otherwise restricted.

1. In the **Network** tab, press <kbd>A</kbd> to add a new host rule.
2. Enter the hostname.
3. Set whether to allow or block access to the host.

Use <kbd>Enter</kbd> to edit an existing host rule, and <kbd>D</kbd> to delete one.

## Enabling and disabling the sandbox quickly

You can toggle the sandbox on or off without opening the full configuration interface:

* **Enable**: Enter `/sandbox enable` in the Copilot CLI session.
* **Disable**: Enter `/sandbox disable` in the Copilot CLI session.

These commands change the **Sandboxing enabled** setting on the **General** tab.

## Further reading

* [About cloud and local sandboxes for GitHub Copilot](/en/copilot/concepts/about-cloud-and-local-sandboxes)
* [Enabling or disabling cloud and local sandboxes for GitHub Copilot for your organization](/en/copilot/how-tos/cloud-and-local-sandboxes/enabling-or-disabling-cloud-and-local-sandboxes-for-your-organization)
* [Configuring GitHub Copilot CLI](/en/copilot/how-tos/copilot-cli/set-up-copilot-cli/configure-copilot-cli)