# Using plan mode in your IDE

Have Copilot research a task and draft an implementation plan for your review before any code is changed.

## Introduction

Plan mode helps you to create detailed implementation plans before executing them. This ensures that all requirements are considered and addressed before any code changes are made. The plan agent does not make any code changes until the plan is reviewed and approved by you. Once approved, you can hand off the plan to the default agent or save it for further refinement, review, or team discussions.

The plan agent is designed to:

* Research the task comprehensively using read-only tools and codebase analysis to identify requirements and constraints.
* Break down the task into manageable, actionable steps and include open questions about ambiguous requirements.
* Present a concise plan draft, based on a standardized plan format, for user review and iteration.

Plan mode is available in Visual Studio Code, JetBrains IDEs, Xcode, and Eclipse. It is not currently available in Visual Studio. Click the tabs above for instructions for your editor.

To run a task without planning it first, see [Using agent mode in your IDE](/en/copilot/how-tos/copilot-in-your-ide/use-copilot-agents/use-agent-mode).

<!-- --------------------- -->

<!-- VS Code -->

<!-- --------------------- -->

<div class="ghd-tool vscode">

## Using the plan agent

1. If the chat view is not already displayed, select **Open Chat** from the Copilot Chat menu.

2. At the bottom of the chat view, select **Plan** from the agents dropdown.

3. Type a prompt that describes a task, such as adding a feature to an existing application, refactoring code, fixing a bug, or creating an initial version of a new application.

   For example: `Create a simple to-do web app with HTML, CSS, and JS files.`

   After a few moments, the plan agent outputs a plan in the chat view. The plan provides a high-level summary and a breakdown of steps, including any open questions for clarification.

4. Review the plan and answer any questions the agent has asked.

   You can iterate multiple times to clarify requirements, adjust scope, or answer questions.

5. Once the plan is complete you can:

   * Click **Start Implementation** to switch Copilot Chat to agent mode and start an agent session to implement the required changes, based on the implementation plan.
   * Click **Open in Editor** to switch Copilot Chat to agent mode and start an agent session that generates Markdown, in a tab of your editor, with the details of the implementation plan. You can start to work through the plan yourself, or save the plan as a Markdown file for later use.

