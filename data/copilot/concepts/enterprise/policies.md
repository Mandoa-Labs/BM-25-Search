# GitHub Copilot policies for enterprises and organizations

Control the availability of GitHub Copilot features and models for your users.

## How do policies work?

You will find policies for GitHub Copilot on your enterprise's **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copilot" aria-label="copilot" role="img"><path d="M7.998 15.035c-4.562 0-7.873-2.914-7.998-3.749V9.338c.085-.628.677-1.686 1.588-2.065.013-.07.024-.143.036-.218.029-.183.06-.384.126-.612-.201-.508-.254-1.084-.254-1.656 0-.87.128-1.769.693-2.484.579-.733 1.494-1.124 2.724-1.261 1.206-.134 2.262.034 2.944.765.05.053.096.108.139.165.044-.057.094-.112.143-.165.682-.731 1.738-.899 2.944-.765 1.23.137 2.145.528 2.724 1.261.566.715.693 1.614.693 2.484 0 .572-.053 1.148-.254 1.656.066.228.098.429.126.612.012.076.024.148.037.218.924.385 1.522 1.471 1.591 2.095v1.872c0 .766-3.351 3.795-8.002 3.795Zm0-1.485c2.28 0 4.584-1.11 5.002-1.433V7.862l-.023-.116c-.49.21-1.075.291-1.727.291-1.146 0-2.059-.327-2.71-.991A3.222 3.222 0 0 1 8 6.303a3.24 3.24 0 0 1-.544.743c-.65.664-1.563.991-2.71.991-.652 0-1.236-.081-1.727-.291l-.023.116v4.255c.419.323 2.722 1.433 5.002 1.433ZM6.762 2.83c-.193-.206-.637-.413-1.682-.297-1.019.113-1.479.404-1.713.7-.247.312-.369.789-.369 1.554 0 .793.129 1.171.308 1.371.162.181.519.379 1.442.379.853 0 1.339-.235 1.638-.54.315-.322.527-.827.617-1.553.117-.935-.037-1.395-.241-1.614Zm4.155-.297c-1.044-.116-1.488.091-1.681.297-.204.219-.359.679-.242 1.614.091.726.303 1.231.618 1.553.299.305.784.54 1.638.54.922 0 1.28-.198 1.442-.379.179-.2.308-.578.308-1.371 0-.765-.123-1.242-.37-1.554-.233-.296-.693-.587-1.713-.7Z"></path><path d="M6.25 9.037a.75.75 0 0 1 .75.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 .75-.75Zm4.25.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 1.5 0Z"></path></svg> AI controls** tab or in your organization's settings. Policies control which GitHub Copilot features, agents, and models your users can access, and how they can use those features. For example, a policy controls whether users can use Copilot CLI.

In an enterprise, policies are set at the enterprise level first. For most policies, enterprise administrators can either explicitly enable or disable a policy, or let organizations decide. As an exception, for Copilot cloud agent, enterprises can select exactly which organizations receive access.

Users who receive access to Copilot directly from the enterprise, rather than through an organization, are not covered by the "Let organizations decide" option. A separate **Policies for enterprise-assigned users** setting determines whether "Let organizations decide" policies default to enabled or disabled for these users.

## Who do policies apply to?

Generally, policies only apply to users on your Copilot plan. A user is governed by the policies of the enterprise or organization where they receive a Copilot Business or Copilot Enterprise license.

A small number of policies work differently and govern a setting for everyone. For example, you can block Copilot cloud agent for all users in your enterprise's repositories. If this is the case, you will see this highlighted in the policy description.

## What about users with multiple licenses?

A user can receive access to Copilot from multiple organizations in the same enterprise. If these organizations have configured the same policy differently, the **least restrictive** policy usually applies, but there are some exceptions.

More rarely, if a user receives a license from multiple different enterprises, the **most restrictive** policy across enterprises almost always applies. For example, if any enterprise disables Copilot Chat in GitHub, that feature is disabled for the user.

For model policies on a GitHub Team plan, a user's model access is determined by the organization paying for their usage. You can find this organization under "Usage billed to" on the [Copilot features page](https://github.com/settings/copilot/features).

A user's individual plan is cancelled when they are added to a Copilot Business or Copilot Enterprise plan, so a user's personal policies cannot conflict with an enterprise's or organization's.

To see details for each policy, see [Feature availability when GitHub Copilot policies conflict in organizations](/en/copilot/reference/enterprise-administrators/policy-conflicts).

## Where do policies apply?

Policies can apply to any surface where users authenticate to Copilot, including IDEs, the GitHub website, and Copilot CLI.

However, not all policies apply to every surface. See [Supported surfaces for GitHub Copilot policies](/en/copilot/reference/supported-surfaces-for-policies).

The GitHub Copilot app and Copilot CLI are governed by separate, independent client policies, so you can allow one without allowing the other.

## How can I prevent policy drift?

If too many people have access to policy settings and your enterprise's governance posture isn't clearly communicated, policy settings can drift over time. This is a risk for enterprises with strict compliance requirements.

* Regularly review the people with access to policies:

  * In enterprises, enterprise owners or users with the "Manage enterprise AI controls" custom role permission
  * In organizations, organization owners or users with various granular custom permissions

* Use your audit log to monitor changes to policy settings or organization enablement.

## Setting policies

To set policies, see:

* [Managing policies and features for GitHub Copilot in your enterprise](/en/copilot/how-tos/administer-copilot/manage-for-enterprise/manage-enterprise-policies)
* [Managing policies and features for GitHub Copilot in your organization](/en/copilot/how-tos/administer-copilot/manage-for-organization/manage-policies)