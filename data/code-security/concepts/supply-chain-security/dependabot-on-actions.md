# Dependabot on GitHub Actions runners

GitHub automatically runs the jobs that generate Dependabot pull requests on GitHub Actions if you have GitHub Actions enabled for the repository. When Dependabot is enabled, these jobs will run by bypassing Actions policy checks and disablement at the repository or organization level.

## About Dependabot on GitHub Actions runners

> \[!IMPORTANT]
> If Dependabot is enabled for a repository, it will always run on GitHub Actions, **bypassing both Actions policy checks and disablement at the repository or organization level**. This ensures that security and version update workflows always run when Dependabot is enabled.

Using GitHub Actions runners allows you to more easily identify Dependabot job errors and manually detect and troubleshoot failed runs. You can also integrate Dependabot into your CI/CD pipelines by using GitHub Actions APIs and webhooks to detect Dependabot job status such as failed runs, and perform downstream processing. For more information, see [REST API endpoints for GitHub Actions](/en/rest/actions) and [Webhook events and payloads](/en/webhooks/webhook-events-and-payloads).

New repositories that you create in your user account or in your organization will automatically be configured to run Dependabot on GitHub Actions using standard GitHub-hosted runners if any of the following is true:

* Dependabot is installed and enabled, and GitHub Actions is enabled and in use.
* The "Dependabot on GitHub Actions runners" setting for your organization is enabled.

Future releases of GitHub will remove the ability to disable running Dependabot on GitHub Actions.

> \[!NOTE] Enabling Dependabot on GitHub Actions may increase the number of concurrent jobs run in your account. If required, customers on enterprise plans can request a higher limit for concurrent jobs. For more information, contact us through the [GitHub Support portal](https://support.github.com/), or contact your sales representative.

## Runner options

You can run Dependabot on GitHub Actions using:

* **Standard GitHub-hosted runners.** These are the default runners used by GitHub to execute GitHub Actions jobs.
* **Larger runners.** These are GitHub-hosted runners with advanced features like more RAM, CPU, and disk space. For more information, see [Using larger runners](/en/actions/using-github-hosted-runners/about-larger-runners).
* **Self-hosted runners.** These runners grant you greater control over Dependabot access to your private registries and internal network resources. Be aware that for security reasons, Dependabot updates on self-hosted runners will not run on public repositories. For more information on assigning a `dependabot` label on self-hosted runners, see [Configuring Dependabot on self-hosted runners](/en/code-security/how-tos/secure-your-supply-chain/manage-your-dependency-security/configure-on-self-hosted-runners).

Running Dependabot on standard GitHub-hosted or self-hosted runners **does not** count towards your included GitHub Actions minutes. For Dependabot on larger runners, GitHub will bill your organization at the regular rate. See [Actions runner pricing](/en/billing/reference/actions-minute-multipliers).

> \[!NOTE]
> Private networking is supported with either an Azure Virtual Network (VNET) or the Actions Runner Controller (ARC) for Dependabot on GitHub Actions. See [Setting up Dependabot to run on self-hosted action runners using the Actions Runner Controller](/en/code-security/dependabot/working-with-dependabot/setting-dependabot-to-run-on-self-hosted-runners-using-arc) and [Setting up Dependabot to run on github-hosted action runners using the Azure Private Network](/en/code-security/dependabot/working-with-dependabot/setting-dependabot-to-run-on-github-hosted-runners-using-vnet).

## How runner settings interact

The Dependabot on GitHub Actions runners and Dependabot on self-hosted runners settings are interdependent:

* Enabling "Dependabot on self-hosted runners" automatically enables "Dependabot on GitHub Actions runners". Disabling "Dependabot on GitHub Actions runners" automatically disables "Dependabot on self-hosted runners".
* When both settings are enabled, Dependabot jobs run **only** on self-hosted runners or larger runners with a `dependabot` label—not on standard GitHub-hosted runners.

> \[!WARNING]
> If both settings are enabled but no self-hosted runners or larger runners with a `dependabot` label are available, Dependabot jobs will remain queued indefinitely. Ensure runners with this label are configured before enabling "Dependabot on self-hosted runners".

## Access and permissions

If you are transitioning to using Dependabot on GitHub Actions runners and you restrict access to your organization's or repository's private resources, you may need to update your list of allowed IP addresses. For example, if you currently limit access to your private resources to the IP addresses that Dependabot uses, you should update your allowlist to use the GitHub-hosted runners IP addresses sourced from the meta API endpoint. For more information, see [REST API endpoints for meta data](/en/rest/meta).

## Next steps

To enable Dependabot on GitHub Actions runners, see [Configuring Dependabot on GitHub-hosted runners](/en/code-security/how-tos/secure-your-supply-chain/manage-your-dependency-security/configure-on-github-hosted-runners) and [Configuring Dependabot on self-hosted runners](/en/code-security/how-tos/secure-your-supply-chain/manage-your-dependency-security/configure-on-self-hosted-runners).