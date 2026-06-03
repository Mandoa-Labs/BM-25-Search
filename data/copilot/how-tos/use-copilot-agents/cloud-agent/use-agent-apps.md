# Using agent apps

Start a partner-built agent from an issue, a pull request comment, or the Agents UI on GitHub.

> \[!NOTE] Agent apps are currently in public preview and subject to change.

## Introduction

Agent apps let you delegate work to partner-built agents from within GitHub. For an overview, see [About agent apps](/en/copilot/concepts/agents/agent-apps).

Before you can use an agent app, the GitHub App must be installed on the account or organization that owns the repository, and agent features must be enabled for the app. If the repository is owned by an organization that belongs to an enterprise, the "Agent apps" Copilot policy must also be enabled in your enterprise settings.

## Authorizing an agent app

The first time you use an agent app, GitHub prompts you to authorize the app through an OAuth flow. Follow the prompts to authorize the app before the agent runs. For more information, see [Authorizing GitHub Apps](/en/apps/using-github-apps/authorizing-github-apps).

## Starting an agent from the Agents UI

1. Open the agents panel or tab:

   * Open the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-agent" aria-label="The Agents icon" role="img"><path d="M14.5 8.9v-.052A2.956 2.956 0 0 0 11.542 5.9a.815.815 0 0 1-.751-.501l-.145-.348A3.496 3.496 0 0 0 7.421 2.9h-.206a3.754 3.754 0 0 0-3.736 4.118l.011.121a.822.822 0 0 1-.619.879A1.81 1.81 0 0 0 1.5 9.773v.14c0 1.097.89 1.987 1.987 1.987H4.5a.75.75 0 0 1 0 1.5H3.487A3.487 3.487 0 0 1 0 9.913v-.14C0 8.449.785 7.274 1.963 6.75A5.253 5.253 0 0 1 7.215 1.4h.206a4.992 4.992 0 0 1 4.586 3.024A4.455 4.455 0 0 1 16 8.848V8.9a.75.75 0 0 1-1.5 0Z"></path><path d="m8.38 7.67 2.25 2.25a.749.749 0 0 1 0 1.061L8.38 13.23a.749.749 0 1 1-1.06-1.06l1.719-1.72L7.32 8.731A.75.75 0 0 1 8.38 7.67ZM15 13.45h-3a.75.75 0 0 1 0-1.5h3a.75.75 0 0 1 0 1.5Z"></path></svg> Agents** tab in a repository.
   * **Navigate to the agents page**: Go to [github.com/copilot/agents](https://github.com/copilot/agents?ref_product=copilot\&ref_type=engagement\&ref_style=text). You can also get here by opening the agents panel, then clicking **View all**.
   * **Open the agents panel**: Click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-agent" aria-label="The Agents icon" role="img"><path d="M14.5 8.9v-.052A2.956 2.956 0 0 0 11.542 5.9a.815.815 0 0 1-.751-.501l-.145-.348A3.496 3.496 0 0 0 7.421 2.9h-.206a3.754 3.754 0 0 0-3.736 4.118l.011.121a.822.822 0 0 1-.619.879A1.81 1.81 0 0 0 1.5 9.773v.14c0 1.097.89 1.987 1.987 1.987H4.5a.75.75 0 0 1 0 1.5H3.487A3.487 3.487 0 0 1 0 9.913v-.14C0 8.449.785 7.274 1.963 6.75A5.253 5.253 0 0 1 7.215 1.4h.206a4.992 4.992 0 0 1 4.586 3.024A4.455 4.455 0 0 1 16 8.848V8.9a.75.75 0 0 1-1.5 0Z"></path><path d="m8.38 7.67 2.25 2.25a.749.749 0 0 1 0 1.061L8.38 13.23a.749.749 0 1 1-1.06-1.06l1.719-1.72L7.32 8.731A.75.75 0 0 1 8.38 7.67ZM15 13.45h-3a.75.75 0 0 1 0-1.5h3a.75.75 0 0 1 0 1.5Z"></path></svg> in the navigation bar at the top right of GitHub.
2. Under the prompt box, select the agent app you want to use.
3. Type a prompt describing your request, then start the task.

## Starting an agent from an issue

You can assign an agent app to an issue in the same way you assign Copilot cloud agent.

1. Navigate to the issue you want the agent to work on.
2. In the sidebar, under "Assignees," assign the agent app to the issue.

The agent starts work on the issue and reports back on its progress.

## Starting an agent from a pull request comment

You can ask an agent app to make changes or perform other tasks by mentioning it in a pull request comment.

1. Navigate to the pull request you want the agent to work on.
2. Add a comment that mentions the agent and describes what you want it to do, for example `@AGENT-NAME add a feature flag for the new checkout flow`. Pick the agent from the autocomplete picker.

The agent responds to your comment and works on the requested changes.

## Using agent apps on GitHub Mobile

You can start agent apps from the same entry points on GitHub Mobile. For more information about using agents on mobile, see [Using Copilot cloud agent on GitHub Mobile](/en/copilot/how-tos/use-copilot-agents/cloud-agent/use-cloud-agent-on-mobile).

## Billing

Agent apps are powered by Copilot cloud agent. When you use an agent app, the AI usage is billed to your Copilot subscription, and sessions consume AI credits in the same way as Copilot cloud agent. See [GitHub Copilot billing](/en/billing/concepts/product-billing/github-copilot-billing).