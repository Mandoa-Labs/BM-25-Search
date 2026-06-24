# Using your own LLM models in the GitHub Copilot app

Connect a model from an external provider of your choice by supplying your own API key, then use the model in agent sessions.

> \[!NOTE]
> Support to use your own provider (BYOK) in the GitHub Copilot app is in public preview and subject to change.

You can configure the GitHub Copilot app to use your own LLM provider, also called BYOK (Bring Your Own Key), instead of GitHub-hosted models.

> \[!NOTE]
> This article is for users who want to configure their own LLM provider API key on their local machine. To set up custom models for users in an organization or enterprise, see [Using your LLM provider API keys with Copilot](/en/copilot/how-tos/administer-copilot/manage-for-organization/use-your-own-api-keys) and [Using your LLM provider API keys with Copilot](/en/copilot/how-tos/administer-copilot/manage-for-enterprise/use-your-own-api-keys).

## Supported providers

GitHub Copilot app supports these model providers:

* OpenAI
* Azure OpenAI
* Microsoft Foundry
* Anthropic
* Ollama
* Foundry Local
* LM Studio
* Any OpenAI-compatible HTTP endpoint

## Prerequisites

* The GitHub Copilot app is installed. For setup steps, see [Getting started with the GitHub Copilot app](/en/copilot/how-tos/github-copilot-app/getting-started).
* You have an API key for your model provider.

## Add a model provider

1. Open the GitHub Copilot app.
2. Open app settings, then click **Model providers**.
3. Click **Add provider**.
4. Select your provider.
5. Enter the provider details. This varies by provider but may include the display name, base URL, and API key.
6. Click **Add provider** to save the provider.

After you add a provider, its models appear in the model picker alongside GitHub-hosted models. You can select the model and use it in a session. For more information, see [Working with agent sessions in the GitHub Copilot app](/en/copilot/how-tos/github-copilot-app/agent-sessions).

Keys are stored in the system credential store and are never displayed in the UI.