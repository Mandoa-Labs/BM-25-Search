# Managing GitHub Copilot in the cloud for your enterprise or organization

Allow users to use Copilot on GitHub and start cloud sessions from local clients.

Copilot in the cloud is a connected experience that lets users start and resume cloud sessions across the GitHub website, GitHub Mobile, Copilot CLI, and the Copilot app. See [GitHub Copilot on GitHub.com and GitHub Mobile](/en/copilot/concepts/copilot-surfaces/copilot-on-github).

The **Copilot in the cloud** policy determines:

* Whether users can access the chat interface or assign work to Copilot on the GitHub website and GitHub Mobile
* Whether users can start sessions in cloud sandboxes from local clients (Copilot CLI and the Copilot app)

This feature is enabled by default. To ensure data security, chat sessions are scoped by default to either a single organization or the user's personal repositories. If you have enabled single sign-on (SSO), users will need to authenticate with SSO to access session data from a repository associated with that organization.

## What if I already set policies for Copilot cloud agent and Copilot Chat in GitHub?

The individual policies for Copilot cloud agent, Copilot Chat in GitHub, and Copilot Chat in GitHub Mobile have been replaced by the **Copilot in the cloud** policy. If you previously opted a repository out of Copilot cloud agent, that repository exclusion is carried over to the new experience.

