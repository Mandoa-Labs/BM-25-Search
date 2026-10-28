# Getting pull requests ready to merge with Agent Merge

Let Copilot watch your pull requests, and fix failed workflows and merge conflicts, while you focus on other work.

## About Agent Merge

Agent Merge is part of Copilot in the cloud. It watches a pull request for blockers you choose and starts work automatically when it finds one. You can allow Copilot to fix failed GitHub Actions workflows, resolve merge conflicts, or both.

Agent Merge helps get a pull request ready to merge and keep it there. It does not replace your review of the changes or the repository's merge requirements.

## Prerequisites and limitations

To use Agent Merge, you must have access to Copilot in the cloud through a paid Copilot plan. If your organization or enterprise provides your Copilot access, its policies must allow you to use Copilot in the cloud.

The repository's **Enable automations** Copilot policy must also be enabled.

Agent Merge does not support stacked pull requests or pull requests opened from a fork.

## Enabling Agent Merge for a pull request

1. On GitHub, open the pull request you want Copilot to watch.
2. In the merge box of the pull request, click **Watch and fix**.
3. Choose the actions you want Copilot to perform:

   * **Fix failed Actions workflows**: Allow Copilot to investigate and fix failing GitHub Actions workflows.
   * **Resolve merge conflicts**: Allow Copilot to resolve conflicts between the pull request's branch and its base branch.

When one of the blockers you selected appears, Copilot starts working in a cloud development environment to fix it.

## Following Agent Merge's work

As Copilot watches your pull request, you'll see updates in the Agent Merge section of the merge box.

When Copilot starts work, an update appears as a pull request timeline event. The update explains why it started, such as a failed workflow or a merge conflict.

Review the changes Copilot makes and check the workflow results before merging. Agent Merge does not remove the need for human review.

## Enabling Agent Merge automatically

You can enable Agent Merge by default for pull requests you create.

1. In the upper-right corner of any page on GitHub, click your profile picture, then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> Settings**.
2. In the sidebar, under **Copilot**, click **Cloud**.
3. Select **Enable Agent Merge automatically for pull requests I create**.
4. Use the **Fix failed Actions workflows** and **Resolve merge conflicts** switches to choose which actions Copilot can perform when Agent Merge is automatically enabled for your pull requests. You can enable either action or both.

## Disabling Agent Merge for a pull request

You can disable Agent Merge for a pull request if you enabled it or if you have write access to the repository.

1. On GitHub, open the pull request.
2. In the merge box at the bottom of the pull request, click **Unassign Copilot**.

## Using Agent Merge with auto-merge

Agent Merge fixes blockers, while auto-merge merges a pull request after all required reviews and status checks pass. Enabling Agent Merge does not enable auto-merge.

You can combine the two to let Copilot get the pull request ready and keep it ready, while GitHub merges it as soon as all requirements are met. For setup guidance, see [Automatically merging a pull request](/en/pull-requests/how-tos/merge-and-close-pull-requests/automatically-merging-a-pull-request).

## Customizing Agent Merge's environment

Although Agent Merge is part of Copilot in the cloud, its fixes run in an GitHub Actions-based development environment, not a cloud sandbox. It uses the same repository customizations as other Copilot tasks that run on GitHub Actions, including:

* Setup steps in `.github/workflows/copilot-setup-steps.yml`. See [Configure the development environment for agents on GitHub Actions](/en/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/customize-the-agent-environment).
* Repository custom instructions. See [Adding repository custom instructions for GitHub Copilot](/en/copilot/how-tos/copilot-on-github/customize-copilot/add-custom-instructions/add-repository-instructions).
* Repository agent skills. See [Adding agent skills for GitHub Copilot](/en/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/add-skills).

## Usage and billing

The AI credits used by Agent Merge are charged to the user who enables it for the pull request, not necessarily the pull request's author. For more information about usage and allowances, see [GitHub Copilot billing and usage](/en/copilot/concepts/billing-and-usage).