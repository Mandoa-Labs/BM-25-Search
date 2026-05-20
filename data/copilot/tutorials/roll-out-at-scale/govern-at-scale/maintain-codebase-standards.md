# Maintaining codebase standards in a GitHub Copilot rollout

Stay in control of your enterprise's code with rulesets, security features, and effective training.

Most enterprises are aware of the productivity benefits that AI coding tools can bring. However, many worry that improper usage in their company, such as malicious prompts or developers accepting AI suggestions without review, will lead to their codebase's standards being compromised.

You can mitigate these risks by setting up your GitHub environment and work culture for effective governance. A major benefit of GitHub Copilot is that it is built into the GitHub platform, which already contains a range of features for enterprise-grade code governance.

## 1. Require pull requests and reviews

Developers and bad actors should never be able to unilaterally apply unvetted AI suggestions or agent work directly to sensitive codebases. You should require an **approved pull request** before users can merge code into production codebases and other important branches.

To do this, create a ruleset:

1. Identify organizations or repositories that contain the codebases you want to protect, and **apply a custom property** to them. This will allow you to easily target those resources in a ruleset. See [Managing custom properties for repositories in your organization](/en/organizations/managing-organization-settings/managing-custom-properties-for-repositories-in-your-organization) or [Managing custom properties for organizations](/en/enterprise-cloud@latest/admin/managing-accounts-and-repositories/managing-organizations-in-your-enterprise/managing-custom-properties-for-organizations).

   Alternatively, you can add these protected resources to a ruleset manually, or target them based on a naming convention.

2. Create a branch ruleset for your enterprise. See [Enforcing code governance in your enterprise with rulesets](/en/enterprise-cloud@latest/admin/enforcing-policies/enforcing-policies-for-your-enterprise/enforcing-policies-for-code-governance#creating-a-branch-or-tag-ruleset).

   * Enable at least the **Require a pull request before merging** and **Block force pushes** rules. Under the "Require a pull request" rule, ensure you require at least one approval.
   * Enable other rules if required. For example, if you're concerned about bad actors hijacking pull requests, make sure you **dismiss stale pull request approvals** when new commits are pushed.

3. Encourage repository administrators to set up CODEOWNERS files for specific files in repositories. This will automatically request a review from the code owners when those files are modified.

   Then, you can go back to your ruleset and enable the **Require review from Code Owners** rule.

4. Encourage organization owners and repository administrators to create more specific rulesets, as they're likely to have more awareness of requirements for their own code.

   These rulesets will add to the baseline that you define at the enterprise level, but will never override it.

## 2. Test your code

Good DevOps practices ensure that your code is automatically tested before being merged and deployed, minimizing the risks of errors entering your default branches and surfacing in production environments.

1. Enable GitHub Actions or another CI/CD system.
2. Encourage developers to write tests for all features and integrate tests into GitHub Actions workflows.
3. Encourage organization owners or repository owners to create rulesets and add important workflows to the **Require workflows to pass before merging** rule.

## 3. Scan code for vulnerabilities

Copilot is already designed to avoid introducing vulnerabilities into your codebase. For example, code created by Copilot cloud agent is automatically scanned for vulnerable patterns and secrets such as API keys.

However, it is good practice to regularly scan all code for vulnerabilities and secrets, and to prevent developers from introducing vulnerabilities in the first place.

1. As a starting point, apply and enforce a basic **security configuration** on your organizations. This is a collection of enablement settings for security features. We recommend including code scanning, secret scanning, and secrets push protection. See [Creating a custom security configuration](/en/code-security/how-tos/secure-at-scale/configure-organization-security/establish-complete-coverage/creating-a-custom-security-configuration#creating-a-secret-protection-and-code-security-configuration).
2. As you learn more about your needs, create additional custom configurations or apply granular settings at the repository level.
3. To enforce code scanning on pull requests, go back to your ruleset and enable the **Require code scanning results** rule.

## 4. Create guidelines for Copilot

To improve the quality of Copilot's suggestions in the first place, you should create custom instructions. These instructions add context to all prompts that tells Copilot to follow your company's coding standards.

1. To establish a good baseline, create **custom instructions at the organization level**. These can be high-level standards that are likely to apply to any repository. However, note that these instructions only apply on the GitHub website. See [Adding organization custom instructions for GitHub Copilot](/en/copilot/how-tos/configure-custom-instructions/add-organization-instructions).
2. For more complete coverage, encourage developers and repository administrators to **write custom instructions for specific repositories**. These apply in more places than organization instructions, and can go into more detail about each project and its requirements. See [Adding repository custom instructions for GitHub Copilot](/en/copilot/how-tos/configure-custom-instructions/add-repository-instructions).

## 5. Encourage best practices

With strong guardrails in place, developers should already be enabled to use AI effectively. However, it is important to provide training on AI tools and create a culture where best practices are encouraged, rather than just enforced.

1. Communicate your governance settings and your company's expectations for how developers should use Copilot. For example, if all agent work should be thoroughly reviewed, ensure this process is established and communicated.
2. Create onboarding resources such as internal documentation or videos. For a starting point, share existing resources like [Best practices for using GitHub Copilot](/en/copilot/using-github-copilot/best-practices-for-using-github-copilot) and [GitHub Copilot Cookbook](/en/copilot/copilot-chat-cookbook).
3. Offer ongoing training and support, such as workshops. In successful rollouts, many companies identify "champions" who can train others on how to use Copilot effectively.

## 6. Plan for the worst

Even with the strictest guardrails in place, it is always possible that vulnerable or error-prone code will be merged, regardless of whether your developers are using AI tools.

To prepare for these scenarios, you should plan for how you will address problems and communicate this plan with developers. For example:

1. Revert a bad pull request and roll back a deployment.
2. Create a discussion post analyzing what went wrong and how to avoid it in the future.
3. Check audit logs for things like ruleset bypasses, incorrect permissions, or changes to governance settings.

## 7. Check code quality

If you're confident in your governance model but still concerned that Copilot will reduce the quality of your codebase over time, you can measure this over the course of a rollout. If enabled, GitHub Code Quality provides metrics on the code health of your repositories. See [About GitHub Code Quality](/en/code-security/concepts/about-code-quality).