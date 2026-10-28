# Adding LLM models to the GitHub Copilot app

Connect a model from an external provider of your choice, hosted locally or in the cloud.

> [!NOTE]
> Support to use your own model provider in the GitHub Copilot app is in public preview and subject to change.

You can configure the GitHub Copilot app to include models from an LLM provider of your choice—using Bring Your Own Key (BYOK)—in addition to the GitHub-provided models. You can set up your model provider when you first open the app or later in app settings.

Windows users with an NVIDIA GPU and sufficient memory can install the MAI Code 1.1 Flash and Flint NVFP4 models locally on their device, directly from within the GitHub Copilot app.

You must sign in with a GitHub account to use the app, but you do not need a Copilot plan if you use your own model provider. If you do have a Copilot plan, you can use models from your own model provider and GitHub-provided models in the same app.

> [!NOTE]
> This article tells you how to configure custom models for your own use. To set up custom models for users in an organization or enterprise, see [Enabling custom models for GitHub Copilot in your organization](/en/copilot/how-tos/administer-copilot/manage-for-organization/enable-custom-models) and [Enabling custom models for GitHub Copilot in your enterprise](/en/copilot/how-tos/administer-copilot/manage-for-enterprise/enable-custom-models).

## Adding models using BYOK

You can use the BYOK method to add models to the GitHub Copilot app.

### Supported providers

The GitHub Copilot app supports these BYOK model providers:

* OpenAI
* Azure OpenAI
* Microsoft Foundry
* Anthropic
* Ollama
* Foundry Local
* LM Studio
* Any OpenAI-compatible HTTP endpoint

### Prerequisite

You must have an API key to add a model provider that requires authentication.

### Set up a model provider

If you are setting up the app for the first time and do not have a Copilot plan, you can choose to set up your own model provider during onboarding.

To add or update a model provider later:

1. Click <span style="vertical-align: 2px"><svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="Settings" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg></span> to open the Settings dialog.
2. In the sidebar, click **Model providers**.
3. Click **Add provider**.
4. Select your provider.
5. Enter the provider details. This varies by provider but may include the display name, base URL, and API key.
6. Click **Add provider** to save the provider.

After you add a provider, its models appear in the model picker alongside GitHub-hosted models. You can select the model and use it in a session. For more information, see [Working with agent sessions in the GitHub Copilot app](/en/copilot/how-tos/github-copilot-app/agent-sessions).

Provider credentials are stored in the system credential store and are never displayed in the UI.

## Installing a local model from the model picker

> [!NOTE]
> This feature is in public preview and is subject to change. You can disable this feature by going to the "Experimental" section of the app settings and, under "Agents", turning off the **Windows ML local models** option.
>
> To enable Copilot Fusion to use local models, you must turn on the **Local model auto routing** option in the "Experimental" section of the app settings.

If you are using Windows and your computer meets the following prerequisites, you can download and install the following models locally on your device from within the app's settings:

* MAI Code 1.1 Flash
* Flint NVFP4

### Prerequisites

You must have:

* A Windows PC

* An NVIDIA GPU (AMD is not supported)

* Minimum available combined RAM per model:

  * **MAI Code 1.1 Flash:**  96 GB
  * **Flint NVFP4:**  48 GB

* Minimum available storage per model:

  * **MAI Code 1.1 Flash:**  60 GB
  * **Flint NVFP4:**  23 GB

