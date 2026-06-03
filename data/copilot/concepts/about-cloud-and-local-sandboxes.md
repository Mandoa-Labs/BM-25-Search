# About cloud and local sandboxes for GitHub Copilot

Cloud and local sandboxes for GitHub Copilot provide isolated execution environments that let Copilot safely interact with code, tools, filesystem, and network resources securely on your local machine or in fully isolated cloud environments.

> \[!NOTE]
> Cloud and local sandboxes for GitHub Copilot is in public preview and subject to change.

## Introduction

Cloud and local sandboxes for GitHub Copilot are the execution platform powering secure sandboxed experiences for GitHub Copilot CLI, both locally and in the cloud. As Copilot takes more actions on your behalf—running tools, executing commands, and modifying files—sandboxes for GitHub Copilot provide the isolation, portability, and policy controls needed to adopt agentic workflows safely. Cloud and local sandboxes for GitHub Copilot currently apply to Copilot CLI sessions, and you can also use cloud sandboxes for sessions in the GitHub Copilot app.

With cloud and local sandboxes for GitHub Copilot, you can choose where Copilot runs:

* **Local sandboxing**: Run Copilot securely on your own machine, with restricted access to filesystem, network, and system capabilities.
* **Cloud sandboxing**: Run Copilot inside fully isolated, ephemeral Linux environments hosted by GitHub.

## Local sandboxing

Local sandboxing lets Copilot run in a sandboxed environment directly on your machine, with restricted access to your filesystem, network connectivity, and system capabilities.

### Enabling local sandboxing

To enable local sandboxing inside a Copilot CLI session, run:

```shell copy
/sandbox enable
```

Once enabled, commands that Copilot executes on your behalf run inside the sandbox, limiting their access to your system.

### Cross-platform support

Local sandboxing is available across macOS, Linux, and Windows, delivering a consistent isolation experience regardless of your operating system.

### Enterprise policy enforcement

For organizations and enterprises, local sandbox policies can be centrally configured and enforced using Microsoft Intune and other MDM (mobile device management) platforms. This gives administrators control over how Copilot interacts with local resources across managed devices.

## Cloud sandboxing

Cloud sandboxing lets you run Copilot CLI sessions inside fully isolated, ephemeral Linux environments hosted by GitHub. Each cloud sandbox session is isolated from your local environment and from other sessions.

Cloud sandboxing is built on Azure Container Apps Sandboxes, with GitHub providing the identity, policy, and billing layer.

### Starting a cloud sandbox session

To start a cloud-backed session, run the following command:

```shell copy
copilot --cloud
```

This launches an interactive Copilot CLI session inside a cloud sandbox. You can prompt Copilot to perform tasks, run shell commands, and iterate on code, the same way you would in a local session. The commands that Copilot runs execute in the cloud environment, not on your local machine.

### Continue sessions across devices

Because cloud sandbox sessions run in GitHub-hosted infrastructure, you can pick up a Copilot session on any device, regardless of where the session was originally started. This enables more flexible workflows without needing to copy files or reinstall dependencies.

### Offload compute-intensive workflows

You can run multiple Copilot tasks in parallel in the cloud without consuming local resources. This keeps your local environment lightweight and responsive while scaling agent-driven work.

### Unified governance

Cloud sandbox policies share the same configuration as Copilot cloud agent policies, extending existing security controls to cloud sandboxed execution without additional setup.

### Session lifecycle

A cloud sandbox session has three main states:

* **Active**: The session is running, and you are interacting with it from Copilot CLI.
* **Stopped**: The session is not currently running, but its state is saved. When you resume it, your files, environment variables, and in-progress work are restored.
* **Deleted**: The session and its saved state are removed and cannot be recovered.

When you stop a session, the cloud sandbox creates a snapshot of its state so you can pick up where you left off later. When you delete a session, both the running environment and the snapshot are removed.

## Authentication and access

Sandboxes for GitHub Copilot use your existing Copilot CLI authentication. If you can sign in to Copilot CLI and have access to Copilot, you can use sandboxes for GitHub Copilot. You don't need to configure a separate cloud provider, manage API keys, or set up infrastructure.

An organization or enterprise owner must enable the **Cloud Sandbox access** policy in the organization or enterprise settings before members can use sandboxes for GitHub Copilot.

For information about signing in to Copilot CLI, see [Installing GitHub Copilot CLI](/en/copilot/how-tos/set-up/install-copilot-cli).

## Billing

Local sandboxing is included in the standard GitHub Copilot seat at no additional cost.

Cloud sandboxing is billed based on usage. GitHub measures cloud sandbox usage across three meters:

| Meter   | Description                                                      | Unit           | Price (USD) |
| ------- | ---------------------------------------------------------------- | -------------- | ----------- |
| Compute | Time that a cloud sandbox session is running.                    | Compute second | $0.000024   |
| Memory  | Memory allocated to a cloud sandbox session while it is running. | GiB second     | $0.000003   |
| Storage | Snapshot storage for stopped sessions.                           | GiB month      | $0.005      |

For more information about how cloud sandbox usage is measured and billed, see [Billing for cloud and local sandboxes for GitHub Copilot](/en/billing/concepts/product-billing/cloud-and-local-sandboxes).

## Further reading

* [About GitHub Copilot CLI](/en/copilot/concepts/agents/copilot-cli/about-copilot-cli)
* [Enabling or disabling cloud and local sandboxes for GitHub Copilot for your organization](/en/copilot/how-tos/cloud-and-local-sandboxes/enabling-or-disabling-cloud-and-local-sandboxes-for-your-organization)
* [Installing GitHub Copilot CLI](/en/copilot/how-tos/set-up/install-copilot-cli)