# Controlling who can execute GitHub Actions workflows

Control who can trigger GitHub Actions workflows and which events are permitted to run them across an enterprise, organization, and repository.

With workflow execution protections, you can define an allowlist that controls who can trigger GitHub Actions workflows and which events are permitted to run them. For more information, see [About Actions policies](/en/actions/concepts/about-actions-policies).

<!-- expires 2026-11-02 -->

> \[!NOTE] GitHub has added a default policy that will block the `pull_request_target` event in public repositories. This policy will be enforced on November 2, 2026. See [Securely using pull\_request\_target](/en/actions/reference/security/securely-using-pull_request_target#default-policy-for-pull_request_target).

<!-- end expires 2026-11-02 -->

## Preparing to add protections

Like rulesets, workflow execution protections layer with other protections in the same repository, organization, or enterprise.

Rather than creating one large policy per account, we recommend creating multiple clearly defined policies and layering protections across account levels. Enterprise owners can create protections at the enterprise level for broad, non-negotiable policies. Organization owners and repository administrators can then add to these restrictions.

For each policy you define, think about:

1. **Which organizations or repositories** your protection will target. For example, open source repositories may need tighter restrictions on who can trigger workflows. You can target repositories by factors like visibility, deployment status, or custom property.

   * Deployment status comes from an organization's linked artifacts page. If this is an important factor, make sure you're uploading deployment records when an artifact is deployed. See [About linked artifacts](/en/code-security/concepts/supply-chain-security/linked-artifacts).
   * To create and assign custom properties, see [Managing custom properties for repositories in your organization](/en/organizations/managing-organization-settings/managing-custom-properties-for-repositories-in-your-organization).

2. **Which workflows** will be protected. For example, workflows that deploy production code might need a certain level of protection, but less sensitive automations may not need the same level of protection. You can scope policies to specific workflow paths or required workflows.

3. **Who should be able to run these workflows** in the repositories you're targeting. This might be users with a certain role, selected bot accounts, or a specific team. Consider grouping these users in an organization or enterprise team so they can be easily contacted and referenced across multiple rulesets. See [Creating an organization team](/en/organizations/organizing-members-into-teams/creating-a-team) or [Creating enterprise teams](/en/enterprise-cloud@latest/admin/managing-accounts-and-repositories/managing-users-in-your-enterprise/create-enterprise-teams).

## Creating a workflow execution policy

First, create a new Actions policy for the account level you're working at.

In a repository or organization:

1. Click the **Settings** tab.
2. In the left sidebar, under **Actions**, click **Policies**.

In an enterprise:

1. Click the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-law" aria-label="law" role="img"><path d="M8.75.75V2h.985c.304 0 .603.08.867.231l1.29.736c.038.022.08.033.124.033h2.234a.75.75 0 0 1 0 1.5h-.427l2.111 4.692a.75.75 0 0 1-.154.838l-.53-.53.529.531-.001.002-.002.002-.006.006-.006.005-.01.01-.045.04c-.21.176-.441.327-.686.45C14.556 10.78 13.88 11 13 11a4.498 4.498 0 0 1-2.023-.454 3.544 3.544 0 0 1-.686-.45l-.045-.04-.016-.015-.006-.006-.004-.004v-.001a.75.75 0 0 1-.154-.838L12.178 4.5h-.162c-.305 0-.604-.079-.868-.231l-1.29-.736a.245.245 0 0 0-.124-.033H8.75V13h2.5a.75.75 0 0 1 0 1.5h-6.5a.75.75 0 0 1 0-1.5h2.5V3.5h-.984a.245.245 0 0 0-.124.033l-1.289.737c-.265.15-.564.23-.869.23h-.162l2.112 4.692a.75.75 0 0 1-.154.838l-.53-.53.529.531-.001.002-.002.002-.006.006-.016.015-.045.04c-.21.176-.441.327-.686.45C4.556 10.78 3.88 11 3 11a4.498 4.498 0 0 1-2.023-.454 3.544 3.544 0 0 1-.686-.45l-.045-.04-.016-.015-.006-.006-.004-.004v-.001a.75.75 0 0 1-.154-.838L2.178 4.5H1.75a.75.75 0 0 1 0-1.5h2.234a.249.249 0 0 0 .125-.033l1.288-.737c.265-.15.564-.23.869-.23h.984V.75a.75.75 0 0 1 1.5 0Zm2.945 8.477c.285.135.718.273 1.305.273s1.02-.138 1.305-.273L13 6.327Zm-10 0c.285.135.718.273 1.305.273s1.02-.138 1.305-.273L3 6.327Z"></path></svg> Policies** tab.
2. In the left sidebar, click **Actions**, then **Policies**.

> \[!TIP] To manage policies programmatically, see [REST API endpoints for GitHub Actions policies](/en/rest/actions/policies).

### Configuring the policy

Next, create a new policy.

1. Choose a name for the policy.
2. Choose an enforcement status. If you select **Evaluate** (GitHub Enterprise Cloud only), you will be able to monitor when users would hit the restriction in policy insights.
3. Target your desired workflows, organizations, or repositories.
4. Configure the following workflow execution protections.

### Restrict actors

By default, every user with write access to a repository can trigger workflows. Actor rules let you separate who contributes code from who runs your CI, so you can grant a contributor write access without granting them the ability to execute workflows.

Only the allowed actors will be able to run the specified workflows in the targeted repository. If you also restrict events, these users will only be able to trigger workflows with the allowed events. Non-allowed actors will not be able to run the specified workflows at all.

GitHub features are exempt from these restrictions for the built-in processes that they run on GitHub Actions. However, if you have created workflows that need to be run by the identity associated with a GitHub feature, such as `dependabot[bot]`, then this identity must be added as an allowed actor.

### Restrict events

Event rules control which events are permitted, such as `push`, `pull_request`, `pull_request_target`, and `workflow_dispatch`.

## Evaluating policies

You can view policy insights to see workflow runs that have been blocked (for active policies) or would have been blocked (for "evaluate" policies). This is a good way to check that policies are working as intended and not causing unnecessary friction.

To view insights, click the **Policy insights** page. You'll find this directly under the page for GitHub Actions policies in your repository, organization, or enterprise sidebar.