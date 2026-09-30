# Using agent mode in your IDE

Give Copilot a task and let it work autonomously in your editor, editing files across your project and running commands until the task is complete.

## Introduction

In agent mode, Copilot takes a high-level task, decides which files to change, makes the edits, and runs commands as needed, iterating until the task is done. You stay in control: you review the changes, and by default you approve commands before they run. Your administrator, or your own editor settings, may allow some commands to run automatically.

Agent mode is available in Visual Studio Code, Visual Studio, JetBrains IDEs, Xcode, and Eclipse. The steps differ by editor, so click the tabs above for instructions for your IDE.

For how to open Copilot Chat and choose between the available modes, see [Asking GitHub Copilot questions in your IDE](/en/copilot/how-tos/copilot-in-your-ide/chat-with-copilot/chat-in-ide).

<!-- --------------------- -->

<!-- VS Code -->

<!-- --------------------- -->

<div class="ghd-tool vscode">

Use agent mode when you have a specific task in mind and want to enable Copilot to autonomously edit your code. In agent mode, Copilot determines which files to make changes to, offers code changes and terminal commands to complete the task, and iterates to remediate issues until the original task is complete.

Agent mode is best suited to use cases where:

* Your task is complex, and involves multiple steps, iterations, and error handling.
* You want Copilot to determine the necessary steps to take to complete the task.
* The task requires Copilot to integrate with external applications, such as an MCP server.

## Using agents

1. If the chat view is not already displayed, select **Open Chat** from the Copilot Chat menu.
2. At the bottom of the chat view, ensure **Agent** is selected from the agents dropdown.
3. Submit a prompt. In response to your prompt, Copilot streams the edits in the editor, updates the working set, and runs terminal commands if necessary.
4. Review and iterate on changes or run a code review.

