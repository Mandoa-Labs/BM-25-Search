# Learning about new features and models

Stay informed about GitHub Copilot features and models, and make confident decisions about enabling them for your enterprise.

GitHub Copilot is evolving rapidly, with new features and models released regularly. If you're an enterprise administrator, staying informed helps you make confident decisions about which capabilities to enable, when to adopt them, and how to manage risk across your organizations.

This article provides guidance on navigating the Copilot landscape, understanding different types of features and models, and preparing for upcoming changes.

## Keeping up to date with Copilot changes

You can use GitHub Docs and the GitHub Blog to keep track of new releases.

### Learning about new Copilot features

To learn about new Copilot features, we recommend monitoring these two locations:

* **Features overview**: For a complete list of Copilot capabilities, see [GitHub Copilot features](/en/copilot/get-started/features).
* **Changelog**: Follow the [Copilot changelog](https://github.blog/changelog/label/copilot/) for announcements about new and updated features.

Copilot features generally fall into three categories:

<div class="ghd-tool rowheaders">

| Type        | Description                                                                                      | Examples                                                          | Considerations                                                                                                                                                              |
| ----------- | ------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Assistive   | Respond to prompts and provide suggestions, but require human review before changes are made.    | Inline suggestions, Copilot Chat, Copilot pull request summaries. | All changes require user approval.                                                                                                                                          |
| Agentic     | Autonomously research, plan, and make changes on behalf of users.                                | Copilot cloud agent, third-party agents.                          | Can work autonomously, but with built-in protections.                                                                                                                       |
| Third-party | External coding agents that work alongside Copilot cloud agent to complete tasks asynchronously. | Anthropic Claude, OpenAI Codex.                                   | Same as agentic. Review provider documentation and enable via policies. See [About third-party coding agents](/en/copilot/concepts/agents/about-third-party-coding-agents). |

</div>

Each feature has its own enablement requirements and policy settings. When a new feature is released:

1. Review the feature documentation to understand its capabilities.
2. Check the policy settings available at the enterprise and organization level. See [GitHub Copilot policies for enterprises and organizations](/en/copilot/concepts/policies).
3. Consider running a pilot with a subset of users before broader rollout.

### Learning about new Copilot models

GitHub Copilot uses multiple AI models from different providers to power its features. Different models have different strengths: some prioritize speed and cost-efficiency, while others are optimized for accuracy, reasoning, or working with multimodal inputs (like images and code together).

Users will have access to different models depending on the feature they're using and your enterprise's Copilot plan and policies.

You can find information about the models available and upcoming models in the following locations:

* **Supported models**: For a complete list of available models and their capabilities, see [Supported AI models in GitHub Copilot](/en/copilot/reference/ai-models/supported-models).
* **Model comparison**: To compare model capabilities side by side, see [AI model comparison](/en/copilot/reference/ai-models/model-comparison).
* **Changelog**: Model updates are announced in the [Copilot changelog](https://github.blog/changelog/label/copilot/).

#### Default enablement

For enterprises on a Copilot Business or Copilot Enterprise plan, a policy controls whether unconfigured generally available (GA) models are enabled or disabled by default. See [About default availability of Copilot models](/en/copilot/concepts/models/default-availability).

#### Special categories

GitHub categorizes certain types of model, allowing you to plan for model transitions and set user expectations.

<div class="ghd-tool rowheaders">

| Model type    | Description                                                                  | Why it matters                                                                           |
| ------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- |
| Utility model | A small set of models that power background GitHub features across surfaces. | Your enterprise cannot disable these models. Monitor these to ensure they are compliant. |
| Base model    | The default model when no other models are enabled.                          | Automatically enabled within 60 days of designation.                                     |
| LTS model     | A model supported for one year from designation.                             | Allows enterprises to build workflows around a stable model.                             |

</div>

For more information, see [Utility models](/en/copilot/concepts/models/utility-models) and [Base and long-term support (LTS) models](/en/copilot/concepts/models/fallback-and-lts-models).

## Considering different release stages

Copilot features and models progress through different release stages. Understanding release stages helps you decide when to enable features for your organization. Each stage has different expectations for stability and support.

<div class="ghd-tool rowheaders">

| Stage                    | Availability                            | Stability                                       |
| ------------------------ | --------------------------------------- | ----------------------------------------------- |
| Private preview          | Limited set of customers by invitation. | May change significantly based on feedback.     |
| Public preview           | All eligible customers who opt in.      | Functional but may have limitations or change.  |
| Generally available (GA) | All customers.                          | Fully supported and recommended for production. |

</div>

> \[!TIP] Many preview features are covered by the [GitHub Data Protection Agreement](https://gh.io/dpa), meaning you can test them without breaching compliance requirements. See [GitHub DPA-Covered Previews](https://gh.io/dpa-previews) for a list.

Preview features are controlled by policy settings at the organization and enterprise level. The **Opt in to preview features** policy allows administrators to enable or disable preview features on the GitHub website specifically. See [Managing policies and features for GitHub Copilot in your enterprise](/en/copilot/how-tos/administer-copilot/manage-for-enterprise/manage-enterprise-policies) and [Managing policies and features for GitHub Copilot in your organization](/en/copilot/how-tos/administer-copilot/manage-for-organization/manage-policies).

## Reviewing information about Responsible AI

GitHub is committed to responsible AI development and provides transparency documentation for each Copilot feature.

Each Copilot feature has a dedicated **responsible use** article describing its purpose, capabilities, and limitations. See [Responsible use of GitHub Copilot features](/en/copilot/responsible-use).