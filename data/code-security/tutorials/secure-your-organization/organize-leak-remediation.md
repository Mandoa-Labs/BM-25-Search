# Organizing remediation efforts for leaked secrets

Systematically organize and manage the remediation of leaked secrets using security campaigns and alert assignments.

## Introduction

In this tutorial, you'll organize remediation efforts for leaked secrets. You'll learn how to:

* Create security campaigns to track remediation work
* Assign alerts based on ownership
* Monitor remediation progress
* Communicate with stakeholders

## Prerequisites

* You must have both GitHub Secret Protection and secret scanning enabled for your organization. See [Pricing and enabling GitHub Secret Protection](/en/code-security/securing-your-organization/understanding-your-organizations-exposure-to-leaked-secrets/protect-your-secrets).
* You must have existing secret scanning alerts available.

## Step 1: Review your secret scanning alerts

Before taking action, you need to understand the current state of your organization's security alerts.

1. On GitHub, navigate to the main page of the organization.

2. Under your organization name, click the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab.

3. In the left sidebar, under "Findings", click the <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-chevron-down" aria-label="chevron-down" role="img"><path d="M12.78 5.22a.749.749 0 0 1 0 1.06l-4.25 4.25a.749.749 0 0 1-1.06 0L3.22 6.28a.749.749 0 1 1 1.06-1.06L8 8.939l3.72-3.719a.749.749 0 0 1 1.06 0Z"></path></svg> symbol to the right of **Secret scanning**.

4. In the dropdown list, select `Default`. `Default` relates to supported patterns and specified custom patterns.

5. Alternatively, you can select `Generic` to review unstructured secrets like passwords. However, generic patterns typically produce more false positives than default patterns, so consider reviewing these alerts after addressing higher-priority leaks.

6. Review the total number of open alerts and repositories affected.

7. Use filters to identify the most urgent alerts and prioritize your remediation efforts.
   * To show leaks in **public** repositories, use `publicly-leaked`.
   * To show secret leaks found in **more than one repository** within the same organization or enterprise, use `is:multi-repository`.
   * To show secrets that are still **valid**, use `validity:active`.
   * To filter by specific **service** credentials (AWS, Azure, GitHub), use `provider:`.
   * To filter by specific **token types**, use `secret-type:`.

8. Optionally, in the sidebar under "Insights," click **Secret scanning** to see:
   * Secret types that have been blocked or bypassed most frequently
   * Repositories with the most blocked pushes or bypasses

## Step 2: Create a security campaign

You can set up a security campaign to organize and track your remediation work across repositories.

1. Navigate to your organization and click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality**.
2. On the left panel, select **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-goal" aria-label="goal" role="img"><path d="M13.637 2.363h-.001l1.676.335c.09.018.164.084.19.173a.25.25 0 0 1-.062.249l-1.373 1.374a.876.876 0 0 1-.619.256H12.31L9.45 7.611A1.5 1.5 0 1 1 6.5 8a1.501 1.501 0 0 1 1.889-1.449l2.861-2.862V2.552c0-.232.092-.455.256-.619L12.88.559a.25.25 0 0 1 .249-.062c.089.026.155.1.173.19Z"></path><path d="M2 8a6 6 0 1 0 11.769-1.656.751.751 0 1 1 1.442-.413 7.502 7.502 0 0 1-12.513 7.371A7.501 7.501 0 0 1 10.069.789a.75.75 0 0 1-.413 1.442A6.001 6.001 0 0 0 2 8Z"></path><path d="M5 8a3.002 3.002 0 0 0 4.699 2.476 3 3 0 0 0 1.28-2.827.748.748 0 0 1 1.045-.782.75.75 0 0 1 .445.61A4.5 4.5 0 1 1 8.516 3.53a.75.75 0 1 1-.17 1.49A3 3 0 0 0 5 8Z"></path></svg> Campaigns**.
3. Click **Create campaign <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-triangle-down" aria-label="triangle down icon" role="img"><path d="m4.427 7.427 3.396 3.396a.25.25 0 0 0 .354 0l3.396-3.396A.25.25 0 0 0 11.396 7H4.604a.25.25 0 0 0-.177.427Z"></path></svg>**, then either:
   * Select a pre-defined Secrets campaign template.
   * Use custom filters to target specific alerts (for example, `is:open provider:azure` or `is:open validity:active`).
4. Review the alerts (maximum 1000) and adjust filters if needed.
5. Click **Save as** and choose **Publish campaign**.
6. Fill out your campaign information, then click **Publish campaign**.

## Step 3: Assign alerts to team members

After creating your campaign, you'll want to assign individual alerts to the developers responsible for fixing them.

1. On your campaign page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-chevron-right" aria-label="Toggle to expand or collapse the repository view" role="img"><path d="M6.22 3.22a.75.75 0 0 1 1.06 0l4.25 4.25a.75.75 0 0 1 0 1.06l-4.25 4.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042L9.94 8 6.22 4.28a.75.75 0 0 1 0-1.06Z"></path></svg> to expand a repository and view its alerts.
2. Click an alert to open its details page.
3. In the right sidebar, click **Assignees**.
4. Select a developer you want to fix the alert. Typically, this is the person who committed the secret or the repository administrator where the leak is detected. They must have write access.

## Step 4: Monitor remediation progress

Once alerts are assigned, you need to regularly track your campaign's progress to ensure timely completion.

1. On your campaign page, review the campaign summary. You'll see:
   * **Campaign progress**: How many alerts are closed (fixed or dismissed) or still left to review
   * **Status**: How many days until the campaign's due date
2. You can explore campaign details:
   * Expand any repository to see its progress in alert remediation.
   * Set **Group by** to **None** to show a list of all alerts.
   * Use filters to focus on specific repositories or alerts.
3. Identify areas needing attention based on repositories with the most open alerts or no recent progress, then reach out to support those repository maintainers or assignees.

## Step 5: Communicate with stakeholders

Throughout the remediation process, you should keep stakeholders informed with regular progress updates. You can use information from your campaign dashboard to help you generate these updates.

1. Navigate to the campaign dashboard.
2. Identify the information you want to include in your reports. Consider these key metrics:
   * Alerts resolved this week
   * Remaining open alerts
   * On-track vs. at-risk items
   * Notable achievements or blockers
3. Incorporate the metrics into your update, then distribute via email, Slack, Teams, or security meetings.

## Step 6: Document remediation procedures

Finally, you should create standardized procedures to make future remediation efforts more efficient.

1. Develop secret-type-specific guides. For example:
   * **AWS credentials**: How to rotate access keys and update services
   * **GitHub tokens**: How to revoke and regenerate Personal Access Tokens
   * **API keys**: Service-specific rotation procedures
   * **Database credentials**: Safe rotation without service disruption
2. Create a remediation checklist.
   1. Verify the secret is actually leaked.
   2. Determine if the secret is still active.
   3. Revoke or rotate the compromised secret.
   4. Update all systems using the old secret.
   5. Test that systems function with new credentials.
   6. Document the incident and remediation steps.
   7. Mark the alert as resolved.
3. Establish escalation paths.
   * Define when to escalate to security leadership.
   * Identify subject matter experts for different secret types.
   * Create incident response procedures for critical leaks.