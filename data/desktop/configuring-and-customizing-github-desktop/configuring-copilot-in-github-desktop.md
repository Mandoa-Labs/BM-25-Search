# Configuring Copilot in GitHub Desktop

Choose which AI model Copilot in GitHub Desktop uses for each feature, or connect your own LLM provider.

You can choose which model Copilot uses for each GitHub Desktop feature, such as commit message generation and conflict resolution.

You can also configure Copilot in GitHub Desktop to use your own LLM provider (BYOK) instead of GitHub-hosted models. This lets you connect to OpenAI-compatible endpoints, Azure OpenAI, or Anthropic, including locally running models such as Ollama.

## Prerequisites

* You must be signed in to a GitHub account with access to Copilot in GitHub Desktop.
* If your access is managed by an organization or enterprise, Copilot in GitHub Desktop must be enabled for your account.
* You have an API key or bearer token from a supported LLM provider, or you have a local model running, such as Ollama.
* You have the base URL and at least one model identifier for the provider you want to use.

> \[!NOTE]
> Custom LLM providers in GitHub Desktop require access to Copilot in GitHub Desktop. To use your own LLM models with Copilot CLI, see [Using your own LLM models in GitHub Copilot CLI](/en/copilot/how-tos/copilot-cli/customize-copilot/use-byok-models).

## Supported provider types

GitHub Desktop supports three custom provider types:

| Provider type                  | Compatible services                                                                                          |
| ------------------------------ | ------------------------------------------------------------------------------------------------------------ |
| **OpenAI / OpenAI-compatible** | OpenAI, Ollama, vLLM, Foundry Local, and any other endpoint that is compatible with the selected API format. |
| **Azure**                      | Azure OpenAI Service.                                                                                        |
| **Anthropic**                  | Anthropic Claude models.                                                                                     |

## Configuring your provider

You configure your model provider by adding a custom provider in GitHub Desktop settings.

<div class="ghd-tool mac">

1. In the menu bar, select **GitHub Desktop**, then click **Settings**.

   ![Screenshot of the menu bar on a Mac. Under the open "GitHub Desktop" dropdown menu, the cursor hovers over "Settings", which is highlighted in blue.](/assets/images/help/desktop/mac-choose-settings.png)

2. In the left sidebar, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copilot" aria-label="copilot" role="img"><path d="M7.998 15.035c-4.562 0-7.873-2.914-7.998-3.749V9.338c.085-.628.677-1.686 1.588-2.065.013-.07.024-.143.036-.218.029-.183.06-.384.126-.612-.201-.508-.254-1.084-.254-1.656 0-.87.128-1.769.693-2.484.579-.733 1.494-1.124 2.724-1.261 1.206-.134 2.262.034 2.944.765.05.053.096.108.139.165.044-.057.094-.112.143-.165.682-.731 1.738-.899 2.944-.765 1.23.137 2.145.528 2.724 1.261.566.715.693 1.614.693 2.484 0 .572-.053 1.148-.254 1.656.066.228.098.429.126.612.012.076.024.148.037.218.924.385 1.522 1.471 1.591 2.095v1.872c0 .766-3.351 3.795-8.002 3.795Zm0-1.485c2.28 0 4.584-1.11 5.002-1.433V7.862l-.023-.116c-.49.21-1.075.291-1.727.291-1.146 0-2.059-.327-2.71-.991A3.222 3.222 0 0 1 8 6.303a3.24 3.24 0 0 1-.544.743c-.65.664-1.563.991-2.71.991-.652 0-1.236-.081-1.727-.291l-.023.116v4.255c.419.323 2.722 1.433 5.002 1.433ZM6.762 2.83c-.193-.206-.637-.413-1.682-.297-1.019.113-1.479.404-1.713.7-.247.312-.369.789-.369 1.554 0 .793.129 1.171.308 1.371.162.181.519.379 1.442.379.853 0 1.339-.235 1.638-.54.315-.322.527-.827.617-1.553.117-.935-.037-1.395-.241-1.614Zm4.155-.297c-1.044-.116-1.488.091-1.681.297-.204.219-.359.679-.242 1.614.091.726.303 1.231.618 1.553.299.305.784.54 1.638.54.922 0 1.28-.198 1.442-.379.179-.2.308-.578.308-1.371 0-.765-.123-1.242-.37-1.554-.233-.296-.693-.587-1.713-.7Z"></path><path d="M6.25 9.037a.75.75 0 0 1 .75.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 .75-.75Zm4.25.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 1.5 0Z"></path></svg> Copilot**.

3. Click the **Providers** tab.

4. Click **Add Provider**.

5. Under **Name**, type a name for the LLM provider.

6. Under **Type**, select the provider type.

7. Under **Base URL**, type the base URL of your model provider's API endpoint.

   The base URL must be an HTTPS URL, or an HTTP URL that points to the local machine.

8. If you selected **OpenAI / OpenAI-compatible**, under **API Format**, select the API format your provider expects.
   * Select **Chat completions (default)** for providers that use the OpenAI Chat Completions API.
   * Select **Responses (GPT-5 series)** for providers that use the OpenAI Responses API.

9. If you selected **Azure**, under **Azure API Version**, type the API version for your deployment.

10. Optionally, under **Request Timeout (seconds)**, type the number of seconds GitHub Desktop waits for the provider to respond.

11. Under **Authentication**, select the authentication method.
    * Select **API key** to authenticate with an API key.
    * Select **Bearer token** to authenticate with a bearer token.
    * Select **None** only for endpoints that do not require credentials.

