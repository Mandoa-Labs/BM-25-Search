# Security overview

You can gain insights into the overall security landscape of your organization or enterprise and identify repositories that require intervention using security overview.

Security overview provides insights into the security of code stored in repositories in your organization.

* **All organizations** on GitHub Team can use the free **secret risk assessment** to evaluate the exposure of their organization to leaked secrets, see [Viewing your security risk assessment reports](/en/code-security/securing-your-organization/understanding-your-organizations-exposure-to-leaked-secrets/viewing-the-secret-risk-assessment-report-for-your-organization).
* GitHub Team accounts that purchase **GitHub Secret Protection or GitHub Code Security** have access to views with additional insights.

The information below describes the views available to organizations with GitHub Secret Protection or GitHub Code Security that you can use to identify trends in detection, remediation, and prevention of security alerts and dig deep into the current state of your repositories.

## About the views

> \[!NOTE]
> All views show information and metrics for the **default** branches of the repositories you have permission to view in an organization or enterprise.

The views are interactive with filters that allow you to look at the aggregated data in detail and identify sources of high risk, see security trends, and see the impact of pull request analysis on blocking security vulnerabilities entering your code. As you apply multiple filters to focus on narrower areas of interest, all data and metrics across the view change to reflect your current selection. For more information, see [Filtering alerts in security overview](/en/code-security/security-overview/filtering-alerts-in-security-overview).

From security overview, you can download comma-separated values (CSV) files containing data from several pages of your organization or enterprise's security overview. These files can be used for efforts like security research and in-depth data analysis, and can integrate easily with external datasets. For more information, see [Exporting data from security overview](/en/code-security/security-overview/exporting-data-from-security-overview).

There are dedicated views for each type of security alert. You can limit your analysis to a specific type of alert, and then narrow the results further with a range of filters specific to each view. For example, in the secret scanning view, you can use the "Secret type" filter to view only secret scanning alerts for a specific secret, like a GitHub personal access token.

> \[!NOTE]
> Security overview displays active alerts raised by security features. If there are no alerts shown in security overview for a repository, undetected security vulnerabilities or code errors may still exist or the feature may not be enabled for that repository.

## About security overview for organizations

The application security team at your company can use the different views for both broad and specific analyses of your organization's security status. For example, the team can use the "Overview" dashboard view to track your organization's security landscape and progression.

You can find security overview on the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab for any organization. Each view shows a summary of the data that you have access to. As you add filters, all data and metrics across the view change to reflect the repositories or alerts that you've selected.

Security overview has multiple views that provide different ways to explore enablement and alert data.

* **Overview:** visualize trends in **Detection**, **Remediation**, and **Prevention** of security alerts. For information about accessing and using the dashboard, see [Viewing security insights](/en/code-security/security-overview/viewing-security-insights). For detailed explanations of metrics and calculations, see [Security overview dashboard metrics](/en/code-security/reference/security-at-scale/security-overview-dashboard-metrics).
* **Risk:** explore the risk from security alerts of all types or focus on a single alert type and identify your risk from specific vulnerable dependencies, code weaknesses, or leaked secrets, see [Assessing the security risk of your code](/en/code-security/security-overview/assessing-code-security-risk).
* **Coverage:** assess the adoption of security features across repositories in the organization, see [Assessing adoption of security features](/en/code-security/security-overview/assessing-adoption-code-security).
* **Assessments:** regardless of the enablement status of Advanced Security features, organizations on GitHub Team and GitHub Enterprise can run a free report to scan the code in the organization for leaked secrets, see [Secret security with GitHub](/en/code-security/securing-your-organization/understanding-your-organizations-exposure-to-leaked-secrets/about-secret-risk-assessment).
* **Campaigns:** coordinate and measure targeted remediation efforts, grouping related security tasks across repositories, assigning owners, and tracking progress toward defined risk‑reduction goals.
* **Enablement:** see how quickly different teams are adopting security features.
* **CodeQL pull requests:** assess the impact of running CodeQL on pull requests and how development teams are resolving code scanning alerts, see [Viewing metrics for pull request alerts](/en/code-security/security-overview/viewing-metrics-for-pull-request-alerts).
* **Dependabot**: prioritize and track critical vulnerabilities by identifying, remediating, and measuring security improvements across repositories.
* **Secret scanning:** find out which types of secret are blocked by push protection and which teams are bypassing push protection, see [Viewing metrics for secret scanning push protection](/en/code-security/security-overview/viewing-metrics-for-secret-scanning-push-protection) and [Reviewing requests to bypass push protection](/en/code-security/security-overview/reviewing-requests-to-bypass-push-protection).

You also create and manage security campaigns to remediate alerts from security overview, see [Creating and managing security campaigns](/en/code-security/securing-your-organization/fixing-security-alerts-at-scale/creating-managing-security-campaigns) and [Running a security campaign to fix alerts at scale](/en/code-security/securing-your-organization/fixing-security-alerts-at-scale/best-practice-fix-alerts-at-scale).

## About security overview for enterprises

You can find security overview on the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab for your enterprise. Each page displays aggregated and repository-specific security information for your enterprise.

Security overview for enterprises has multiple views that provide different ways to explore data, including an overview dashboard that visualizes alert trends. For information about the dashboard, see [Viewing security insights](/en/code-security/security-overview/viewing-security-insights) and [Security overview dashboard metrics](/en/code-security/reference/security-at-scale/security-overview-dashboard-metrics).

## Access to data in security overview

What you can see in security overview depends on your role and permissions in the organization or enterprise.

In general:

* **Organization owners and security managers** can view security data across all repositories in their organization.
* **Organization members** can view data only for repositories where they have access to security alerts.
* **Enterprise owners** can view aggregated security data in the enterprise-level security overview for organizations where they are an organization owner or security manager. To see repository-level details, they must have the appropriate role within the organization.

Security overview displays data only for repositories you have permission to view, and some views or actions may be limited based on your role.

For detailed, role-by-role permission information, including which views are available and how repository access affects visibility, see [Security overview permissions](/en/code-security/reference/permissions/security-overview-permissions).

## Understanding dashboard data accuracy

The overview dashboard displays metrics based on the current state of your repositories and the historical state of security alerts. This data model has important implications for data consistency:

**Data changes over time:** Dashboard metrics can change for the same historical time period when viewed at different times. This occurs when repositories are deleted, security advisories are modified, or other changes affect the underlying data. If you need consistent data for compliance reports or auditing purposes, use the audit log instead. See [Auditing security alerts](/en/code-security/getting-started/auditing-security-alerts).

**Alert data is historical; repository attributes are current:** The dashboard tracks security alerts based on their historical state during the selected time period. However, repository filters (such as archived/active status) reflect the *current state* of repositories.

For example, if you archive a repository today, any open alerts in that repository are automatically closed. If you then view the overview dashboard for last week:

* The repository only appears when you filter to show archived repositories (its current state)
* The alerts from that repository appear as open (their state during last week)

This design ensures alert trends accurately reflect security activity during the time period you're analyzing, while repository filters help you focus on your current repository structure.

## Further reading

* [Quickstart for securing your repository](/en/code-security/getting-started/securing-your-repository)
* [Configuring security features in your organization](/en/code-security/securing-your-organization)
* [Introduction to adopting GitHub Advanced Security at scale](/en/code-security/adopting-github-advanced-security-at-scale/introduction-to-adopting-github-advanced-security-at-scale)