Be aware that coverage of other policies and enterprise managed settings is different for the unified surface. Check that your governance settings still meet your needs. See [Supported surfaces for GitHub Copilot policies](/en/copilot/reference/supported-surfaces-for-policies) and [Enterprise managed settings](/en/copilot/reference/enterprise-administrators/enterprise-managed-settings#supported-keys).

## Prerequisites

Before enabling Copilot in the cloud, you may want to review your enterprise policies, repository protections, and runner settings to ensure agents will operate in a secure environment. See [Building a secure cloud environment for agents in your enterprise](/en/copilot/tutorials/cloud-agent/build-guardrails).

## Managing the Copilot in the cloud policy

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.

2. At the top of the page, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copilot" aria-label="copilot" role="img"><path d="M7.998 15.035c-4.562 0-7.873-2.914-7.998-3.749V9.338c.085-.628.677-1.686 1.588-2.065.013-.07.024-.143.036-.218.029-.183.06-.384.126-.612-.201-.508-.254-1.084-.254-1.656 0-.87.128-1.769.693-2.484.579-.733 1.494-1.124 2.724-1.261 1.206-.134 2.262.034 2.944.765.05.053.096.108.139.165.044-.057.094-.112.143-.165.682-.731 1.738-.899 2.944-.765 1.23.137 2.145.528 2.724 1.261.566.715.693 1.614.693 2.484 0 .572-.053 1.148-.254 1.656.066.228.098.429.126.612.012.076.024.148.037.218.924.385 1.522 1.471 1.591 2.095v1.872c0 .766-3.351 3.795-8.002 3.795Zm0-1.485c2.28 0 4.584-1.11 5.002-1.433V7.862l-.023-.116c-.49.21-1.075.291-1.727.291-1.146 0-2.059-.327-2.71-.991A3.222 3.222 0 0 1 8 6.303a3.24 3.24 0 0 1-.544.743c-.65.664-1.563.991-2.71.991-.652 0-1.236-.081-1.727-.291l-.023.116v4.255c.419.323 2.722 1.433 5.002 1.433ZM6.762 2.83c-.193-.206-.637-.413-1.682-.297-1.019.113-1.479.404-1.713.7-.247.312-.369.789-.369 1.554 0 .793.129 1.171.308 1.371.162.181.519.379 1.442.379.853 0 1.339-.235 1.638-.54.315-.322.527-.827.617-1.553.117-.935-.037-1.395-.241-1.614Zm4.155-.297c-1.044-.116-1.488.091-1.681.297-.204.219-.359.679-.242 1.614.091.726.303 1.231.618 1.553.299.305.784.54 1.638.54.922 0 1.28-.198 1.442-.379.179-.2.308-.578.308-1.371 0-.765-.123-1.242-.37-1.554-.233-.296-.693-.587-1.713-.7Z"></path><path d="M6.25 9.037a.75.75 0 0 1 .75.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 .75-.75Zm4.25.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 1.5 0Z"></path></svg> AI controls**.

3. In the sidebar, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copilot" aria-label="copilot" role="img"><path d="M7.998 15.035c-4.562 0-7.873-2.914-7.998-3.749V9.338c.085-.628.677-1.686 1.588-2.065.013-.07.024-.143.036-.218.029-.183.06-.384.126-.612-.201-.508-.254-1.084-.254-1.656 0-.87.128-1.769.693-2.484.579-.733 1.494-1.124 2.724-1.261 1.206-.134 2.262.034 2.944.765.05.053.096.108.139.165.044-.057.094-.112.143-.165.682-.731 1.738-.899 2.944-.765 1.23.137 2.145.528 2.724 1.261.566.715.693 1.614.693 2.484 0 .572-.053 1.148-.254 1.656.066.228.098.429.126.612.012.076.024.148.037.218.924.385 1.522 1.471 1.591 2.095v1.872c0 .766-3.351 3.795-8.002 3.795Zm0-1.485c2.28 0 4.584-1.11 5.002-1.433V7.862l-.023-.116c-.49.21-1.075.291-1.727.291-1.146 0-2.059-.327-2.71-.991A3.222 3.222 0 0 1 8 6.303a3.24 3.24 0 0 1-.544.743c-.65.664-1.563.991-2.71.991-.652 0-1.236-.081-1.727-.291l-.023.116v4.255c.419.323 2.722 1.433 5.002 1.433ZM6.762 2.83c-.193-.206-.637-.413-1.682-.297-1.019.113-1.479.404-1.713.7-.247.312-.369.789-.369 1.554 0 .793.129 1.171.308 1.371.162.181.519.379 1.442.379.853 0 1.339-.235 1.638-.54.315-.322.527-.827.617-1.553.117-.935-.037-1.395-.241-1.614Zm4.155-.297c-1.044-.116-1.488.091-1.681.297-.204.219-.359.679-.242 1.614.091.726.303 1.231.618 1.553.299.305.784.54 1.638.54.922 0 1.28-.198 1.442-.379.179-.2.308-.578.308-1.371 0-.765-.123-1.242-.37-1.554-.233-.296-.693-.587-1.713-.7Z"></path><path d="M6.25 9.037a.75.75 0 0 1 .75.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 .75-.75Zm4.25.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 1.5 0Z"></path></svg> **Copilot**.

4. Under "Features & clients", click **Configure features & clients**.

5. Select a global policy for Copilot in the cloud, then communicate your decision with your organizations.

   > [!TIP] If you select **Enabled for selected organizations**, click **Manage organizations**, then **Select organizations**. In the "Copilot in the cloud" dialog, select the organizations to enable, then click **Save**. To select organizations based on custom properties instead, use the REST API. See [REST API endpoints for Copilot cloud agent management](/en/rest/copilot/copilot-coding-agent-management#selecting-organizations-with-custom-properties).

6. By default, the feature will be available in all repositories in selected organizations. If there are repositories where the cloud agent should be blocked for all users, tell organization owners to configure this setting. See [Managing GitHub Copilot in the cloud for your organization](/en/copilot/how-tos/administer-copilot/manage-for-organization/add-copilot-cloud-agent#disabling-or-enabling-copilot-cloud-agent-in-your-repositories).

## Configuring permissions for tool calls

By default, cloud sessions run in interactive mode with assisted tool approvals. This gives users the best balance between control and ease of use. Users can also enable "allow-all" mode unless your enterprise has blocked this option.

To disable "allow-all" mode or assisted approval, or configure permissions for specific operations, you can use your enterprise's `managed-settings.json` file. See [Getting started with enterprise-managed settings](/en/copilot/how-tos/administer-copilot/manage-for-enterprise/use-managed-settings/get-started).

## Configuring MCP servers and web access

Copilot automatically has access to a small number of default MCP servers. See [Model Context Protocol (MCP)](/en/copilot/concepts/agents/cloud-agent/mcp-and-cloud-agent#default-mcp-servers).

You can enable third-party MCP servers for your enterprise.

1. In the sidebar, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-mcp" aria-label="mcp" role="img"><path d="M5.52 1.12a3.578 3.578 0 0 1 6.078 2.98 3.578 3.578 0 0 1 2.982 6.08l-3.292 3.293a.252.252 0 0 0 0 .354l.843.843a.749.749 0 1 1-1.06 1.06l-.844-.843a1.75 1.75 0 0 1 0-2.474L13.52 9.12a2.08 2.08 0 0 0 0-2.94 2.08 2.08 0 0 0-2.94 0L7.731 9.03A.75.75 0 0 1 6.67 7.97l2.85-2.85a2.08 2.08 0 0 0 0-2.94 2.08 2.08 0 0 0-2.94 0l-4.799 4.8A.75.75 0 0 1 .72 5.92Z"></path><path d="M7.52 3.12a.749.749 0 1 1 1.06 1.06L5.731 7.03A2.079 2.079 0 0 0 8.67 9.97l2.85-2.85a.749.749 0 1 1 1.06 1.06l-2.849 2.85A3.578 3.578 0 0 1 4.67 5.97Z"></path></svg> **MCP**.
2. Set a policy for **MCP servers in Copilot**.

For more granular settings, you can configure an allowlist or denylist in your enterprise's `managed-settings.json` file. See [Configuring an MCP server allowlist for your enterprise](/en/copilot/how-tos/administer-copilot/manage-mcp-usage/configure-enterprise-allowlist).

Organization owners can configure the firewall for their organization to determine which external hosts and URLs the cloud agent can access. For more information, see [Customizing or disabling the firewall for GitHub Copilot](/en/copilot/how-tos/copilot-on-github/customize-copilot/customize-the-firewall).

## Configuring session environments

Agent sessions on GitHub can run in a cloud sandbox or on GitHub Actions. Compute costs from both environments draw on the same monthly allowance.

* A cloud sandbox is a faster, lightweight environment that allows users to resume sessions in GitHub's chat interface or in other clients.
* GitHub Actions gives you more control over the environment, such as secrets and variables, setup steps to install dependencies, and access to self-hosted runners or private networking.

For a detailed comparison, see [GitHub Copilot on GitHub.com and GitHub Mobile](/en/copilot/concepts/copilot-surfaces/copilot-on-github#comparison-of-the-two-experiences).

Coverage of policies and enterprise managed settings currently varies between environments. Where users can choose between these environments, cloud sandboxes are the default. However, currently, some interfaces can only run on GitHub Actions (such as assigning an issue to Copilot or mentioning `@Copilot` in a pull request).

Enabling the **Copilot in the cloud** policy automatically makes cloud sandboxes available to users, and cloud sandboxes cannot be disabled separately. See [Managing cloud sandboxes for your organization or enterprise](/en/copilot/how-tos/cloud-and-local-sandboxes/enabling-or-disabling-cloud-sandboxes-for-your-organization).

For more information about configuring the GitHub Actions environment, see [Configure the development environment for agents on GitHub Actions](/en/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/customize-the-agent-environment) and [Configuring runners for GitHub Copilot cloud agent in your organization](/en/copilot/how-tos/administer-copilot/manage-for-organization/configure-runner-for-coding-agent).

## Enabling agent apps and third-party agents

Enterprise owners can enable third-party agents, including agent apps, for their organizations. Once enabled at the enterprise level, organization owners can choose which agents to allow. For more information, see [Agent apps](/en/copilot/concepts/agent-capabilities/about-agents/agent-apps) and [Third-party coding agents](/en/copilot/concepts/agent-capabilities/about-agents/about-third-party-coding-agents).