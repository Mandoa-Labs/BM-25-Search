# Personalizing your cloud sessions

Bring your personal instructions, skills, and custom agents to your sessions with Copilot in the cloud using a dotfiles repository.

## About personalizing cloud sessions

You can use a dotfiles repository to give Copilot in the cloud your preferred instructions, reusable skills, and specialized agents across repositories. You can also use personal custom instructions to apply to every conversation you have on GitHub.com and GitHub Mobile. These personal customizations apply to your sessions, rather than configuring a repository for everyone who works in it.

Dotfiles personalization works only in **cloud sandboxes**. It does not apply to sessions that run on GitHub Actions.

Copilot uses the same dotfiles setting as GitHub Codespaces. You can configure it in either your personal **Copilot** > **Cloud** settings or your Codespaces settings. You do not need to create a codespace to use dotfiles with Copilot.

Personal custom instructions apply to every conversation you have with Copilot in the cloud, so Copilot always responds in your preferred language, tone, and style.

Examples of custom instructions you can add:

* `Always respond in Spanish.`
* `Use a helpful, collegial tone. Keep explanations brief, but provide enough context to understand the code.`
* `Always provide examples in TypeScript.`

Multiple types of custom instructions can apply to a request sent to Copilot. Personal instructions take the highest priority. Repository instructions come next, and then organization instructions are prioritized last. However, all sets of relevant instructions are provided to Copilot.

Whenever possible, try to avoid providing conflicting sets of instructions. If you are concerned about response quality, you can temporarily disable repository instructions. See [Adding repository custom instructions for GitHub Copilot](/en/copilot/how-tos/copilot-on-github/customize-copilot/add-custom-instructions/add-repository-instructions?tool=webui).

## Preparing your dotfiles repository

Your dotfiles repository must contain a `.copilot` directory at its root. If this directory is not present, Copilot does not install the repository's dotfiles.

Add the personal customizations you want to use to this directory. For example:

```text
.copilot/
  copilot-instructions.md
  skills/
    release-notes/
      SKILL.md
  agents/
    reviewer.agent.md
```

These files use the same formats and home-directory locations as personal customizations for GitHub Copilot CLI. Use the following guides to write their contents:

| Customization          | Location in your dotfiles repository  | Guidance                                                                                                                                                                                                                                      |
| ---------------------- | ------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Personal instructions  | `.copilot/copilot-instructions.md`    | Write guidance to apply across repositories, such as your preferred coding conventions or response style. See [Adding custom instructions for GitHub Copilot CLI](/en/copilot/how-tos/copilot-cli/customize-copilot/add-custom-instructions). |
| Personal skills        | `.copilot/skills/SKILL-NAME/SKILL.md` | Define repeatable workflows with instructions, scripts, and resources. See [Adding agent skills for GitHub Copilot CLI](/en/copilot/how-tos/copilot-cli/customize-copilot/add-skills).                                                        |
| Personal custom agents | `.copilot/agents/AGENT-NAME.agent.md` | Define specialist agents with their own instructions and tools. See [Creating and using custom agents for GitHub Copilot CLI](/en/copilot/how-tos/copilot-cli/customize-copilot/create-custom-agents-for-cli).                                |

Replace `SKILL-NAME` and `AGENT-NAME` with descriptive names for your skill and agent. The linked guides also describe CLI-specific commands, which are not required to set up your dotfiles repository.

Do not commit secrets or credentials to your dotfiles repository.

## Enabling dotfiles for your cloud sessions

1. Create a dotfiles repository that you own on GitHub, or use an existing one.

2. Add a `.copilot` directory at the root of the repository, with your personal customization files as described above.

3. Commit and push your changes to the repository.

4. In your personal GitHub settings, under **Copilot**, click **Cloud**. Enable dotfiles and select your repository.

   Alternatively, configure dotfiles in your [Codespaces settings](https://github.com/settings/codespaces?utm_source=personalize-cloud-sessions-codespaces-dotfiles\&utm_medium=docs\&utm_campaign=universe-2026). Both settings pages share the same selection, so changing it also changes the dotfiles repository used for your codespaces.

5. Start a session in a cloud sandbox, or resume an existing cloud sandbox session. Where you can choose an environment, select **Cloud**, not **Actions**. For more information, see [About cloud sandboxes for GitHub Copilot](/en/copilot/concepts/security-governance-and-network-settings/about-cloud-sandboxes).

When the cloud sandbox is created or resumed, Copilot copies the contents of your dotfiles repository into the sandbox's home directory, making your personal customizations available under `~/.copilot`.

## How dotfiles are applied

If your dotfiles repository contains a root `.copilot` directory, Copilot copies the entire repository's contents, not just `.copilot`.

Unlike GitHub Codespaces, Copilot does not run dotfiles installation scripts such as `install.sh` or `bootstrap.sh`. Include your customization files directly in the repository rather than relying on a script to create them.

Changes to your dotfiles repository take effect the next time a cloud sandbox is created or resumed. They are not applied to a sandbox while it is running.

## Adding personal custom instructions

To add personal custom instructions for Copilot in the cloud on GitHub:

1. Open a [Copilot](https://github.com/copilot?ref_product=copilot\&ref_type=engagement\&ref_style=text\&utm_source=personalize-cloud-sessions-start-session-cta\&utm_medium=docs\&utm_campaign=universe-2026) session.

2. In the bottom left menu, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="The Gear icon" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg>**.

3. Add natural language instructions to the text box.

   Use any format. For example, a single block of text, each instruction on a new line, or instructions separated by blank lines.

4. Click **Save**.

Your instructions are now active and remain active until you change or remove them.

For a curated collection of examples of personal custom instructions, see [Custom instructions](/en/copilot/tutorials/customization-library/custom-instructions).

<div class="border rounded-2 p-3">

Did you successfully personalize your cloud sessions?

<a href="https://docs.github.io/success-test/yes.html" target="_blank" class="btn btn-outline mt-3 mr-3 no-underline"><span>Yes</span></a>  <a href="https://docs.github.io/success-test/no.html" target="_blank" class="btn btn-outline mt-3 mr-3 no-underline"><span>No</span></a>

</div>