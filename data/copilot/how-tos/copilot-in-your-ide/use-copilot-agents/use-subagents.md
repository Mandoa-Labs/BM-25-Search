# Using subagents in your IDE

Delegate a self-contained subtask to a separate agent that works in its own context and reports back to your main chat session.

## Introduction

You can use subagents to delegate tasks to an isolated agent with its own context window within your chat session. The subagent operates independently without pausing for user feedback and returns the final result to the main chat session.

Subagents are best suited for situations where:

* You want to delegate complex, multi-step tasks like research or analysis without interrupting your main session.
* You need to process large amounts of information or multiple documents that would clutter your primary context window.
* You want to explore different approaches or perspectives independently without mixing contexts together.

Subagents use the same tools and AI model as the main session, but they cannot create other subagents.

Subagents are available in Visual Studio Code, JetBrains IDEs, Xcode, and Eclipse. They are not currently available in Visual Studio. The steps to enable and invoke them differ by editor, so click the tabs above for instructions for your IDE.

For the agent session that subagents are delegated from, see [Using agent mode in your IDE](/en/copilot/how-tos/copilot-in-your-ide/use-copilot-agents/use-agent-mode).

<!-- --------------------- -->

<!-- VS Code -->

<!-- --------------------- -->

<div class="ghd-tool vscode">

## Enabling subagents

1. In the Copilot Chat window, click the tools icon.
2. Enable the `runSubagent` tool.

