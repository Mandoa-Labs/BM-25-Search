# Agent management

Use one centralized control page to jump between agent sessions, check progress, and stay in control without losing your place.

## About agents

AI agents are autonomous systems that can evaluate their environment, make decisions, and take actions to complete tasks. Agents can break down complex tasks into steps, use various tools and resources, plan their approach, and adapt based on human feedback until they accomplish their assigned objective.

Agents bring automation and assistance to every stage of the software development process on GitHub. You can run multiple agent sessions concurrently, allowing you to efficiently delegate work items.

Alongside Copilot, you can use Anthropic Claude and OpenAI Codex, giving you more flexibility and choice to find the right agent for a task. See [Third-party coding agents](/en/copilot/concepts/agent-capabilities/about-agents/about-third-party-coding-agents).

GitHub partners can also offer their own agents as agent apps, which you install as GitHub Apps and trigger from issues, pull requests, and the Agents UI. See [Agent apps](/en/copilot/concepts/agent-capabilities/about-agents/agent-apps).

Utilizing custom agents you can build out a team of task-specific agents with customized system prompts to handle simpler tasks like writing tests and refactoring, giving you bandwidth to prioritize problem-solving and collaboration. See [About custom agents](/en/copilot/concepts/agents/cloud-agent/about-custom-agents).

Model choice allows you to choose from a selection of AI models to use with your agents, each with its own particular strengths. See [Supported AI models in GitHub Copilot](/en/copilot/reference/ai-models/supported-models).

To learn more about Copilot cloud agent, see [GitHub Copilot on GitHub.com](/en/copilot/concepts/copilot-surfaces/copilot-on-github).

## Managing agents

When utilizing GitHub's agentic features, you can use the **Agents** tab within a repository that has Copilot cloud agent enabled to initiate, monitor, and manage agent sessions without leaving your workflow. You can also use the [Agents page](https://github.com/copilot/agents?ref_product=copilot\&ref_type=engagement\&ref_style=text) to view and start agent sessions. To learn how to enable Copilot cloud agent, see [Managing access to GitHub Copilot cloud agent](/en/copilot/concepts/enterprise/cloud-agent-access).

From the Agents tab, you can:

* **Kick off new agent tasks**: Select an AI model of your choice, and optionally choose from third-party agents or custom agents best suited for the task. See [Starting GitHub Copilot sessions](/en/copilot/how-tos/use-copilot-agents/cloud-agent/start-copilot-sessions).
* **Monitor live session logs**: Once the agent starts working, you can click any agent session to open the session log and follow its progress and thought process in real time.
* **Track active sessions**: You can view all active agent sessions that have been started in the repository.
* **Steer agents mid-session**: If you realize you didn't scope a request correctly, or want the agent to use a specific tool or service, you can step in and provide **steering input** without stopping the run. Steering consumes AI credits per message. See [Managing agent sessions](/en/copilot/how-tos/copilot-on-github/use-copilot-agents/manage-and-track-agents#steer-an-agent-session).
* **Open a session in VS Code or GitHub Copilot CLI**: When you want to start working on changes to an agent session in your local development environment, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-vscode" aria-label="VS Code" role="img"><path d="M10.863 13.919a.796.796 0 0 1-.644.025.795.795 0 0 1-.279-.183L4.816 9.063l-2.232 1.703a.54.54 0 0 1-.691-.031l-.716-.655a.546.546 0 0 1 0-.805L3.112 7.5 1.177 5.725a.546.546 0 0 1 0-.805l.716-.655a.54.54 0 0 1 .691-.031l2.232 1.703L9.94 1.239a.805.805 0 0 1 .923-.159l2.677 1.295c.281.136.46.422.46.736V8h-3.248V4.534L6.864 7.5l3.888 2.966V8H14v3.889c0 .314-.179.6-.46.736l-2.677 1.294Z"></path></svg> Open in VS Code** or **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-agent" aria-label="Agent" role="img"><path d="M14.5 8.9v-.052A2.956 2.956 0 0 0 11.542 5.9a.815.815 0 0 1-.751-.501l-.145-.348A3.496 3.496 0 0 0 7.421 2.9h-.206a3.754 3.754 0 0 0-3.736 4.118l.011.121a.822.822 0 0 1-.619.879A1.81 1.81 0 0 0 1.5 9.773v.14c0 1.097.89 1.987 1.987 1.987H4.5a.75.75 0 0 1 0 1.5H3.487A3.487 3.487 0 0 1 0 9.913v-.14C0 8.449.785 7.274 1.963 6.75A5.253 5.253 0 0 1 7.215 1.4h.206a4.992 4.992 0 0 1 4.586 3.024A4.455 4.455 0 0 1 16 8.848V8.9a.75.75 0 0 1-1.5 0Z"></path><path d="m8.38 7.67 2.25 2.25a.749.749 0 0 1 0 1.061L8.38 13.23a.749.749 0 1 1-1.06-1.06l1.719-1.72L7.32 8.731A.75.75 0 0 1 8.38 7.67ZM15 13.45h-3a.75.75 0 0 1 0-1.5h3a.75.75 0 0 1 0 1.5Z"></path></svg> Continue in GitHub Copilot CLI** to bring the session to your local machine.
  > \[!NOTE]
  > Opening a session in VS Code requires the latest versions of VS Code, the GitHub Copilot extension, and the GitHub Pull Requests extension.
* **Review and merge agent code**: Once the agent completes a session, you can jump to the pull request to review the changes, request further improvements, or approve and merge. See [Review output from Copilot](/en/copilot/how-tos/copilot-on-github/use-copilot-agents/review-copilot-output).
* **Set up automations**: Run Copilot cloud agent automatically, on a schedule or in response to events such as an issue being opened. See [Copilot automations](/en/copilot/concepts/agent-capabilities/agent-powered-workflows-and-operations/about-automations).
* **Query your past sessions**: You can search and reference your past agent sessions using natural language from Copilot CLI or VS Code. See [About GitHub Copilot session data](/en/copilot/concepts/security-governance-and-network-settings/session-data).

## Next steps

To start managing agents, see [Managing agent sessions](/en/copilot/how-tos/copilot-on-github/use-copilot-agents/manage-and-track-agents).