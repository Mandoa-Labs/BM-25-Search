# Choosing a model in the Copilot app

Choose which large language model you want to use for a task in the Copilot app.

## Introduction

Copilot supports a range of AI models. Different models have different strengths. For example, some prioritize low latency, while others are optimized for complex reasoning or large context windows. You can choose the model you think best fits your needs for a particular task.

For details of models and their capabilities, see [Supported AI models in GitHub Copilot](/en/copilot/reference/ai-models/supported-models) and [AI model comparison](/en/copilot/reference/ai-models/model-comparison). The models available to you depend on your Copilot plan and your enterprise or organization settings.

## Identifying the currently selected model

Details of the currently selected model are displayed below the prompt box.

To see the model that was used for a completed response, hover over the response until the information icon (<span style="vertical-align: 2px"><svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-info" aria-label="the info icon" role="img"><path d="M0 8a8 8 0 1 1 16 0A8 8 0 0 1 0 8Zm8-6.5a6.5 6.5 0 1 0 0 13 6.5 6.5 0 0 0 0-13ZM6.5 7.75A.75.75 0 0 1 7.25 7h1a.75.75 0 0 1 .75.75v2.75h.25a.75.75 0 0 1 0 1.5h-2a.75.75 0 0 1 0-1.5h.25v-2h-.25a.75.75 0 0 1-.75-.75ZM8 6a1 1 0 1 1 0-2 1 1 0 0 1 0 2Z"></path></svg></span>) is displayed below the response. Hover over the information icon to view the model details. If multiple models were used during work on a task, the information box shows the model used by the main agent, not any subagents that were used.

## Choosing a model

You can choose which model you want to use at any point during a session. Your choice takes effect immediately if Copilot is currently idle, or when the current turn completes. The model will continue to be used for the remainder of the session, unless you change it again. Your choice becomes the default model for future sessions, but the model used in other existing sessions is not affected.

If you have installed local models, these are only available if you are currently in a local session. See [Adding LLM models to the GitHub Copilot app](/en/copilot/how-tos/github-copilot-app/add-llm-models).

1. Click the current model choice, shown below the prompt box.

2. To use Copilot Fusion:

   1. Toggle the **Copilot Fusion** switch to the on position.

   2. Choose an effort level:

      * **Fusion Standard** – Prioritizes versatile models for everyday coding.
      * **Fusion High** – Prioritizes capable models for challenging tasks and deeper reasoning.
      * **Fusion Max** – Prioritizes the most capable models for the most demanding tasks and complex reasoning.response times.

   3. Click outside the dialog to dismiss it.

   When you choose the **Copilot Fusion** option, Copilot analyzes each task and selects a model to complete it, orchestrating multiple models through execution patterns when needed. For more information, see [About GitHub Copilot Fusion](/en/copilot/concepts/models/copilot-fusion).

3. To choose a specific model:
   1. Toggle the **Copilot Fusion** switch to the off position.

   2. Hover over the current model choice in the dialog and click to select a different model from the list that's displayed.

   3. Depending on the model you choose, additional options for effort level and context window size may be available.

      Select the appropriate options based on your needs.

   4. Click outside the dialog to dismiss it.

## Further reading

* [Models in GitHub Copilot](/en/copilot/concepts/models/overview)
* [Adding LLM models to the GitHub Copilot app](/en/copilot/how-tos/github-copilot-app/add-llm-models)