# Estimating the price of Secret Protection

Learn how to use the pricing calculator to estimate the monthly cost of GitHub Secret Protection for your repositories.

## What is the pricing calculator?

You can use the pricing calculator on the secret risk assessment page to estimate the monthly cost of GitHub Secret Protection for your organization. This tool allows you to preview costs based on your current repositories and active committers, so you can plan for purchase or rollout decisions.

For more information about Secret Protection, see [Pricing and enabling GitHub Secret Protection](/en/code-security/securing-your-organization/understanding-your-organizations-exposure-to-leaked-secrets/choosing-github-secret-protection).

## Prerequisites

You need to have generated a secret risk assessment for your organization. See [Viewing your security risk assessment reports](/en/code-security/securing-your-organization/understanding-your-organizations-exposure-to-leaked-secrets/viewing-the-secret-risk-assessment-report-for-your-organization).

## Estimating the price of Secret Protection

1. On GitHub, navigate to the main page of the organization.
2. Under your organization name, click the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab.
3. In the sidebar, under "Security", click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-key" aria-label="key" role="img"><path d="M10.5 0a5.499 5.499 0 1 1-1.288 10.848l-.932.932a.749.749 0 0 1-.53.22H7v.75a.749.749 0 0 1-.22.53l-.5.5a.749.749 0 0 1-.53.22H5v.75a.749.749 0 0 1-.22.53l-.5.5a.749.749 0 0 1-.53.22h-2A1.75 1.75 0 0 1 0 14.25v-2c0-.199.079-.389.22-.53l4.932-4.932A5.5 5.5 0 0 1 10.5 0Zm-4 5.5c-.001.431.069.86.205 1.269a.75.75 0 0 1-.181.768L1.5 12.56v1.69c0 .138.112.25.25.25h1.69l.06-.06v-1.19a.75.75 0 0 1 .75-.75h1.19l.06-.06v-1.19a.75.75 0 0 1 .75-.75h1.19l1.023-1.025a.75.75 0 0 1 .768-.18A4 4 0 1 0 6.5 5.5ZM11 6a1 1 0 1 1 0-2 1 1 0 0 1 0 2Z"></path></svg> Assessments**.
4. On the top right corner of the banner, click **Get started**.
5. In the dropdown, select **Preview cost and enable Secret Protection**.
6. In the calculator dialog, choose whether to estimate the cost for:
   * **All repositories**: Includes every repository in your organization.
   * **Selected repositories**: Choose specific repositories for the estimate.
     Once you've made your choices, the calculator shows:
     * The **estimated monthly cost** for your organization.
     * The **number of Secret Protection licenses required**, based on active committers in the last 90 days for the selected repositories.
     * The **per-committer rate** (for example, $19 per active committer).
7. To proceed with enabling Secret Protection, click **Review and enable**.

<div class="ghd-alert ghd-alert-accent ghd-spotlight-accent">

Did you successfully use the pricing calculator to estimate the cost of using Secret Protection features on your organization?

<a href="https://docs.github.io/success-test/yes.html" target="_blank" class="btn btn-outline mt-3 mr-3 no-underline"><span>Yes</span></a>  <a href="https://docs.github.io/success-test/no.html" target="_blank" class="btn btn-outline mt-3 mr-3 no-underline"><span>No</span></a>

</div>

## Understanding your results

* **The pricing calculator only provides an estimate.** Actual billing is based on the number of active committers in the selected private repositories during the billing period.
* The calculator **does not include costs for other GitHub Advanced Security features**.
* The calculator **dynamically calculates active committers** for each repository you select. If two repositories share the same number of committers, adding the second repository shows 0 additional committers, because enabling Secret Protection for one also covers the other. This helps you quickly see the true incremental cost as you select repositories.
* USD is the only supported currency.