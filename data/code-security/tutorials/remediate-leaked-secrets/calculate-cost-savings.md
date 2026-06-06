# Calculating the cost savings of push protection

Estimate the remediation time and labor costs you'll avoid by preventing leaked secrets.

## What is the cost savings calculator?

You can use the ROI calculator to estimate the cost avoided by preventing leaked secrets with push protection. This information can help you:

* Determine how widely to enable GitHub Secret Protection in your organization.
* Compare the estimated impact of push protection in different teams or environments.
* Communicate time and cost implications of rollout decisions to stakeholders.

Push protection is a paid feature which is available with GitHub Secret Protection. For more information, see [Pricing and enabling GitHub Secret Protection](/en/code-security/securing-your-organization/understanding-your-organizations-exposure-to-leaked-secrets/choosing-github-secret-protection).

## Prerequisites

* You need to have generated a secret risk assessment for your organization. See [Viewing your security risk assessment reports](/en/code-security/securing-your-organization/understanding-your-organizations-exposure-to-leaked-secrets/viewing-the-secret-risk-assessment-report-for-your-organization).
* You have realistic values for:
  * Average remediation time per leaked secret (hours)
  * Average annual developer salary (USD)

## Estimating cost savings from push protection

1. On GitHub, navigate to the main page of the organization.
2. Under your organization name, click the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab.
3. In the sidebar, under "Security", click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-key" aria-label="key" role="img"><path d="M10.5 0a5.499 5.499 0 1 1-1.288 10.848l-.932.932a.749.749 0 0 1-.53.22H7v.75a.749.749 0 0 1-.22.53l-.5.5a.749.749 0 0 1-.53.22H5v.75a.749.749 0 0 1-.22.53l-.5.5a.749.749 0 0 1-.53.22h-2A1.75 1.75 0 0 1 0 14.25v-2c0-.199.079-.389.22-.53l4.932-4.932A5.5 5.5 0 0 1 10.5 0Zm-4 5.5c-.001.431.069.86.205 1.269a.75.75 0 0 1-.181.768L1.5 12.56v1.69c0 .138.112.25.25.25h1.69l.06-.06v-1.19a.75.75 0 0 1 .75-.75h1.19l.06-.06v-1.19a.75.75 0 0 1 .75-.75h1.19l1.023-1.025a.75.75 0 0 1 .768-.18A4 4 0 1 0 6.5 5.5ZM11 6a1 1 0 1 1 0-2 1 1 0 0 1 0 2Z"></path></svg> Assessments**.
4. On the top right corner of the banner, click **Get started**.
5. In the dropdown, select **Estimate push protection savings**.
6. Review the non-editable value for "Preventable leaks" (P). If 0, a baseline value (such as 70) is shown for modeling purposes.
7. Enter or adjust the average developer annual compensation (C), in USD.
   * Use blended fully loaded annual compensation (salary + benefits).
   * Keep estimates conservative to avoid overstatement.
8. Enter or adjust the time to remediate each leaked secret (T), in hours. We recommend you use an average remediation time that reflects steps for revoking, rotating, and validating secrets, as well as notifying your teams or customers:
   * T = 1-1.5 hours for simple rotation, minimal coordination
   * T = 2-3 hours to account for a distributed team or extra checks
   * T = 3-4 hours if you work in a regulated / audited environment
9. Review the outputs from the **Return on investment** panel:
   * **Secrets prevented**: The number of preventable secrets detected.
   * **Time saved**: Total hours saved by preventing these secrets, based on your input.
   * **Potential savings with push protection**: The total estimated labor cost avoided.

<div class="ghd-alert ghd-alert-accent ghd-spotlight-accent">

Did you successfully use the ROI calculator to estimate the cost savings of using push protection on your organization?

<a href="https://docs.github.io/success-test/yes.html" target="_blank" class="btn btn-outline mt-3 mr-3 no-underline"><span>Yes</span></a>  <a href="https://docs.github.io/success-test/no.html" target="_blank" class="btn btn-outline mt-3 mr-3 no-underline"><span>No</span></a>

</div>

## Understanding your results

Next, review the results to understand their implications and determine the appropriate scope for rolling out push protection in your organization. Keep the following information in mind as you interpret your results.

The calculator **does**:

* Estimate savings for **secrets blocked by push protection** only.
* Base results on your risk assessment and assumptions you provide.
* Provide estimates based on **labor cost avoidance** only.
* Provide a modeled baseline for preventable leaks if no secrets were detected in the current scan window.

The calculator does **not**:

* Include any costs related to data breaches or external impacts. For informational purposes, the cost of a data breach averaged $4.88M in 2024 according to IBM.
* Include time savings from other GitHub Secret Protection features.
* Support currencies other than USD.

## Troubleshooting

If you run into problems using the calculator, use the following table to troubleshoot.

| Issue                            | Action                                                                                                                                                                                                                                                                                                                                                                                                              |
| -------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Preventable secrets = 0**      | When no preventable secrets are detected, the calculator displays a default baseline value (such as 70) for modeling purposes.<br> To replace the baseline with real data, enable push protection on more repositories and allow secret scanning to collect more information.                                                                                                                                       |
| **Estimated savings shows $5M+** | The calculator is capped at $5M. If your modeled savings exceed this threshold, the value will be displayed as "$5M+" in the UI. To get the precise amount, export your input values (preventable secrets, time to remediate, and developer salary) and replicate the formula in a spreadsheet:</br>`(Secrets prevented) × (Time to remediate) × (Hourly rate)` where hourly rate is calculated as `Salary ÷ 2080`. |
| **Value seems low**              | Review your inputs for time to remediate and average developer compensation. Ensure you have included all steps involved in remediation (such as revoke, rotate, validate, and notify) and that the salary reflects a fully loaded annual cost.                                                                                                                                                                     |
| **Value seems high**             | Double-check your input values for time to remediate and average compensation to make sure they are realistic and not overstated. Remove any outliers that could be skewing the estimate.                                                                                                                                                                                                                           |

## Further reading

* [Detecting and Preventing Secret Leaks in Code](https://github.com/resources/whitepapers/secret-scanning-a-key-to-your-cybersecurity-strategy) in  GitHub's `resources` repository