If you use custom prompt files or custom agents, ensure you specify the `runSubagent` tool in the `tools` frontmatter property. See [Creating custom agents for Copilot cloud agent](/en/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/create-custom-agents#configuring-an-agent-profile), and [Use prompt files in VS Code](https://code.visualstudio.com/docs/copilot/customization/prompt-files) in the Visual Studio Code documentation.

## Invoking subagents

Subagents can be invoked in different ways:

* **Automatic delegation**. Copilot will analyze the description of your request, the description field of your configured custom agents, and the current context and available tools to automatically choose a subagent. For example, this prompt would automatically delegate the task to a **refactor-specialist** custom agent:

  ```text
  Suggest ways to refactor this legacy code.
  ```

* **Direct invocation**. You can directly call the subagent in your prompt:

  ```text
  Use the testing subagent to write unit tests for the authentication module.
  ```

* **Calling the #runSubagent tool.**

  ```text
  Evaluate the #file:databaseSchema using #runSubagent and generate an optimized data-migration plan.
  ```

When the subagent completes its task, its results appear back in the main chat session, ready for follow-up questions or next steps.

## Further reading

* [Using agent mode in your IDE](/en/copilot/how-tos/copilot-in-your-ide/use-copilot-agents/use-agent-mode)
* [Copilot customization cheat sheet](/en/copilot/reference/customization-cheat-sheet)

</div>

<!-- --------------------- -->

<!-- JetBrains -->

<!-- --------------------- -->

<div class="ghd-tool jetbrains">

To use subagents, you **must have custom agents configured in your environment**. See [Using custom agents in your IDE](/en/copilot/how-tos/copilot-in-your-ide/use-copilot-agents/use-custom-agents).

## Enabling subagents

1. Click **Tools** in the menu bar, then click **GitHub Copilot**, then **Edit Settings**.
2. In the popup menu, click **Chat**, then click the **Enable Subagent** checkbox.

## Invoking subagents

Subagents can be invoked in different ways:

* **Automatic delegation**. Copilot will analyze the description of your request, the description field of your configured custom agents, and the current context and available tools to automatically choose a subagent. For example, this prompt would automatically delegate the task to a **refactor-specialist** custom agent:

  ```text
  Suggest ways to refactor this legacy code.
  ```

* **Direct invocation**. You can directly call the subagent in your prompt:

  ```text
  Use the testing subagent to write unit tests for the authentication module.
  ```

When the subagent completes its task, its results appear back in the main chat session, ready for follow-up questions or next steps.

## Further reading

* [Using agent mode in your IDE](/en/copilot/how-tos/copilot-in-your-ide/use-copilot-agents/use-agent-mode)
* [Copilot customization cheat sheet](/en/copilot/reference/customization-cheat-sheet)

</div>

<!-- --------------------- -->

<!-- Xcode -->

<!-- --------------------- -->

<div class="ghd-tool xcode">

To use subagents, you **must have custom agents configured in your environment**. See [Using custom agents in your IDE](/en/copilot/how-tos/copilot-in-your-ide/use-copilot-agents/use-custom-agents).

## Enabling subagents

1. Click **Editor** in the menu bar, then click **GitHub Copilot** then **Open GitHub Copilot for Xcode Settings**.
2. Click **Advanced** in the chat panel, then under **Chat Settings** click the **Enable Subagents** toggle.

## Invoking subagents

Subagents can be invoked in different ways:

* **Automatic delegation**. Copilot will analyze the description of your request, the description field of your configured custom agents, and the current context and available tools to automatically choose a subagent. For example, this prompt would automatically delegate the task to a **refactor-specialist** custom agent:

  ```text
  Suggest ways to refactor this legacy code.
  ```

* **Direct invocation**. You can directly call the subagent in your prompt:

  ```text
  Use the testing subagent to write unit tests for the authentication module.
  ```

When the subagent completes its task, its results appear back in the main chat session, ready for follow-up questions or next steps.

## Further reading

* [Using agent mode in your IDE](/en/copilot/how-tos/copilot-in-your-ide/use-copilot-agents/use-agent-mode)
* [Copilot customization cheat sheet](/en/copilot/reference/customization-cheat-sheet)

</div>

<!-- --------------------- -->

<!-- Eclipse -->

<!-- --------------------- -->

<div class="ghd-tool eclipse">

To use subagents, you **must have custom agents configured in your environment**. See [Using custom agents in your IDE](/en/copilot/how-tos/copilot-in-your-ide/use-copilot-agents/use-custom-agents).

## Enabling subagents

1. Click the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copilot" aria-label="copilot" role="img"><path d="M7.998 15.035c-4.562 0-7.873-2.914-7.998-3.749V9.338c.085-.628.677-1.686 1.588-2.065.013-.07.024-.143.036-.218.029-.183.06-.384.126-.612-.201-.508-.254-1.084-.254-1.656 0-.87.128-1.769.693-2.484.579-.733 1.494-1.124 2.724-1.261 1.206-.134 2.262.034 2.944.765.05.053.096.108.139.165.044-.057.094-.112.143-.165.682-.731 1.738-.899 2.944-.765 1.23.137 2.145.528 2.724 1.261.566.715.693 1.614.693 2.484 0 .572-.053 1.148-.254 1.656.066.228.098.429.126.612.012.076.024.148.037.218.924.385 1.522 1.471 1.591 2.095v1.872c0 .766-3.351 3.795-8.002 3.795Zm0-1.485c2.28 0 4.584-1.11 5.002-1.433V7.862l-.023-.116c-.49.21-1.075.291-1.727.291-1.146 0-2.059-.327-2.71-.991A3.222 3.222 0 0 1 8 6.303a3.24 3.24 0 0 1-.544.743c-.65.664-1.563.991-2.71.991-.652 0-1.236-.081-1.727-.291l-.023.116v4.255c.419.323 2.722 1.433 5.002 1.433ZM6.762 2.83c-.193-.206-.637-.413-1.682-.297-1.019.113-1.479.404-1.713.7-.247.312-.369.789-.369 1.554 0 .793.129 1.171.308 1.371.162.181.519.379 1.442.379.853 0 1.339-.235 1.638-.54.315-.322.527-.827.617-1.553.117-.935-.037-1.395-.241-1.614Zm4.155-.297c-1.044-.116-1.488.091-1.681.297-.204.219-.359.679-.242 1.614.091.726.303 1.231.618 1.553.299.305.784.54 1.638.54.922 0 1.28-.198 1.442-.379.179-.2.308-.578.308-1.371 0-.765-.123-1.242-.37-1.554-.233-.296-.693-.587-1.713-.7Z"></path><path d="M6.25 9.037a.75.75 0 0 1 .75.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 .75-.75Zm4.25.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 1.5 0Z"></path></svg>** icon in the status bar.
2. In the popup menu, click **Edit Preferences**.
3. Under **Chat**, click the **Enable sub-agent** check box.

## Invoking subagents

Subagents can be invoked in different ways:

* **Automatic delegation**. Copilot will analyze the description of your request, the description field of your configured custom agents, and the current context and available tools to automatically choose a subagent. For example, this prompt would automatically delegate the task to a **refactor-specialist** custom agent:

  ```text
  Suggest ways to refactor this legacy code.
  ```

* **Direct invocation**. You can directly call the subagent in your prompt:

  ```text
  Use the testing subagent to write unit tests for the authentication module.
  ```

When the subagent completes its task, its results appear back in the main chat session, ready for follow-up questions or next steps.

## Further reading

* [Using agent mode in your IDE](/en/copilot/how-tos/copilot-in-your-ide/use-copilot-agents/use-agent-mode)
* [Copilot customization cheat sheet](/en/copilot/reference/customization-cheat-sheet)

</div>