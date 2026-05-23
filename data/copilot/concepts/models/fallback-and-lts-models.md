# Base and long-term support (LTS) models

Learn about base models, long-term support (LTS) models, and how they affect model availability for enterprises using GitHub Copilot.

## About base models

> \[!IMPORTANT]
>
> * On March 18, 2026, GitHub designated GPT-5.3-Codex as the base model.
> * Base models apply only to Copilot Business and Copilot Enterprise.

A base model is the default AI model that GitHub Copilot uses when no other models are enabled. The base model is automatically enabled for all Copilot Business or Copilot Enterprise accounts within 60 days after the model is designated as a base model.

When a new model is designated a base model, the following timeline applies:

| Phase          | Timeline        | What happens                                                                                   |
| -------------- | --------------- | ---------------------------------------------------------------------------------------------- |
| Announcement   | Day 0           | GitHub announces the new base model.                                                           |
| Upgrade window | Day 0 to Day 60 | Customers have 60 days to upgrade their IDE extensions to versions that support the new model. |
| Enablement     | Day 60          | The new model is automatically enabled on all organizations and enterprises as the base model. |

> \[!NOTE]
> The base model has a **1x premium request multiplier** on paid plans. For more information about multipliers, see [Requests in GitHub Copilot](/en/copilot/concepts/billing/copilot-requests#model-multipliers).

## About long-term support (LTS) models

> \[!IMPORTANT]
>
> * On March 18, 2026, GitHub designated GPT-5.3-Codex as the LTS model.
> * LTS models apply only to Copilot Business and Copilot Enterprise.

An LTS model is an AI model that GitHub commits to supporting for an extended period of one year from its designation date. During that period, the model remains available, which allows users to build around the model without concern that it will be closing down unexpectedly.

## Further reading

* [Supported AI models in GitHub Copilot](/en/copilot/reference/ai-models/supported-models)
* [Requests in GitHub Copilot](/en/copilot/concepts/billing/copilot-requests)