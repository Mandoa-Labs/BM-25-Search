# Creating automations with Copilot cloud agent

Create and manage automations to run Copilot cloud agent on a schedule or in response to events.

## Introduction

With automations, you can set up Copilot cloud agent to run automatically, either on a schedule or in response to an event in a repository. Automations can take action within the repository where they are configured, such as opening a pull request or labeling an issue.

You can create and manage automations from the **Agents** tab of a repository on GitHub. You can also create and manage automations from the **Automations** tab in the GitHub Copilot app.

For an overview of automations, including triggers, tools, visibility, and security, see [About Copilot automations](/en/copilot/concepts/agents/cloud-agent/about-automations).

## Prerequisites

For automations to be available in a repository, all of the following must be true:

* The repository must be **private or internal**. Automations are not available in public repositories.
* Copilot cloud agent must be enabled for the repository. If you have Copilot Business or Copilot Enterprise, an administrator must enable the Copilot cloud agent policy. See [Managing access to GitHub Copilot cloud agent](/en/copilot/concepts/agents/cloud-agent/access-management).
* The organization must allow both Copilot cloud agent and automations in the repository (both are enabled by default). See [Adding GitHub Copilot cloud agent to your organization](/en/copilot/how-tos/administer-copilot/manage-for-organization/add-copilot-cloud-agent).

Automations are available with the GitHub Copilot Pro, GitHub Copilot Pro+, GitHub Copilot Max, GitHub Copilot Business, and GitHub Copilot Enterprise plans.

## Creating an automation

1. On GitHub, navigate to the main page of the repository.

2. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-agent" aria-label="agent" role="img"><path d="M14.5 8.9v-.052A2.956 2.956 0 0 0 11.542 5.9a.815.815 0 0 1-.751-.501l-.145-.348A3.496 3.496 0 0 0 7.421 2.9h-.206a3.754 3.754 0 0 0-3.736 4.118l.011.121a.822.822 0 0 1-.619.879A1.81 1.81 0 0 0 1.5 9.773v.14c0 1.097.89 1.987 1.987 1.987H4.5a.75.75 0 0 1 0 1.5H3.487A3.487 3.487 0 0 1 0 9.913v-.14C0 8.449.785 7.274 1.963 6.75A5.253 5.253 0 0 1 7.215 1.4h.206a4.992 4.992 0 0 1 4.586 3.024A4.455 4.455 0 0 1 16 8.848V8.9a.75.75 0 0 1-1.5 0Z"></path><path d="m8.38 7.67 2.25 2.25a.749.749 0 0 1 0 1.061L8.38 13.23a.749.749 0 1 1-1.06-1.06l1.719-1.72L7.32 8.731A.75.75 0 0 1 8.38 7.67ZM15 13.45h-3a.75.75 0 0 1 0-1.5h3a.75.75 0 0 1 0 1.5Z"></path></svg> Agents**.

3. In the sidebar, click **Automations**.

4. Click **Create new**.

5. Enter a **name** for the automation.

6. Select one or more **triggers** that determine when the automation runs:

   * **On a schedule**: choose a recurring interval, either hourly, daily, or weekly.
   * **When an issue is created**: the automation runs each time an issue is opened in the repository.
   * **When a pull request is opened**: the automation runs each time a pull request is opened in the repository.
   * **When a pull request is synchronized**: the automation runs each time new commits are pushed to a pull request in the repository.

   You can optionally configure filters for issue and pull request triggers:

   * For when **an issue is created**, add a search query filter.
   * For when **a pull request is opened** and when **a pull request is synchronized**, add a search query filter and a filter for files changed in the pull request.

7. In the **prompt** field, describe the task you want Copilot to perform each time the automation runs.

   For example, `Label this issue as a bug, an enhancement, or other, based on its content.`

   > \[!WARNING]
   > The Copilot cloud agent sessions started by an automation are visible to others with access to the repository. Don't include secrets or other sensitive information in your prompt. To give Copilot access to sensitive values, use repository secrets. See [Configure secrets and variables for Copilot cloud agent](/en/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/configure-secrets-and-variables).

8. Optionally, select the **model** you want Copilot to use. See [Changing the AI model for GitHub Copilot cloud agent](/en/copilot/how-tos/use-copilot-agents/cloud-agent/changing-the-ai-model).

9. Select the **tools** Copilot can use when the automation runs, such as pushing changes, updating issue labels, or creating a pull request.

   Select only the tools the task requires. The tools you select control what actions Copilot can take in your repository. Optionally, you can use the **Suggest tools** button to ask Copilot to suggest tools based on your prompt. See [About Copilot automations](/en/copilot/concepts/agents/cloud-agent/about-automations#tools-and-actions).

10. Save the automation by clicking **Create automation**.

## Testing an automation

You can run an automation immediately, without waiting for its trigger to fire, to check that it behaves as you expect.

1. Open the automation you want to test from the **Automations** pane.
2. Click the **Run now** button.
   Copilot starts a Copilot cloud agent session and runs the automation's prompt with the tools you selected. You can open the session to follow its progress and review any changes it makes.

## Managing your Automations

Your automations are private to you, but the sessions started from your automations will be visible to everyone with read access to the repository.

From the **Automations** pane in a repository, you can:

* View your automations for the repository and the sessions they have started.
* Edit an automation to change its name, prompt, triggers, tools, or model.
* Disable an automation to stop it running, or enable it again later.
* Delete an automation you no longer need.

To see all of your automations across every repository, and navigate to manage each one, use the Automations view at the user level.

## Further reading

* [About Copilot automations](/en/copilot/concepts/agents/cloud-agent/about-automations)
* [Starting GitHub Copilot sessions](/en/copilot/how-tos/use-copilot-agents/cloud-agent/start-copilot-sessions)
* [Risks and mitigations for GitHub Copilot cloud agent](/en/copilot/concepts/agents/cloud-agent/risks-and-mitigations)