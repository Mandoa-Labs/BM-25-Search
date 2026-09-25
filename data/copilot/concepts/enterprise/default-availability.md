# About default availability of Copilot features and models

Policies control whether unconfigured features and models default to enabled or disabled.

For enterprises with Copilot Business or Copilot Enterprise plans, two separate policies control whether unconfigured generally available (GA) features and models default to enabled or disabled. If these policies are enabled, users benefit from the latest features and models without the need for administrator intervention.

<!-- expires 2026-10-22 -->

The models policy is already active. The feature policy will become active soon.

<!-- end expires 2026-10-22 -->

<!-- expires 2026-10-22 -->

## Default availability of features

The **Default policy for new features** policy is available to configure but is **not** currently active. It will start applying to new and existing GA features from October 22, 2026. In your policy settings, you will see a banner showing how many eligible policies are currently unconfigured, so you can assess the impact of your global default and explicitly configure individual policies before October 22.

This policy is enabled by default. If you don't take action, unconfigured features will be enabled on October 22.

<!-- end expires 2026-10-22 -->

### What does the policy do?

Your setting for this policy determines the enablement status of:

* New GA (general availability) features
* Features that move from preview to GA
* Existing GA features that are **Unconfigured** in your policy settings

The policy can be configured in an enterprise and its organizations. At the enterprise level, it applies to features labeled as **Unconfigured**. At the organization level, it applies to features that an enterprise owner has set to **Let organizations decide**, but that an organization owner has not explicitly configured.

The policy does **not** apply to features in preview.

### What counts as a feature?

For the purposes of this policy, a "feature" refers to any policy configured on an enterprise's "Features & clients" page (`github.com/enterprises/ENTERPRISE/ai-controls/copilot/features`), **plus**:

* The **Copilot code review** policy on the "Agents" page
* The **MCP servers in Copilot** policy on the "MCP" page

The following policies are exceptions and are **not** affected:

* Restrictive model policies on GHE.com: **Restrict Copilot to data residency models** and **Restrict Copilot to FedRAMP models**
* **Store local sessions in the Cloud** for Copilot CLI and VS Code

## Default availability of models

The **Default availability for released models** policy is active and affects new and unconfigured GA models.

### Which models follow the policy?

The default policy applies to models that you have not explicitly configured. These models are indicated in your enterprise or organization's model settings with the **Delegate to Default Policy** label. When a new model is released, it inherits the default until you explicitly configure it.

The following models are **not** in scope. They are disabled by default, regardless of your "Default availability" policy setting.

* Pre-GA models
* Open weight models (DeepSeek, Kimi K2.7 Code, Kimi K3)
* Models that are not covered by GitHub's data retention agreement (Claude Fable 5, Claude Fable 5.1)
* For enterprises that have restricted models to data-resident or FedRAMP-compliant models, any models that do not respect these policies

## How do I prevent default enablement?

To disable default enablement entirely, disable the default policies in your enterprise or organization's settings. You can set a policy for the entire enterprise, or disable the policy only in organizations with stricter compliance requirements.

If you keep the default availability policies enabled, you can explicitly disable individual features and models so that they are not eligible for automatic enablement.

* For features, see [Managing policies and features for GitHub Copilot in your enterprise](/en/copilot/how-tos/administer-copilot/manage-for-enterprise/manage-enterprise-policies) and [Managing policies and features for GitHub Copilot in your organization](/en/copilot/how-tos/administer-copilot/manage-for-organization/manage-policies).
* For models, see [Managing availability of models in your enterprise](/en/copilot/how-tos/administer-copilot/manage-for-enterprise/manage-availability-of-default-models) and [Managing the availability of models in an organization](/en/copilot/how-tos/administer-copilot/manage-for-organization/manage-default-models).

## How do I prepare for new releases?

We recommend keeping up with new releases and GA announcements so you can choose your enablement settings. New features and models are announced on GitHub's changelog. For more information, see [Learning about new features and models](/en/copilot/concepts/enterprise/learning-about-new-features-and-models).