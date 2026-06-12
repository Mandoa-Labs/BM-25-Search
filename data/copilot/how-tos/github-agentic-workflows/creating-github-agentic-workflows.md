# Creating GitHub Agentic Workflows

Build custom AI-powered automations tailored to your repository's needs.

> \[!NOTE]
> GitHub Agentic Workflows are in public preview and subject to change.

## About creating GitHub Agentic Workflows

You can create GitHub Agentic Workflows with a coding agent (recommended) or manually. A workflow is a markdown file in `.github/workflows/` that contains YAML frontmatter for configuration and natural language instructions for the AI agent.

To create an agentic workflow, you define the workflow in markdown, compile it into a `.lock.yml` file, commit both files, then run it through GitHub Actions triggers or the GitHub CLI.

This article focuses on the core tasks: creating, updating, and reusing workflows. For complete technical detail and additional patterns, use the [GitHub Agentic Workflows documentation site](https://github.github.com/gh-aw/).

## Prerequisites

Before you begin, make sure you have:

* An AI account: GitHub Copilot, Anthropic Claude, OpenAI Codex, or Google Gemini

* A GitHub repository where you have write access

* GitHub Actions enabled for the repository

* GitHub CLI (`gh`) v2.0.0 or later installed and authenticated

  To check your version, run `gh --version`. To authenticate, run:

  ```shell
  gh auth login --scopes repo,workflow
  ```

* The GitHub Agentic Workflows extension for the GitHub CLI installed:

  ```shell
  gh extension install github/gh-aw
  ```

  If you're using GitHub CLI version 2.90.0 or later, running any `gh aw` command will prompt you to install the extension automatically if it is not yet installed.

## Authentication

You can set up authentication with your chosen AI engine (coding agent) in two ways:

* [Using the built-in `GITHUB_TOKEN`](#using-the-built-in-github_token) for organization billing (recommended). This option is specifically for the GitHub Copilot engine, and can only be used by repositories owned by an organization with a GitHub Copilot plan.
* [Using a personal access token or API key](#using-a-personal-access-token-or-api-key) for personal repositories and third-party AI engines.

### Using the built-in `GITHUB_TOKEN`

> \[!TIP]
> If you use GitHub Copilot in an organization-owned repository, the built-in `GITHUB_TOKEN` approach in this section is strongly recommended.

If you are using GitHub Copilot in an organization-owned repository, you can use GitHub Actions' built-in `GITHUB_TOKEN` instead of a personal access token. This bills the workflow's usage directly to your organization and avoids the need to manage a personal access token secret for Copilot requests. To set this up:

1. Your organization administrator should enable the policy "Allow use of Copilot CLI billed to the organization", if not already enabled, in Copilot settings.
2. For workflows that you want to bill to an organization, put `copilot-requests: write` in the workflow frontmatter `permissions`.

#### Enabling organization billing

"Allow use of Copilot CLI billed to the organization" must be enabled in GitHub Copilot policy settings. If the "Copilot CLI" policy is already enabled, the billing policy is enabled by default.

1. In the upper-right corner of GitHub, click your profile picture, then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-organization" aria-label="organization" role="img"><path d="M1.75 16A1.75 1.75 0 0 1 0 14.25V1.75C0 .784.784 0 1.75 0h8.5C11.216 0 12 .784 12 1.75v12.5c0 .085-.006.168-.018.25h2.268a.25.25 0 0 0 .25-.25V8.285a.25.25 0 0 0-.111-.208l-1.055-.703a.749.749 0 1 1 .832-1.248l1.055.703c.487.325.779.871.779 1.456v5.965A1.75 1.75 0 0 1 14.25 16h-3.5a.766.766 0 0 1-.197-.026c-.099.017-.2.026-.303.026h-3a.75.75 0 0 1-.75-.75V14h-1v1.25a.75.75 0 0 1-.75.75Zm-.25-1.75c0 .138.112.25.25.25H4v-1.25a.75.75 0 0 1 .75-.75h2.5a.75.75 0 0 1 .75.75v1.25h2.25a.25.25 0 0 0 .25-.25V1.75a.25.25 0 0 0-.25-.25h-8.5a.25.25 0 0 0-.25.25ZM3.75 6h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5ZM3 3.75A.75.75 0 0 1 3.75 3h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 3 3.75Zm4 3A.75.75 0 0 1 7.75 6h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 7 6.75ZM7.75 3h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5ZM3 9.75A.75.75 0 0 1 3.75 9h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 3 9.75ZM7.75 9h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5Z"></path></svg> Organizations**.

2. Select an organization by clicking on it.

3. Under your organization name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> Settings**. If you cannot see the "Settings" tab, select the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="More" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>** dropdown menu, then click **Settings**.

   ![Screenshot of the tabs in an organization's profile. The "Settings" tab is outlined in dark orange.](/assets/images/help/discussions/org-settings-global-nav-update.png)

4. In the sidebar, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copilot" aria-label="copilot" role="img"><path d="M7.998 15.035c-4.562 0-7.873-2.914-7.998-3.749V9.338c.085-.628.677-1.686 1.588-2.065.013-.07.024-.143.036-.218.029-.183.06-.384.126-.612-.201-.508-.254-1.084-.254-1.656 0-.87.128-1.769.693-2.484.579-.733 1.494-1.124 2.724-1.261 1.206-.134 2.262.034 2.944.765.05.053.096.108.139.165.044-.057.094-.112.143-.165.682-.731 1.738-.899 2.944-.765 1.23.137 2.145.528 2.724 1.261.566.715.693 1.614.693 2.484 0 .572-.053 1.148-.254 1.656.066.228.098.429.126.612.012.076.024.148.037.218.924.385 1.522 1.471 1.591 2.095v1.872c0 .766-3.351 3.795-8.002 3.795Zm0-1.485c2.28 0 4.584-1.11 5.002-1.433V7.862l-.023-.116c-.49.21-1.075.291-1.727.291-1.146 0-2.059-.327-2.71-.991A3.222 3.222 0 0 1 8 6.303a3.24 3.24 0 0 1-.544.743c-.65.664-1.563.991-2.71.991-.652 0-1.236-.081-1.727-.291l-.023.116v4.255c.419.323 2.722 1.433 5.002 1.433ZM6.762 2.83c-.193-.206-.637-.413-1.682-.297-1.019.113-1.479.404-1.713.7-.247.312-.369.789-.369 1.554 0 .793.129 1.171.308 1.371.162.181.519.379 1.442.379.853 0 1.339-.235 1.638-.54.315-.322.527-.827.617-1.553.117-.935-.037-1.395-.241-1.614Zm4.155-.297c-1.044-.116-1.488.091-1.681.297-.204.219-.359.679-.242 1.614.091.726.303 1.231.618 1.553.299.305.784.54 1.638.54.922 0 1.28-.198 1.442-.379.179-.2.308-.578.308-1.371 0-.765-.123-1.242-.37-1.554-.233-.296-.693-.587-1.713-.7Z"></path><path d="M6.25 9.037a.75.75 0 0 1 .75.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 .75-.75Zm4.25.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 1.5 0Z"></path></svg> Copilot**, then click **Policies**.

5. Enable "Copilot CLI", then enable "Allow use of Copilot CLI billed to the organization."

#### Billing a workflow to an organization

When creating a workflow, you must include `copilot-requests: write` under `permissions` in the workflow frontmatter. When this permission is set, the GitHub Actions' token is used for Copilot requests, and `COPILOT_GITHUB_TOKEN` is ignored for those requests. If the GitHub Actions token does not have GitHub Copilot access from the organization, the workflow fails when it sends Copilot requests, and you should configure `COPILOT_GITHUB_TOKEN` instead.

```yaml
permissions:
  contents: read
  copilot-requests: write
```

### Using a personal access token or API key

For personal repositories or third-party AI engines, you need to create a repository secret storing a personal access token or API key. For GitHub Copilot, the secret is `COPILOT_GITHUB_TOKEN`, which stores a fine-grained personal access token.

If you use `gh aw add-wizard`, the setup flow prompts you to create that secret. If you are creating an agentic workflow from the GitHub web interface or manually, you will first need to add the secret yourself in your repository's GitHub Actions secrets, either in the GitHub UI or with `gh aw secrets set` in the CLI. For instructions, see [authentication reference](https://github.github.com/gh-aw/reference/auth/).

## Creating a workflow

The recommended way to create agentic workflows is to use a CLI coding agent or VS Code. This gives you one guided path for authoring, compiling, and committing the workflow.

### Using a CLI coding agent or VS Code

1. Using the GitHub CLI GitHub Agentic Workflows extension (`gh aw`), initialize the repository for agentic authoring (recommended for first-time setup in a repository):

   ```shell
   gh aw init
   ```

   This adds skills, instructions, and a custom agent related to agentic workflow authoring, so coding agents can create and edit workflows more effectively.

2. Start your coding agent in the context of your repository (for example, Copilot CLI or VS Code agent mode).

3. Enter a prompt mentioning the `agentic-workflows` skill and describing your desired workflow:

   ```copilot copy
   /agentic-workflows Create a new workflow that creates a daily report on
   recent activity in the repository, delivered as
   an issue.
   ```

4. The agent will create the workflow, and compile the workflow using the GitHub CLI.

5. Review the workflow, then ask the agent to commit and push the files.

6. Trigger the workflow from the GitHub Actions tab, or with the GitHub CLI run:

   ```shell
   gh aw run YOUR-WORKFLOW-NAME
   ```

### Other creation methods

You can also create agentic workflows:

* In the GitHub web interface. See [creating workflows in the GitHub web interface](https://github.github.com/gh-aw/setup/creating-workflows/#github-web-interface).
* Manually. See [creating workflows by manual editing](https://github.github.com/gh-aw/setup/creating-workflows/#manual-editing).

## Workflow structure reference

Each workflow markdown file has two parts:

| Section              | Purpose                                                                    |
| -------------------- | -------------------------------------------------------------------------- |
| **YAML frontmatter** | Defines triggers (`on`), permissions, safe outputs, and the AI engine.     |
| **Markdown body**    | Natural language instructions the AI agent follows when the workflow runs. |

Key frontmatter fields:

| Field          | Description                                                                                                           |
| -------------- | --------------------------------------------------------------------------------------------------------------------- |
| `on`           | The event trigger (same syntax as GitHub Actions triggers).                                                           |
| `permissions`  | Repository permissions granted to the agent. Defaults to `read-all`.                                                  |
| `safe-outputs` | Write operations the agent is allowed to perform (for example, `create-issue`, `add-comment`, `create-pull-request`). |
| `engine`       | The AI engine to use (`copilot` is the default; `claude`, `codex`, and `gemini` are also supported).                  |

For the full frontmatter reference, see the [GitHub Agentic Workflows frontmatter documentation](https://github.github.com/gh-aw/reference/frontmatter/).

## Example agentic workflow

The following example is a simplified weekly issue activity report for a repository.

```markdown
---
on: weekly on monday

permissions:
  issues: read
  copilot-requests: write

network: defaults

tools:
  github:
    toolsets: [issues]

safe-outputs:
  create-issue:

---

# Weekly issue activity report

Review issue activity from the last 7 days in this repository.

Create a GitHub issue that includes:

- Total issues opened and closed this week.
- The top recurring themes from issue titles and descriptions.
- A short list of notable issues that still need attention.
- Two or three actionable recommendations for maintainers.

Keep the report concise and action-oriented.
```

## Updating a workflow

To update an existing workflow:

1. Edit the workflow markdown file in `.github/workflows/`.

2. Recompile to refresh the lock file:

   ```shell
   gh aw compile
   ```

3. Commit and push both updated files.

4. Open a pull request and verify GitHub Actions checks.

For detailed editing guidance, see [Editing Workflows](https://github.github.com/gh-aw/guides/editing-workflows/).

## Reusing workflows

You can also import workflows from external repositories that you can access. For example, you can add a workflow from `githubnext/agentics`:

```shell
gh aw add-wizard githubnext/agentics/daily-repo-status
```

For non-interactive setup, you can use `gh aw add` and optionally pin a version.

When you import a workflow, GitHub CLI stores a `source:` value in frontmatter so you can update from upstream later with `gh aw update`.

Only import workflows from sources you trust, and review what a workflow does before adding it to your repository. Workflows marked `private: true` can't be imported into other repositories.

When you update an imported workflow, GitHub CLI tries to preserve local changes. If there are merge conflicts, resolve them and run `gh aw compile` again.

For more information, see [Reusing Workflows](https://github.github.com/gh-aw/guides/reusing-workflows/).

## Next steps

* For workflow examples, advanced patterns, guides, and troubleshooting information, see the [GitHub Agentic Workflows documentation site](https://github.github.com/gh-aw/).