# About remote control of GitHub Copilot CLI sessions

Remote control lets you monitor and steer a Copilot CLI session from GitHub.com or GitHub Mobile, even after you've stepped away from your machine.

This article explains the concepts around remote control of Copilot CLI sessions. For instructions on how to enable remote control, see [Steering a GitHub Copilot CLI session from another device](/en/copilot/how-tos/copilot-cli/use-copilot-cli/steer-remotely).

## When remote control helps

By default, GitHub Copilot CLI sessions are only steerable from your local machine. However, you can enable remote control of the session. Remote control is useful when you want to view progress or respond to prompts and permission requests, without having to remain at the machine where the session is running. For example:

* **You step away from your workstation**: Keep interacting with Copilot from your phone or another device, without returning to the machine where the session is running.
* **A long-running task needs your input**: Approve permission requests and answer questions as they come up, so the task isn't blocked while you're away.
* **You want a quick status check**: Glance at session progress from GitHub Mobile while you work on something else.

## Prerequisites

Remote control requires:

* **Policy enablement**: If your Copilot seat comes from an organization, an enterprise or organization owner must enable the "Remote Control" policy (off by default). See [Administering remote control](#administering-remote-control) later in this article.
* **The machine must be online**: The CLI session must be actively running in a terminal on a machine with an internet connection. If the machine goes to sleep or loses its connection, remote control is unavailable until the machine is back online. See [Reconnection](#reconnection) later in this article.
* **An interactive session**: Remote access is only available for interactive sessions. It is not available when you use the CLI programmatically with the `--prompt` command-line option, for example when you use the CLI in a script.

## Accessing a session remotely

When you enable remote control for a Copilot CLI session, you can go to GitHub.com or GitHub Mobile and find the session in the list of your recent agent sessions. The remote interface is updated in real time, allowing you to monitor ongoing output from the session and respond to prompts and permission requests as they come in.

Both the local terminal and the remote interface are active at the same time. You can enter commands in either interface. Copilot CLI uses the first response it receives to any prompt or permission request.

Your session continues to run on your local machine. The remote interface provides a way to interact with the session, but the CLI itself—and all the tools, shell commands, and file operations it runs—remain on the machine where you started the session.

## What you can do remotely

When connected to a session remotely from GitHub.com or GitHub Mobile, you can:

* **Respond to permission requests**: Approve or deny tool, file path, and URL permission requests.
* **Respond to questions**: Answer when Copilot asks you to supply more information or make a decision.
* **Approve or reject plans**: Respond to plan approval prompts when Copilot is in plan mode.
* **Submit new prompts**: Enter questions or instructions, just as you would in the terminal.
* **Switch modes**: Change the session mode—for example, between interactive and plan mode.
* **End the current operation**: Cancel the agent's current work.

> \[!NOTE]
> Slash commands—such as `/allow-all`—are not currently available from the remote interface.

## Reconnection

If the connection between your local machine and GitHub is temporarily lost—for example, due to a network interruption—you can continue using the session remotely as soon as the connection is restored.

You can use the `/keep-alive` slash command to prevent your machine from going to sleep. See [Preventing your machine from going to sleep](/en/copilot/how-tos/copilot-cli/use-copilot-cli/steer-remotely#preventing-your-machine-from-going-to-sleep).

When you use `copilot --continue` or `copilot --resume` to resume a CLI session for which remote control was enabled, remote control is automatically re-enabled.

## Security and privacy

Remote control is only available to you — the person signed in to GitHub with the same account that started the CLI session. No one else can view or interact with your sessions remotely. The session URL displayed in the CLI is session-specific and only accessible to authenticated users with the correct account.

When remote control is enabled:

* Session events (conversation messages, tool execution events, and permission requests) are sent from your local machine to GitHub.
* Remote commands are polled by Copilot CLI from GitHub and injected into your local session.
* The CLI continues to run locally — all shell commands, file operations, and tool executions happen on your machine. Remote control does not grant direct access to your machine beyond what the CLI agent can do within the session.

The remote session link (displayed in the CLI when you enable remote control) points to a session-specific URL on GitHub.com. Only authenticated users with the correct account can access this URL.

## Administering remote control

Enterprise and organization owners control whether users can enable remote control, using the "Remote Control" policy. This policy is off by default.

For more information, see [Managing policies and features for GitHub Copilot in your organization](/en/copilot/how-tos/administer-copilot/manage-for-organization/manage-policies) and [Administering Copilot CLI for your enterprise](/en/copilot/how-tos/copilot-cli/administer-copilot-cli-for-your-enterprise).