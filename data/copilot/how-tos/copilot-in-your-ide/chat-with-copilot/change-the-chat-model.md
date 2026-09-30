# Changing the AI model for GitHub Copilot Chat

Learn how to switch between models for Copilot Chat.

Choose from a selection of models, each with its own particular strengths. You may have a favorite model that you like to use, or you might prefer to use a particular model for inquiring about a specific subject.

To view the available models per client, see [Supported AI models in GitHub Copilot](/en/copilot/reference/ai-models/supported-models#supported-ai-models-per-client).

> \[!NOTE] The models available to you depend on your Copilot plan and where you're using Copilot, such as GitHub.com or an IDE. Different models consume AI credits at different rates based on their token pricing. For details, see [Models and pricing for GitHub Copilot](/en/copilot/reference/copilot-billing/models-and-pricing).

Copilot allows you to change the model during a chat and have the alternative model used to generate responses to your prompts.

If you access Copilot Chat through a Copilot Business subscription, your organization must grant members the ability to switch to a different model. See [Managing policies and features for GitHub Copilot in your organization](/en/copilot/how-tos/administer-copilot/manage-for-organization/manage-policies).

Changing the model used by Copilot Chat does not affect the model used for Copilot inline suggestions. See [Changing the AI model for GitHub Copilot inline suggestions](/en/copilot/how-tos/copilot-in-your-ide/copilot-for-common-tasks/change-the-completion-model).

<div class="ghd-tool vscode">

## Changing the AI model

These instructions are for Visual Studio Code. For instructions on different clients, click the appropriate tab at the top of this page.

> \[!NOTE]
>
> * If you use Copilot Extensions, they may override the model you select.
> * Experimental pre-release versions of the models may not interact with all filters correctly, including the setting to block suggestions matching public code (see [Managing GitHub Copilot policies as an individual subscriber](/en/copilot/how-tos/manage-your-account/manage-policies#enabling-or-disabling-suggestions-matching-public-code)).

1. Open Copilot Chat by clicking the chat icon in the title bar of Visual Studio Code.
2. At the bottom of the chat view, select the **CURRENT-MODEL** <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-chevron-down" aria-label="chevron-down" role="img"><path d="M12.78 5.22a.749.749 0 0 1 0 1.06l-4.25 4.25a.749.749 0 0 1-1.06 0L3.22 6.28a.749.749 0 1 1 1.06-1.06L8 8.939l3.72-3.719a.749.749 0 0 1 1.06 0Z"></path></svg> dropdown menu, then click the AI model of your choice.

> \[!NOTE] If you select **Auto**, Copilot auto model selection will select the best model based on availability and to help reduce rate limiting. See [About Copilot auto model selection](/en/copilot/concepts/models/auto-model-selection).

## Adding more models

You can expand the model options that are available to power Copilot Chat. You can add models from:

* **A model provider**—such as Anthropic, Gemini, OpenAI, and others.
* **The AI Toolkit for Visual Studio Code**.

> \[!NOTE] Using the AI Toolkit for VS Code is in public preview and subject to change.

### Prerequisites

* Depending on the provider or model you choose, you may need to supply an API key, or model ID, from the provider, or a GitHub personal access token (PAT).
* To add models from the AI Toolkit for Visual Studio Code, you must <a href="vscode:extension/ms-windows-ai-studio.windows-ai-studio?ref_product=copilot&ref_type=engagement&ref_style=text">install the AI Toolkit extension</a>.
* If you are on a Copilot Business or Copilot Enterprise plan and want to use third-party models in a supported IDE, the **Bring Your Own Language Model Key in Select IDEs** policy must be enabled. For more information, see [Managing policies and features for GitHub Copilot in your organization](/en/copilot/how-tos/administer-copilot/manage-for-organization/manage-policies) or [Managing policies and features for GitHub Copilot in your enterprise](/en/copilot/how-tos/administer-copilot/manage-for-enterprise/manage-enterprise-policies).

### Adding models

1. In the Copilot chat view, click the **CURRENT-MODEL** <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-chevron-down" aria-label="chevron-down" role="img"><path d="M12.78 5.22a.749.749 0 0 1 0 1.06l-4.25 4.25a.749.749 0 0 1-1.06 0L3.22 6.28a.749.749 0 1 1 1.06-1.06L8 8.939l3.72-3.719a.749.749 0 0 1 1.06 0Z"></path></svg> dropdown menu.

2. Click **Manage Models**.

   ![Screenshot of the 'Manage Models' option, highlighted with a dark orange outline.](/assets/images/help/copilot/vsc-manage-models-option.png)

   A list of providers is displayed.

   If you have installed the AI Toolkit, then additional providers, added via the AI Toolkit, are also listed.

   ![Screenshot of the 'Manage Language Models' list.](/assets/images/help/copilot/vsc-manage-models-list.png)

3. Click the provider whose model(s) you want to add.

4. Depending on which provider you selected, you may be prompted to enter a GitHub PAT, an API key for the provider, or a model ID for a specific model.

   Enter the required information, then press <kbd>Enter</kbd>.

   A list of available models is displayed.

5. Select the model(s) you want to add, then click **OK**.

The models you selected are now available in the model picker in the chat view.

If you added a model from a provider via the AI Toolkit then the first time you use the model, you will be prompted to download it. You may also be prompted to authenticate with the provider.

> \[!TIP] If you're already using chat with auto model selection, you'll need to start a new chat session to switch models. To start a new session, in the top right of the chat view, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-plus" aria-label="new chat" role="img"><path d="M7.75 2a.75.75 0 0 1 .75.75V7h4.25a.75.75 0 0 1 0 1.5H8.5v4.25a.75.75 0 0 1-1.5 0V8.5H2.75a.75.75 0 0 1 0-1.5H7V2.75A.75.75 0 0 1 7.75 2Z"></path></svg> new chat.

</div>

<div class="ghd-tool visualstudio">

## Changing the AI model

These instructions are for Visual Studio. For instructions on different clients, click the appropriate tab at the top of this page.

To use multi-model Copilot Chat, you must use Visual Studio 2022 version 17.12 or later. See the [Visual Studio downloads page](https://visualstudio.microsoft.com/downloads/).

> \[!NOTE]
>
> * If you use Copilot Extensions, they may override the model you select.
> * Experimental pre-release versions of the models may not interact with all filters correctly, including the setting to block suggestions matching public code (see [Managing GitHub Copilot policies as an individual subscriber](/en/copilot/how-tos/manage-your-account/manage-policies#enabling-or-disabling-suggestions-matching-public-code)).

1. In the Visual Studio menu bar, click **View**, then click **GitHub Copilot Chat**.
2. In the bottom right of the chat view, select the **CURRENT-MODEL** <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-triangle-down" aria-label="triangle-down" role="img"><path d="m4.427 7.427 3.396 3.396a.25.25 0 0 0 .354 0l3.396-3.396A.25.25 0 0 0 11.396 7H4.604a.25.25 0 0 0-.177.427Z"></path></svg> dropdown menu, then click the AI model of your choice.

> \[!NOTE] If you select **Auto**, Copilot auto model selection will select the best model based on availability and to help reduce rate limiting. See [About Copilot auto model selection](/en/copilot/concepts/models/auto-model-selection).

</div>

<div class="ghd-tool jetbrains">

## Changing the AI model

These instructions are for the JetBrains IDEs. For instructions on different clients, click the appropriate tab at the top of this page.

> \[!NOTE]
>
> * If you use Copilot Extensions, they may override the model you select.
> * Experimental pre-release versions of the models may not interact with all filters correctly, including the setting to block suggestions matching public code (see [Managing GitHub Copilot policies as an individual subscriber](/en/copilot/how-tos/manage-your-account/manage-policies#enabling-or-disabling-suggestions-matching-public-code)).

For reasoning models that support configurable thinking effort, you can control how much reasoning the model applies to each request.

1. Click the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copilot" aria-label="copilot" role="img"><path d="M7.998 15.035c-4.562 0-7.873-2.914-7.998-3.749V9.338c.085-.628.677-1.686 1.588-2.065.013-.07.024-.143.036-.218.029-.183.06-.384.126-.612-.201-.508-.254-1.084-.254-1.656 0-.87.128-1.769.693-2.484.579-.733 1.494-1.124 2.724-1.261 1.206-.134 2.262.034 2.944.765.05.053.096.108.139.165.044-.057.094-.112.143-.165.682-.731 1.738-.899 2.944-.765 1.23.137 2.145.528 2.724 1.261.566.715.693 1.614.693 2.484 0 .572-.053 1.148-.254 1.656.066.228.098.429.126.612.012.076.024.148.037.218.924.385 1.522 1.471 1.591 2.095v1.872c0 .766-3.351 3.795-8.002 3.795Zm0-1.485c2.28 0 4.584-1.11 5.002-1.433V7.862l-.023-.116c-.49.21-1.075.291-1.727.291-1.146 0-2.059-.327-2.71-.991A3.222 3.222 0 0 1 8 6.303a3.24 3.24 0 0 1-.544.743c-.65.664-1.563.991-2.71.991-.652 0-1.236-.081-1.727-.291l-.023.116v4.255c.419.323 2.722 1.433 5.002 1.433ZM6.762 2.83c-.193-.206-.637-.413-1.682-.297-1.019.113-1.479.404-1.713.7-.247.312-.369.789-.369 1.554 0 .793.129 1.171.308 1.371.162.181.519.379 1.442.379.853 0 1.339-.235 1.638-.54.315-.322.527-.827.617-1.553.117-.935-.037-1.395-.241-1.614Zm4.155-.297c-1.044-.116-1.488.091-1.681.297-.204.219-.359.679-.242 1.614.091.726.303 1.231.618 1.553.299.305.784.54 1.638.54.922 0 1.28-.198 1.442-.379.179-.2.308-.578.308-1.371 0-.765-.123-1.242-.37-1.554-.233-.296-.693-.587-1.713-.7Z"></path><path d="M6.25 9.037a.75.75 0 0 1 .75.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 .75-.75Zm4.25.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 1.5 0Z"></path></svg>** icon in the status bar.
2. In the popup menu, click **Open GitHub Copilot Chat**.
3. In the bottom right of the chat view, select an AI model of your choice from the **CURRENT-MODEL** <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-chevron-down" aria-label="chevron-down" role="img"><path d="M12.78 5.22a.749.749 0 0 1 0 1.06l-4.25 4.25a.749.749 0 0 1-1.06 0L3.22 6.28a.749.749 0 1 1 1.06-1.06L8 8.939l3.72-3.719a.749.749 0 0 1 1.06 0Z"></path></svg> dropdown menu.
4. Optionally, hover over a reasoning model that supports configurable thinking effort.
   1. In the **Thinking Effort** submenu, select an effort level. Nonreasoning models do not display the **Thinking Effort** submenu.

> \[!NOTE] If you select **Auto**, Copilot auto model selection will select the best model based on availability and to help reduce rate limiting. See [About Copilot auto model selection](/en/copilot/concepts/models/auto-model-selection).

> \[!TIP]
> Model selection is also available when using Copilot through JetBrains AI Assistant. For more information, see [Using GitHub Copilot in JetBrains IDEs](/en/copilot/concepts/agents/copilot-in-jetbrains).

</div>

<div class="ghd-tool eclipse">

## Changing the AI model

These instructions are for the Eclipse IDE. For instructions on different clients, click the appropriate tab at the top of this page.

> \[!NOTE]
>
> * If you use Copilot Extensions, they may override the model you select.
> * Experimental pre-release versions of the models may not interact with all filters correctly, including the setting to block suggestions matching public code (see [Managing GitHub Copilot policies as an individual subscriber](/en/copilot/how-tos/manage-your-account/manage-policies#enabling-or-disabling-suggestions-matching-public-code)).

1. Click the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copilot" aria-label="copilot" role="img"><path d="M7.998 15.035c-4.562 0-7.873-2.914-7.998-3.749V9.338c.085-.628.677-1.686 1.588-2.065.013-.07.024-.143.036-.218.029-.183.06-.384.126-.612-.201-.508-.254-1.084-.254-1.656 0-.87.128-1.769.693-2.484.579-.733 1.494-1.124 2.724-1.261 1.206-.134 2.262.034 2.944.765.05.053.096.108.139.165.044-.057.094-.112.143-.165.682-.731 1.738-.899 2.944-.765 1.23.137 2.145.528 2.724 1.261.566.715.693 1.614.693 2.484 0 .572-.053 1.148-.254 1.656.066.228.098.429.126.612.012.076.024.148.037.218.924.385 1.522 1.471 1.591 2.095v1.872c0 .766-3.351 3.795-8.002 3.795Zm0-1.485c2.28 0 4.584-1.11 5.002-1.433V7.862l-.023-.116c-.49.21-1.075.291-1.727.291-1.146 0-2.059-.327-2.71-.991A3.222 3.222 0 0 1 8 6.303a3.24 3.24 0 0 1-.544.743c-.65.664-1.563.991-2.71.991-.652 0-1.236-.081-1.727-.291l-.023.116v4.255c.419.323 2.722 1.433 5.002 1.433ZM6.762 2.83c-.193-.206-.637-.413-1.682-.297-1.019.113-1.479.404-1.713.7-.247.312-.369.789-.369 1.554 0 .793.129 1.171.308 1.371.162.181.519.379 1.442.379.853 0 1.339-.235 1.638-.54.315-.322.527-.827.617-1.553.117-.935-.037-1.395-.241-1.614Zm4.155-.297c-1.044-.116-1.488.091-1.681.297-.204.219-.359.679-.242 1.614.091.726.303 1.231.618 1.553.299.305.784.54 1.638.54.922 0 1.28-.198 1.442-.379.179-.2.308-.578.308-1.371 0-.765-.123-1.242-.37-1.554-.233-.296-.693-.587-1.713-.7Z"></path><path d="M6.25 9.037a.75.75 0 0 1 .75.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 .75-.75Zm4.25.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 1.5 0Z"></path></svg>** icon in the status bar.
2. In the popup menu, click **Open Chat**.
3. In the bottom right of the chat panel, click the currently selected AI model, then select an alternative model from the popup menu.

> \[!NOTE] If you select **Auto**, Copilot auto model selection will select the best model based on availability and to help reduce rate limiting. See [About Copilot auto model selection](/en/copilot/concepts/models/auto-model-selection).

</div>

<div class="ghd-tool xcode">

## Changing the AI model

These instructions are for Xcode. For instructions on different clients, click the appropriate tab at the top of this page.

To use multi-model Copilot Chat, you must install the GitHub Copilot for Xcode extension. See [Installing the GitHub Copilot extension in your environment](/en/copilot/how-tos/copilot-in-your-ide/set-up-copilot/install-copilot-extension).

> \[!NOTE]
>
> * If you use Copilot Extensions, they may override the model you select.
> * Experimental pre-release versions of the models may not interact with all filters correctly, including the setting to block suggestions matching public code (see [Managing GitHub Copilot policies as an individual subscriber](/en/copilot/how-tos/manage-your-account/manage-policies#enabling-or-disabling-suggestions-matching-public-code)).

1. To open the chat view, click **Editor** in the menu bar, then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copilot" aria-label="copilot" role="img"><path d="M7.998 15.035c-4.562 0-7.873-2.914-7.998-3.749V9.338c.085-.628.677-1.686 1.588-2.065.013-.07.024-.143.036-.218.029-.183.06-.384.126-.612-.201-.508-.254-1.084-.254-1.656 0-.87.128-1.769.693-2.484.579-.733 1.494-1.124 2.724-1.261 1.206-.134 2.262.034 2.944.765.05.053.096.108.139.165.044-.057.094-.112.143-.165.682-.731 1.738-.899 2.944-.765 1.23.137 2.145.528 2.724 1.261.566.715.693 1.614.693 2.484 0 .572-.053 1.148-.254 1.656.066.228.098.429.126.612.012.076.024.148.037.218.924.385 1.522 1.471 1.591 2.095v1.872c0 .766-3.351 3.795-8.002 3.795Zm0-1.485c2.28 0 4.584-1.11 5.002-1.433V7.862l-.023-.116c-.49.21-1.075.291-1.727.291-1.146 0-2.059-.327-2.71-.991A3.222 3.222 0 0 1 8 6.303a3.24 3.24 0 0 1-.544.743c-.65.664-1.563.991-2.71.991-.652 0-1.236-.081-1.727-.291l-.023.116v4.255c.419.323 2.722 1.433 5.002 1.433ZM6.762 2.83c-.193-.206-.637-.413-1.682-.297-1.019.113-1.479.404-1.713.7-.247.312-.369.789-.369 1.554 0 .793.129 1.171.308 1.371.162.181.519.379 1.442.379.853 0 1.339-.235 1.638-.54.315-.322.527-.827.617-1.553.117-.935-.037-1.395-.241-1.614Zm4.155-.297c-1.044-.116-1.488.091-1.681.297-.204.219-.359.679-.242 1.614.091.726.303 1.231.618 1.553.299.305.784.54 1.638.54.922 0 1.28-.198 1.442-.379.179-.2.308-.578.308-1.371 0-.765-.123-1.242-.37-1.554-.233-.296-.693-.587-1.713-.7Z"></path><path d="M6.25 9.037a.75.75 0 0 1 .75.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 .75-.75Zm4.25.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 1.5 0Z"></path></svg> Copilot** then **Open Chat**. Copilot Chat opens in a new window.
2. In the bottom right of the chat view, select the **CURRENT-MODEL** <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-triangle-down" aria-label="triangle-down" role="img"><path d="m4.427 7.427 3.396 3.396a.25.25 0 0 0 .354 0l3.396-3.396A.25.25 0 0 0 11.396 7H4.604a.25.25 0 0 0-.177.427Z"></path></svg> dropdown menu, then click the AI model of your choice.

> \[!NOTE] If you select **Auto**, Copilot auto model selection will select the best model based on availability and to help reduce rate limiting. See [About Copilot auto model selection](/en/copilot/concepts/models/auto-model-selection).

</div>

## Further reading

* [Changing the AI model for GitHub Copilot inline suggestions](/en/copilot/how-tos/copilot-in-your-ide/copilot-for-common-tasks/change-the-completion-model)
* [AI model comparison](/en/copilot/reference/ai-models/model-comparison)

<div class="ghd-tool vscode">

* [AI language models in VS Code](https://code.visualstudio.com/docs/copilot/language-models#_bring-your-own-language-model-key) in the Visual Studio Code documentation.

</div>