For more information, see [Planning with agents in VS Code](https://code.visualstudio.com/docs/copilot/agents/planning) in the Visual Studio Code documentation.

## Further reading

* [Using agent mode in your IDE](/en/copilot/how-tos/copilot-in-your-ide/use-copilot-agents/use-agent-mode)
* [Asking GitHub Copilot questions in your IDE](/en/copilot/how-tos/copilot-in-your-ide/chat-with-copilot/chat-in-ide)

</div>

<!-- --------------------- -->

<!-- JetBrains -->

<!-- --------------------- -->

<div class="ghd-tool jetbrains">

## Using plan mode

1. If it is not already displayed, open the Copilot Chat panel by clicking the **GitHub Copilot Chat** icon at the right side of the JetBrains IDE window.

2. At the bottom of the Copilot Chat panel, select **Plan** from the agents dropdown.

3. Type a prompt that describes a task, such as adding a feature to an existing application, refactoring code, fixing a bug, or creating an initial version of a new application.

   For example: `Create a simple to-do web app with HTML, CSS, and JS files.`

4. Submit the prompt.

   After a few moments, the plan agent outputs a plan in the chat panel. The plan provides a high-level summary and a breakdown of steps, including any open questions for clarification.

5. Review the plan and answer any questions the agent has asked.

   You can iterate multiple times to clarify requirements, adjust scope, or answer questions.

6. Once the plan is complete you can:

   * Click **Start Implementation** to switch Copilot Chat to agent mode and start an agent session to implement the required changes, based on the implementation plan.
   * Click **Open in Editor** to switch Copilot Chat to agent mode and start an agent session that generates Markdown, in a tab of your editor, with the details of the implementation plan. You can start to work through the plan yourself, or save the plan as a Markdown file for later use.

## Further reading

* [Using agent mode in your IDE](/en/copilot/how-tos/copilot-in-your-ide/use-copilot-agents/use-agent-mode)
* [Asking GitHub Copilot questions in your IDE](/en/copilot/how-tos/copilot-in-your-ide/chat-with-copilot/chat-in-ide)

</div>

<!-- --------------------- -->

<!-- Xcode -->

<!-- --------------------- -->

<div class="ghd-tool xcode">

> \[!NOTE]
> Plan mode is currently in public preview and subject to change.

## Using plan mode

1. If it is not already displayed, open the Copilot Chat window by clicking **Editor** in the menu bar, then clicking **GitHub Copilot** then **Open Chat**.

2. At the bottom of the Copilot Chat window, select **Plan** from the agents dropdown.

3. Type a prompt that describes a task, such as adding a feature to an existing application, refactoring code, fixing a bug, or creating an initial version of a new application.

   For example: `Create a simple to-do app with Swift files.`

4. Submit the prompt.

   After a few moments, the plan agent outputs a plan in the chat panel. The plan provides a high-level summary and a breakdown of steps, including any open questions for clarification.

5. Review the plan and answer any questions the agent has asked.

   You can iterate multiple times to clarify requirements, adjust scope, or answer questions.

6. Once the plan is complete you can:

   * Click **Start Implementation** to switch Copilot Chat to agent mode and start an agent session to implement the required changes, based on the implementation plan.
   * Click **Open in Editor** to switch Copilot Chat to agent mode and start an agent session that generates Markdown, in a tab of your editor, with the details of the implementation plan. You can start to work through the plan yourself, or save the plan as a Markdown file for later use.

## Further reading

* [Using agent mode in your IDE](/en/copilot/how-tos/copilot-in-your-ide/use-copilot-agents/use-agent-mode)
* [Asking GitHub Copilot questions in your IDE](/en/copilot/how-tos/copilot-in-your-ide/chat-with-copilot/chat-in-ide)

</div>

<!-- --------------------- -->

<!-- Eclipse -->

<!-- --------------------- -->

<div class="ghd-tool eclipse">

> \[!NOTE]
> Plan mode is currently in public preview and subject to change.

## Using plan mode

1. If it is not already displayed, open the Copilot Chat panel by clicking the Copilot icon (<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copilot" aria-label="copilot" role="img"><path d="M7.998 15.035c-4.562 0-7.873-2.914-7.998-3.749V9.338c.085-.628.677-1.686 1.588-2.065.013-.07.024-.143.036-.218.029-.183.06-.384.126-.612-.201-.508-.254-1.084-.254-1.656 0-.87.128-1.769.693-2.484.579-.733 1.494-1.124 2.724-1.261 1.206-.134 2.262.034 2.944.765.05.053.096.108.139.165.044-.057.094-.112.143-.165.682-.731 1.738-.899 2.944-.765 1.23.137 2.145.528 2.724 1.261.566.715.693 1.614.693 2.484 0 .572-.053 1.148-.254 1.656.066.228.098.429.126.612.012.076.024.148.037.218.924.385 1.522 1.471 1.591 2.095v1.872c0 .766-3.351 3.795-8.002 3.795Zm0-1.485c2.28 0 4.584-1.11 5.002-1.433V7.862l-.023-.116c-.49.21-1.075.291-1.727.291-1.146 0-2.059-.327-2.71-.991A3.222 3.222 0 0 1 8 6.303a3.24 3.24 0 0 1-.544.743c-.65.664-1.563.991-2.71.991-.652 0-1.236-.081-1.727-.291l-.023.116v4.255c.419.323 2.722 1.433 5.002 1.433ZM6.762 2.83c-.193-.206-.637-.413-1.682-.297-1.019.113-1.479.404-1.713.7-.247.312-.369.789-.369 1.554 0 .793.129 1.171.308 1.371.162.181.519.379 1.442.379.853 0 1.339-.235 1.638-.54.315-.322.527-.827.617-1.553.117-.935-.037-1.395-.241-1.614Zm4.155-.297c-1.044-.116-1.488.091-1.681.297-.204.219-.359.679-.242 1.614.091.726.303 1.231.618 1.553.299.305.784.54 1.638.54.922 0 1.28-.198 1.442-.379.179-.2.308-.578.308-1.371 0-.765-.123-1.242-.37-1.554-.233-.296-.693-.587-1.713-.7Z"></path><path d="M6.25 9.037a.75.75 0 0 1 .75.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 .75-.75Zm4.25.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 1.5 0Z"></path></svg>) in the status bar at the bottom of Eclipse, then clicking **Open Chat**.

2. At the bottom of the chat panel, select **Plan** from the agents dropdown.

3. Type a prompt that describes a task, such as adding a feature to an existing application, refactoring code, fixing a bug, or creating an initial version of a new application.

   For example: `Create a simple to-do app using JavaFX.`

4. Submit the prompt.

   After a few moments, the plan agent outputs a plan in the chat panel. The plan provides a high-level summary and a breakdown of steps, including any open questions for clarification.

5. Review the plan and answer any questions the agent has asked.

   You can iterate multiple times to clarify requirements, adjust scope, or answer questions.

6. Once the plan is complete you can:

   * Click **Start Implementation** to switch Copilot Chat to agent mode and start an agent session to implement the required changes, based on the implementation plan.
   * Click **Open in Editor** to switch Copilot Chat to agent mode and start an agent session that generates Markdown, in a tab of your editor, with the details of the implementation plan. You can start to work through the plan yourself, or save the plan as a Markdown file for later use.

## Further reading

* [Using agent mode in your IDE](/en/copilot/how-tos/copilot-in-your-ide/use-copilot-agents/use-agent-mode)
* [Asking GitHub Copilot questions in your IDE](/en/copilot/how-tos/copilot-in-your-ide/chat-with-copilot/chat-in-ide)

</div>