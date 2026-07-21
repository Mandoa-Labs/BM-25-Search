# Exploring GitHub Code Quality results in your organization

Understand your organization's code health at a glance with the organization-level dashboard for Code Quality.

## Prerequisites

* If your organization belongs to an enterprise, an enterprise owner must enable Code Quality for your organization. See [Allowing use of GitHub Code Quality in your enterprise](/en/code-security/how-tos/secure-at-scale/configure-enterprise-security/configure-specific-tools/allow-github-code-quality-in-enterprise?utm_campaign=code-quality-ga-july-2026\&utm_medium=docs\&utm_source=docs-explore-cq-enterprise-enablement).
* Your organization must have repositories with Code Quality enabled. See [Enabling GitHub Code Quality](/en/code-security/how-tos/maintain-quality-code/enable-code-quality?utm_campaign=code-quality-ga-july-2026\&utm_medium=docs\&utm_source=docs-explore-cq-repo-enablement).

## Viewing code quality insights for your organization

1. On GitHub, navigate to the main page of your organization. For example, from [https://github.com/settings/organizations](https://github.com/settings/organizations?ref_product=github\&ref_type=engagement\&ref_style=text\&utm_campaign=code-quality-ga-july-2026\&utm_medium=docs\&utm_source=docs-explore-cq-org-settings).
2. Under your organization name, click the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab.
3. In the "Insights" section of the sidebar, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-code-square" aria-label="code-square" role="img"><path d="M0 1.75C0 .784.784 0 1.75 0h12.5C15.216 0 16 .784 16 1.75v12.5A1.75 1.75 0 0 1 14.25 16H1.75A1.75 1.75 0 0 1 0 14.25Zm1.75-.25a.25.25 0 0 0-.25.25v12.5c0 .138.112.25.25.25h12.5a.25.25 0 0 0 .25-.25V1.75a.25.25 0 0 0-.25-.25Zm7.47 3.97a.75.75 0 0 1 1.06 0l2 2a.75.75 0 0 1 0 1.06l-2 2a.749.749 0 0 1-1.275-.326.749.749 0 0 1 .215-.734L10.69 8 9.22 6.53a.75.75 0 0 1 0-1.06ZM6.78 6.53 5.31 8l1.47 1.47a.749.749 0 0 1-.326 1.275.749.749 0 0 1-.734-.215l-2-2a.75.75 0 0 1 0-1.06l2-2a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042Z"></path></svg> **Code quality**.

> \[!NOTE]
> What you see on the dashboard depends on your access:
>
> * Organization owners see data for **every** repository that has Code Quality enabled.
> * All other organization members see data only for repositories where they can view Code Quality findings (the repository-level pages), up to a maximum of 3,000 repositories.

## Interpreting the score distribution chart

The score distribution chart provides a visual overview of the code health of your organization. Each bubble represents a collection of repositories with the same maintainability and reliability scores.

* The **position** of each bubble demonstrates the overall health of those repositories. Higher bubbles represent higher maintainability scores, while bubbles further to the right represent higher reliability scores.
* The **color and border pattern** of a bubble indicate the severity of the lower score for those repositories. For example, a bubble with a "Poor" score in either category will always be red with a dashed border.
* The **size** of each bubble represents the number of repositories with that particular score combination.

To view the maintainability score, reliability score, and number of repositories represented by a particular bubble, hover over the bubble.

## Exploring the repository table

Below the bubble chart, there is a table that lists all repositories in your organization. Here, you can view code quality findings, along with more detailed information about those findings.

You can sort the repository table in ascending or descending order for any column by clicking the column header.

## Investigating low-scoring repositories

1. To filter the dashboard data for the lowest-performing repositories, on the score distribution chart, click the bubble with the lowest combined scores.
2. Scroll down to the repository table. By default, the table is sorted from most to least recent repository scan, helping you prioritize current quality issues.
3. Optionally, to prioritize repositories with the highest number of CodeQL findings, click **Standard Findings** twice.
4. To view the repository-level dashboard for a specific repository, click the repository's name.

## Next steps

To understand the code health information available on the repository-level dashboard, see [Interpreting the code quality results for your repository](/en/code-security/how-tos/maintain-quality-code/interpret-results).