12. If you selected **API key** or **Bearer token**, type the required credential.

13. Add at least one model to the provider. For more information, see [Adding models to your provider](#adding-models-to-your-provider).

14. Click **Add**.

</div>

<div class="ghd-tool windows">

1. Use the **File** menu, then click **Options**.

   ![Screenshot of the "GitHub Desktop" menu bar on Windows. In the expanded "File" dropdown menu, the "Options" item is outlined in orange.](/assets/images/help/desktop/windows-choose-options.png)

2. In the left sidebar, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copilot" aria-label="copilot" role="img"><path d="M7.998 15.035c-4.562 0-7.873-2.914-7.998-3.749V9.338c.085-.628.677-1.686 1.588-2.065.013-.07.024-.143.036-.218.029-.183.06-.384.126-.612-.201-.508-.254-1.084-.254-1.656 0-.87.128-1.769.693-2.484.579-.733 1.494-1.124 2.724-1.261 1.206-.134 2.262.034 2.944.765.05.053.096.108.139.165.044-.057.094-.112.143-.165.682-.731 1.738-.899 2.944-.765 1.23.137 2.145.528 2.724 1.261.566.715.693 1.614.693 2.484 0 .572-.053 1.148-.254 1.656.066.228.098.429.126.612.012.076.024.148.037.218.924.385 1.522 1.471 1.591 2.095v1.872c0 .766-3.351 3.795-8.002 3.795Zm0-1.485c2.28 0 4.584-1.11 5.002-1.433V7.862l-.023-.116c-.49.21-1.075.291-1.727.291-1.146 0-2.059-.327-2.71-.991A3.222 3.222 0 0 1 8 6.303a3.24 3.24 0 0 1-.544.743c-.65.664-1.563.991-2.71.991-.652 0-1.236-.081-1.727-.291l-.023.116v4.255c.419.323 2.722 1.433 5.002 1.433ZM6.762 2.83c-.193-.206-.637-.413-1.682-.297-1.019.113-1.479.404-1.713.7-.247.312-.369.789-.369 1.554 0 .793.129 1.171.308 1.371.162.181.519.379 1.442.379.853 0 1.339-.235 1.638-.54.315-.322.527-.827.617-1.553.117-.935-.037-1.395-.241-1.614Zm4.155-.297c-1.044-.116-1.488.091-1.681.297-.204.219-.359.679-.242 1.614.091.726.303 1.231.618 1.553.299.305.784.54 1.638.54.922 0 1.28-.198 1.442-.379.179-.2.308-.578.308-1.371 0-.765-.123-1.242-.37-1.554-.233-.296-.693-.587-1.713-.7Z"></path><path d="M6.25 9.037a.75.75 0 0 1 .75.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 .75-.75Zm4.25.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 1.5 0Z"></path></svg> Copilot**.

3. Click the **Providers** tab.

4. Click **Add Provider**.

5. Under **Name**, type a name for the LLM provider.

6. Under **Type**, select the provider type.

7. Under **Base URL**, type the base URL of your model provider's API endpoint.

   The base URL must be an HTTPS URL, or an HTTP URL that points to the local machine.

8. If you selected **OpenAI / OpenAI-compatible**, under **API Format**, select the API format your provider expects.
   * Select **Chat completions (default)** for providers that use the OpenAI Chat Completions API.
   * Select **Responses (GPT-5 series)** for providers that use the OpenAI Responses API.

9. If you selected **Azure**, under **Azure API Version**, type the API version for your deployment.

10. Optionally, under **Request Timeout (seconds)**, type the number of seconds GitHub Desktop waits for the provider to respond.

11. Under **Authentication**, select the authentication method.
    * Select **API key** to authenticate with an API key.
    * Select **Bearer token** to authenticate with a bearer token.
    * Select **None** only for endpoints that do not require credentials.

12. If you selected **API key** or **Bearer token**, type the required credential.

13. Add at least one model to the provider. For more information, see [Adding models to your provider](#adding-models-to-your-provider).

14. Click **Add**.

</div>

## Adding models to your provider

Add the models you want to use from your provider. Each model you add appears in the model picker alongside GitHub-hosted models.

1. In the **Add Custom Provider** or **Edit Custom Provider** dialog, under **Models**, click **Add Model**.
2. Under **Display Name**, type the friendly name shown in the Copilot model picker.
3. Under **Model Identifier**, type the exact model name your provider expects.
4. Under **Reasoning Effort**, select the reasoning level for the model.

   For non-reasoning models, or to let the provider choose, leave **Default (provider's choice)** selected.
5. Click **Add**.

## Reviewing provider responsibilities

When you use your own LLM provider, GitHub Desktop sends prompts and repository context to that provider instead of GitHub. Check your provider's data handling and retention policies before adding credentials.

Always review generated commit messages and conflict-resolution suggestions before committing. For more information, see [Responsible use of GitHub Copilot features](/en/copilot/responsible-use).

## Further reading

* [Committing and reviewing changes to your project in GitHub Desktop](/en/desktop/making-changes-in-a-branch/committing-and-reviewing-changes-to-your-project-in-github-desktop)
* [Supported AI models in GitHub Copilot](/en/copilot/reference/ai-models/supported-models)
* [Using your own LLM models in GitHub Copilot CLI](/en/copilot/how-tos/copilot-cli/customize-copilot/use-byok-models)