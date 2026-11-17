# Viewing repository insights

Use Repository insights to understand how your team acts on Copilot code review feedback and identify opportunities to improve review practices.

When deciding how to improve your team's review process, use Repository insights to see where Copilot code review coverage is missing and which feedback developers act on. It brings review outcomes together with pull request activity, so you can consider them alongside throughput and merge times.

Use this overview to choose where to investigate unaddressed feedback, expand review coverage, or adjust review practices. These signals support those decisions, but do not prove that code is defect-free or that Copilot caused an improvement.

## Prerequisites

<!-- Confirm before publication with the PM/privacy reviewers: Confirm subscription eligibility and rollout restrictions. -->

Repository insights is available for organization-owned repositories. You need read access to the repository.

The Copilot code review section appears only when the organization has enabled both the Copilot usage metrics policy and the Copilot code review policy. The **Pull requests** section is visible to anyone who can view the page.

For information about enabling these policies, see [Managing policies and features for GitHub Copilot in your organization](/en/copilot/how-tos/administer-copilot/manage-for-organization/manage-policies).

## Accessing Repository insights

<!-- Confirm before publication in a feature-enabled repository: The page heading "Repository insights" and section headings "Pull requests" and "Copilot code review" follow the prototype descriptions. Verify the final headings, stale-data indication, and page-level waiting state. -->

1. On GitHub, navigate to the main page of the repository.
2. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-graph" aria-label="graph" role="img"><path d="M1.5 1.75V13.5h13.75a.75.75 0 0 1 0 1.5H.75a.75.75 0 0 1-.75-.75V1.75a.75.75 0 0 1 1.5 0Zm14.28 2.53-5.25 5.25a.75.75 0 0 1-1.06 0L7 7.06 4.28 9.78a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042l3.25-3.25a.75.75 0 0 1 1.06 0L10 7.94l4.72-4.72a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042Z"></path></svg> Insights**.

   ![Screenshot of the main page of a repository. In the horizontal navigation bar, a tab, labeled with a graph icon and "Insights," is outlined in orange.](/assets/images/help/repository/repo-nav-insights-tab.png)
3. On the **Repository insights** page, review the **Pull requests** section for activity and merge-time context, then the **Copilot code review** section for feedback outcomes.

The weekly reporting period covers seven calendar days ending on the latest fully published day. Check the dates displayed on the page. If the latest data is older than expected, the page will indicate that data is delayed.

If you see "Waiting on your data", allow a few days for data to become available. This state does not mean the repository had no activity. Monthly address-rate trends have a separate reporting period and can have less history.

For metric definitions, reporting limits, and guidance on choosing follow-up actions, see [Repository insights metrics](/en/copilot/reference/copilot-usage-metrics/repository-insights-metrics).