* llama.cpp v0.7.0 or later installed and `LLAMACPP_SERVER_PATH` set to its path. Required build version:

  * **MAI Code 1.1 Flash:**  [b11669](https://github.com/ggml-org/llama.cpp/releases/tag/b11669?utm_source=local-model-prereq-mai-code\&utm_medium=docs\&utm_campaign=universe-2026) or later
  * **Flint NVFP4:**  [b11803](https://github.com/ggml-org/llama.cpp/releases?q=flint\&expanded=true\&utm_source=local-model-prerequisite-flint\&utm_medium=docs\&utm_campaign=universe-2026#release-b11803) or later

  See [Installing llama.cpp for Windows](#installing-llamacpp-for-windows).

### Benefits of using MAI Code 1.1 Flash locally

MAI Code 1.1 Flash is a coding-optimized model that you can run locally on your Windows PC. By using a model that's running locally, you can use Copilot offline and avoid consuming GitHub AI Credits.

After installing MAI Code 1.1 Flash, you can select it from the model picker, just like any other model. The model also becomes available for Copilot Fusion's Fusion Standard effort level to use. When you set the model selection to **Copilot Fusion** with Fusion Standard, MAI Code 1.1 Flash will be automatically chosen to work on appropriate tasks, leaving cloud-based models for tasks that require more resources or higher performance.

### Installing llama.cpp for Windows

To install llama.cpp on Windows with the CUDA build:

1. In your browser, go to the releases page of the llama.cpp repository: [https://github.com/ggml-org/llama.cpp/releases](https://github.com/ggml-org/llama.cpp/releases?utm_source=llama-windows-install-cta\&utm_medium=docs\&utm_campaign=universe-2026).

2. Choose the release you want to install—for example, [b11803](https://github.com/ggml-org/llama.cpp/releases?q=flint\&expanded=true\&utm_source=local-model-prerequisite-flint\&utm_medium=docs\&utm_campaign=universe-2026#release-b11803).

3. Click the links to download both files for the Windows CUDA 13.4 ARM64 build:

   * Windows arm64 (CUDA 13)
   * CUDA 13.4 DLLs

4. Open Command Prompt and create the installation folder:

   ```shell copy
   mkdir "%LOCALAPPDATA%\Programs\llama.cpp\BUILD-cuda-13.4-arm64"
   ```

   Replacing `BUILD` the the build number—for example, `b11803`.

5. Extract all files from both ZIP files directly into this folder. If you use **Extract All** in File Explorer, change the destination to this folder, because by default File Explorer creates a separate subfolder for each ZIP file. When you're done, the folder should contain a large number of files, including `llama-server.exe`, `cudart64_13.dll`, `cublas64_13.dll`, and `cublasLt64_13.dll`, with no subfolders.

6. Set the `LLAMACPP_SERVER_PATH` environment variable:

   ```shell copy
   setx LLAMACPP_SERVER_PATH "%LOCALAPPDATA%\Programs\llama.cpp\BUILD-cuda-13.4-arm64\llama-server.exe"
   ```

   Replacing `BUILD` the the build number.

7. Close Command Prompt and open a new Command Prompt window. If the Copilot app or VS Code is already open, restart it. If Copilot CLI is running, exit it and start it again from a new terminal window.

8. To check the installation, run:

   ```shell copy
   "%LLAMACPP_SERVER_PATH%" --list-devices
   ```

### Installing a local model from within the Copilot app

1. Click <span style="vertical-align: 2px"><svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="Settings" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg></span> to open the Settings dialog.

2. In the sidebar, click **Model providers**.

3. Click **Add provider**.

4. Select **Windows ML**.

   If your local machine meets the prerequisites, the supported local models will be listed under "Available models."

5. Click **Download** for the model you want to install.

6. Use the **Maximum % system memory to use** slider to cap the amount of system memory that can be used by Windows ML models.

7. Turn on **Restart models on app restart** to automatically restart downloaded Windows ML models when you restart the Copilot app.

8. Alter the model-specific settings as required.

### Using a downloaded local model

After the download is complete, the local model will be available for use in your sessions.

You can either:

* Select it from the model picker, the same as any other available model. See [Choosing a model in the Copilot app](/en/copilot/how-tos/github-copilot-app/choose-a-model).
* **MAI Code 1.1 Flash only:** Choose **Copilot Fusion, then Fusion Standard** effort level in the model picker, and Copilot will automatically use this model when appropriate.
* Assign it to a custom agent for focused tasks. You can then prompt Copilot to use that custom agent for part of a task, while keeping your main session on a different model in the cloud. See [Creating and using custom agents for GitHub Copilot CLI](/en/copilot/how-tos/copilot-cli/customize-copilot/create-custom-agents-for-cli#delegating-focused-tasks-to-a-specific-model).

> [!IMPORTANT]
> After downloading a local model from the model picker, do not use it simultaneously in sessions within different Copilot surfaces (Copilot CLI, the Copilot app, VS Code), either by direct selection or via Copilot Fusion. Each surface loads its own instance of the model into memory, which is likely to cause your local machine to run out of RAM.