You can also [click this link](vscode://GitHub.Copilot-Chat/chat?mode=agent\&ref_product=copilot\&ref_type=engagement\&ref_style=text) to go directly to agent mode in VS Code. <!-- markdownlint-disable-line GHD003 -->

> \[!NOTE]
> If you don’t see the **Agent** option in the mode selector, your enterprise or organization administrator may have disabled agent mode for your IDE.

For more information, see [Chat overview](https://aka.ms/vscode-copilot-agent) in the Visual Studio Code documentation.

When you use agent mode, each prompt you enter consumes GitHub AI Credits.

## Steering an agent while it works

Agent mode is interactive. While Copilot is working, you can:

* Submit a follow-up prompt to redirect the agent before it finishes.
* Confirm or reject each terminal command the agent proposes, unless it has been configured to run automatically.
* Review streamed edits as they appear and undo any you do not want.

If a task is large or ambiguous, consider drafting an implementation plan first. See [Using plan mode in your IDE](/en/copilot/how-tos/copilot-in-your-ide/use-copilot-agents/use-plan-mode).

## Choosing a model or a custom agent

Before you submit a task, you can change which AI model the agent uses, or select a custom agent tailored to a specific kind of work.

* To change the model, see [Changing the AI model for GitHub Copilot Chat](/en/copilot/how-tos/copilot-in-your-ide/chat-with-copilot/change-the-chat-model).
* To select a custom agent, see [Using custom agents in your IDE](/en/copilot/how-tos/copilot-in-your-ide/use-copilot-agents/use-custom-agents).

## Extending agent mode with tools

Much of agent mode's capability comes from the tools it can call. You can extend the agent with Model Context Protocol (MCP) servers, which add tools for working with external systems and with GitHub itself.

* To set up MCP servers in your IDE, see [Extending GitHub Copilot Chat with Model Context Protocol (MCP) servers](/en/copilot/how-tos/copilot-in-your-ide/customize-copilot/extend-copilot-with-tools-and-context/extend-copilot-chat-with-mcp).
* To work with GitHub from your editor, see [Using the GitHub MCP Server in your IDE](/en/copilot/how-tos/copilot-in-your-ide/copilot-for-common-tasks/use-the-github-mcp-server).
* For a worked example, see [Enhancing GitHub Copilot agent mode with MCP](/en/copilot/tutorials/enhance-agent-mode-with-mcp).

To hand a self-contained subtask to a separate agent with its own context, see [Using subagents in your IDE](/en/copilot/how-tos/copilot-in-your-ide/use-copilot-agents/use-subagents).

## Further reading

* [Asking GitHub Copilot questions in your IDE](/en/copilot/how-tos/copilot-in-your-ide/chat-with-copilot/chat-in-ide)
* [About GitHub Copilot Chat](/en/copilot/concepts/chat)

</div>

<!-- --------------------- -->

<!-- Visual Studio -->

<!-- --------------------- -->

<div class="ghd-tool visualstudio">

Use agent mode when you have a specific task in mind and want to enable Copilot to autonomously edit your code. In agent mode, Copilot determines which files to make changes to, offers code changes and terminal commands to complete the task, and iterates to remediate issues until the original task is complete.

Agent mode is available in Visual Studio 17.14 and later.

## Using agent mode

1. In the Visual Studio menu bar, click **View**, then click **GitHub Copilot Chat**.
2. At the bottom of the chat panel, select **Agent** from the mode dropdown.
3. Submit a prompt. In response to your prompt, Copilot streams the edits in the editor, updates the working set, and if necessary, suggests terminal commands to run.
4. Review the changes. If Copilot suggested terminal commands, confirm whether or not Copilot can run them. In response, Copilot iterates and performs additional actions to complete the task in your original prompt.

When you use Copilot agent mode, each prompt you enter consumes GitHub AI Credits.

## Choosing a model

Before you submit a task, you can change which AI model the agent uses. See [Changing the AI model for GitHub Copilot Chat](/en/copilot/how-tos/copilot-in-your-ide/chat-with-copilot/change-the-chat-model).

## Extending agent mode with tools

You can extend the agent with Model Context Protocol (MCP) servers, which add tools for working with external systems and with GitHub itself.

* To set up MCP servers in your IDE, see [Extending GitHub Copilot Chat with Model Context Protocol (MCP) servers](/en/copilot/how-tos/copilot-in-your-ide/customize-copilot/extend-copilot-with-tools-and-context/extend-copilot-chat-with-mcp).
* To work with GitHub from your editor, see [Using the GitHub MCP Server in your IDE](/en/copilot/how-tos/copilot-in-your-ide/copilot-for-common-tasks/use-the-github-mcp-server).

## Further reading

* [Asking GitHub Copilot questions in your IDE](/en/copilot/how-tos/copilot-in-your-ide/chat-with-copilot/chat-in-ide)
* [About GitHub Copilot Chat](/en/copilot/concepts/chat)

</div>

<!-- --------------------- -->

<!-- JetBrains -->

<!-- --------------------- -->

<div class="ghd-tool jetbrains">

Use agent mode when you have a specific task in mind and want to enable Copilot to autonomously edit your code. In agent mode, Copilot determines which files to make changes to, offers code changes and terminal commands to complete the task, and iterates to remediate issues until the original task is complete.

Agent mode is best suited to use cases where:

* Your task is complex, and involves multiple steps, iterations, and error handling.
* You want Copilot to determine the necessary steps to take to complete the task.
* The task requires Copilot to integrate with external applications, such as an MCP server.

## Using agent mode

1. To start an edit session using agent mode, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copilot" aria-label="copilot" role="img"><path d="M7.998 15.035c-4.562 0-7.873-2.914-7.998-3.749V9.338c.085-.628.677-1.686 1.588-2.065.013-.07.024-.143.036-.218.029-.183.06-.384.126-.612-.201-.508-.254-1.084-.254-1.656 0-.87.128-1.769.693-2.484.579-.733 1.494-1.124 2.724-1.261 1.206-.134 2.262.034 2.944.765.05.053.096.108.139.165.044-.057.094-.112.143-.165.682-.731 1.738-.899 2.944-.765 1.23.137 2.145.528 2.724 1.261.566.715.693 1.614.693 2.484 0 .572-.053 1.148-.254 1.656.066.228.098.429.126.612.012.076.024.148.037.218.924.385 1.522 1.471 1.591 2.095v1.872c0 .766-3.351 3.795-8.002 3.795Zm0-1.485c2.28 0 4.584-1.11 5.002-1.433V7.862l-.023-.116c-.49.21-1.075.291-1.727.291-1.146 0-2.059-.327-2.71-.991A3.222 3.222 0 0 1 8 6.303a3.24 3.24 0 0 1-.544.743c-.65.664-1.563.991-2.71.991-.652 0-1.236-.081-1.727-.291l-.023.116v4.255c.419.323 2.722 1.433 5.002 1.433ZM6.762 2.83c-.193-.206-.637-.413-1.682-.297-1.019.113-1.479.404-1.713.7-.247.312-.369.789-.369 1.554 0 .793.129 1.171.308 1.371.162.181.519.379 1.442.379.853 0 1.339-.235 1.638-.54.315-.322.527-.827.617-1.553.117-.935-.037-1.395-.241-1.614Zm4.155-.297c-1.044-.116-1.488.091-1.681.297-.204.219-.359.679-.242 1.614.091.726.303 1.231.618 1.553.299.305.784.54 1.638.54.922 0 1.28-.198 1.442-.379.179-.2.308-.578.308-1.371 0-.765-.123-1.242-.37-1.554-.233-.296-.693-.587-1.713-.7Z"></path><path d="M6.25 9.037a.75.75 0 0 1 .75.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 .75-.75Zm4.25.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 1.5 0Z"></path></svg> Copilot** in the menu bar, then select **Open GitHub Copilot Chat**.
2. At the top of the chat panel, click the **Agent** tab.
3. Submit a prompt. In response to your prompt, Copilot streams the edits in the editor, updates the working set, and if necessary, suggests terminal commands to run.
4. Review the changes. If Copilot suggested terminal commands, confirm whether or not Copilot can run them. In response, Copilot iterates and performs additional actions to complete the task in your original prompt.

When you use agent mode, each prompt you enter consumes GitHub AI Credits.

## Steering an agent while it works

Agent mode is interactive. While Copilot is working, you can submit a follow-up prompt to redirect the agent, and confirm or reject each terminal command it proposes.

If a task is large or ambiguous, consider drafting an implementation plan first. See [Using plan mode in your IDE](/en/copilot/how-tos/copilot-in-your-ide/use-copilot-agents/use-plan-mode).

## Choosing a model or a custom agent

Before you submit a task, you can change which AI model the agent uses, or select a custom agent tailored to a specific kind of work.

* To change the model, see [Changing the AI model for GitHub Copilot Chat](/en/copilot/how-tos/copilot-in-your-ide/chat-with-copilot/change-the-chat-model).
* To select a custom agent, see [Using custom agents in your IDE](/en/copilot/how-tos/copilot-in-your-ide/use-copilot-agents/use-custom-agents).

## Extending agent mode with tools

You can extend the agent with Model Context Protocol (MCP) servers, which add tools for working with external systems and with GitHub itself.

* To set up MCP servers in your IDE, see [Extending GitHub Copilot Chat with Model Context Protocol (MCP) servers](/en/copilot/how-tos/copilot-in-your-ide/customize-copilot/extend-copilot-with-tools-and-context/extend-copilot-chat-with-mcp).
* To work with GitHub from your editor, see [Using the GitHub MCP Server in your IDE](/en/copilot/how-tos/copilot-in-your-ide/copilot-for-common-tasks/use-the-github-mcp-server).

To hand a self-contained subtask to a separate agent with its own context, see [Using subagents in your IDE](/en/copilot/how-tos/copilot-in-your-ide/use-copilot-agents/use-subagents).

## Further reading

* [Asking GitHub Copilot questions in your IDE](/en/copilot/how-tos/copilot-in-your-ide/chat-with-copilot/chat-in-ide)
* [About GitHub Copilot Chat](/en/copilot/concepts/chat)

</div>

<!-- --------------------- -->

<!-- Xcode -->

<!-- --------------------- -->

<div class="ghd-tool xcode">

Use agent mode when you have a specific task in mind and want to enable Copilot to autonomously edit your code. In agent mode, Copilot determines which files to make changes to, offers code changes and terminal commands to complete the task, and iterates to remediate issues until the original task is complete.

Agent mode is best suited to use cases where:

* Your task is complex, and involves multiple steps, iterations, and error handling.
* You want Copilot to determine the necessary steps to take to complete the task.
* The task requires Copilot to integrate with external applications, such as an MCP server.

## Using agent mode

1. If it is not already displayed, open the Copilot Chat window by clicking **Editor** in the menu bar, then clicking **GitHub Copilot** then **Open Chat**.
2. At the bottom of the chat panel, select **Agent** from the agents dropdown.
3. Optionally, add relevant files to the *working set* view to indicate to Copilot which files you want to work on.
4. Submit a prompt. In response to your prompt, Copilot streams the edits in the editor, updates the working set, and if necessary, suggests terminal commands to run.
5. Review the changes. If Copilot suggested terminal commands, confirm whether or not Copilot can run them. In response, Copilot iterates and performs additional actions to complete the task in your original prompt.

When you use agent mode, each prompt you enter consumes GitHub AI Credits.

## Steering an agent while it works

Agent mode is interactive. While Copilot is working, you can submit a follow-up prompt to redirect the agent, and confirm or reject each terminal command it proposes.

If a task is large or ambiguous, consider drafting an implementation plan first. See [Using plan mode in your IDE](/en/copilot/how-tos/copilot-in-your-ide/use-copilot-agents/use-plan-mode).

## Choosing a model

Before you submit a task, you can change which AI model the agent uses. See [Changing the AI model for GitHub Copilot Chat](/en/copilot/how-tos/copilot-in-your-ide/chat-with-copilot/change-the-chat-model).

To hand a self-contained subtask to a separate agent with its own context, see [Using subagents in your IDE](/en/copilot/how-tos/copilot-in-your-ide/use-copilot-agents/use-subagents).

## Further reading

* [Asking GitHub Copilot questions in your IDE](/en/copilot/how-tos/copilot-in-your-ide/chat-with-copilot/chat-in-ide)
* [About GitHub Copilot Chat](/en/copilot/concepts/chat)

</div>

<!-- --------------------- -->

<!-- Eclipse -->

<!-- --------------------- -->

<div class="ghd-tool eclipse">

Use agent mode when you have a specific task in mind and want to enable Copilot to autonomously edit your code. In agent mode, Copilot determines which files to make changes to, offers code changes and terminal commands to complete the task, and iterates to remediate issues until the original task is complete.

Agent mode is best suited to use cases where:

* Your task is complex, and involves multiple steps, iterations, and error handling.
* You want Copilot to determine the necessary steps to take to complete the task.
* The task requires Copilot to integrate with external applications, such as an MCP server.

## Using agent mode

1. Open the Copilot Chat panel by clicking the Copilot icon (<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copilot" aria-label="copilot" role="img"><path d="M7.998 15.035c-4.562 0-7.873-2.914-7.998-3.749V9.338c.085-.628.677-1.686 1.588-2.065.013-.07.024-.143.036-.218.029-.183.06-.384.126-.612-.201-.508-.254-1.084-.254-1.656 0-.87.128-1.769.693-2.484.579-.733 1.494-1.124 2.724-1.261 1.206-.134 2.262.034 2.944.765.05.053.096.108.139.165.044-.057.094-.112.143-.165.682-.731 1.738-.899 2.944-.765 1.23.137 2.145.528 2.724 1.261.566.715.693 1.614.693 2.484 0 .572-.053 1.148-.254 1.656.066.228.098.429.126.612.012.076.024.148.037.218.924.385 1.522 1.471 1.591 2.095v1.872c0 .766-3.351 3.795-8.002 3.795Zm0-1.485c2.28 0 4.584-1.11 5.002-1.433V7.862l-.023-.116c-.49.21-1.075.291-1.727.291-1.146 0-2.059-.327-2.71-.991A3.222 3.222 0 0 1 8 6.303a3.24 3.24 0 0 1-.544.743c-.65.664-1.563.991-2.71.991-.652 0-1.236-.081-1.727-.291l-.023.116v4.255c.419.323 2.722 1.433 5.002 1.433ZM6.762 2.83c-.193-.206-.637-.413-1.682-.297-1.019.113-1.479.404-1.713.7-.247.312-.369.789-.369 1.554 0 .793.129 1.171.308 1.371.162.181.519.379 1.442.379.853 0 1.339-.235 1.638-.54.315-.322.527-.827.617-1.553.117-.935-.037-1.395-.241-1.614Zm4.155-.297c-1.044-.116-1.488.091-1.681.297-.204.219-.359.679-.242 1.614.091.726.303 1.231.618 1.553.299.305.784.54 1.638.54.922 0 1.28-.198 1.442-.379.179-.2.308-.578.308-1.371 0-.765-.123-1.242-.37-1.554-.233-.296-.693-.587-1.713-.7Z"></path><path d="M6.25 9.037a.75.75 0 0 1 .75.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 .75-.75Zm4.25.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 1.5 0Z"></path></svg>) in the status bar at the bottom of Eclipse, then clicking **Open Chat**.
2. At the bottom of the chat panel, select **Agent** from the agents dropdown.
3. Submit a prompt. In response to your prompt, Copilot streams the edits in the editor, updates the working set, and if necessary, suggests terminal commands to run.
4. Review the changes. If Copilot suggested terminal commands, confirm whether or not Copilot can run them. In response, Copilot iterates and performs additional actions to complete the task in your original prompt.

When you use agent mode, each prompt you enter consumes GitHub AI Credits.

## Steering an agent while it works

Agent mode is interactive. While Copilot is working, you can submit a follow-up prompt to redirect the agent, and confirm or reject each terminal command it proposes.

If a task is large or ambiguous, consider drafting an implementation plan first. See [Using plan mode in your IDE](/en/copilot/how-tos/copilot-in-your-ide/use-copilot-agents/use-plan-mode).

## Choosing a model

Before you submit a task, you can change which AI model the agent uses. See [Changing the AI model for GitHub Copilot Chat](/en/copilot/how-tos/copilot-in-your-ide/chat-with-copilot/change-the-chat-model).

To hand a self-contained subtask to a separate agent with its own context, see [Using subagents in your IDE](/en/copilot/how-tos/copilot-in-your-ide/use-copilot-agents/use-subagents).

## Further reading

* [Asking GitHub Copilot questions in your IDE](/en/copilot/how-tos/copilot-in-your-ide/chat-with-copilot/chat-in-ide)
* [About GitHub Copilot Chat](/en/copilot/concepts/chat)

</div>