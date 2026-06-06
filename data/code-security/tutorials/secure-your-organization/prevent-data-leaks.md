# Best practices for preventing data leaks in your organization

Learn guidance and recommendations to help you avoid private or sensitive data present in your organization from being exposed.

## About this guide

As an organization owner, preventing exposure of private or sensitive data should be a top priority. Whether intentional or accidental, data leaks can cause substantial risk to the parties involved. While GitHub takes measures to help protect you against data leaks, you are also responsible for administering your organization to harden security.

There are several key components when it comes to defending against data leaks:

* Taking a proactive approach towards prevention
* Early detection of possible leaks
* Maintaining a mitigation plan when an incident occurs

The best approach will depend on the type of organization you're managing. For example, an organization that focuses on open source development might require looser controls than a fully commercial organization, to allow for external collaboration. This article provide high level guidance on the GitHub features and settings to consider, which you should implement according to your needs.

## Secure accounts

Protect your organization's repositories and settings by implementing security best practices, including enabling 2FA and requiring it for all members, and establishing strong password guidelines.

* Requiring organization members, outside collaborators, and billing managers to enable 2FA for their personal accounts, making it harder for malicious actors to access an organization's repositories and settings. For more information, see [Requiring two-factor authentication in your organization](/en/organizations/keeping-your-organization-secure/managing-two-factor-authentication-for-your-organization/requiring-two-factor-authentication-in-your-organization).

* Encouraging your users to create strong passwords and secure them appropriately, by following GitHub’s recommended password guidelines. For more information, see [Creating a strong password](/en/authentication/keeping-your-account-and-data-secure/creating-a-strong-password).

* Encouraging your users to keep push protection for users enabled in their personal account settings, so that no matter which public repository they push to, they are protected. For more information, see [Managing push protection for users](/en/code-security/secret-scanning/working-with-secret-scanning-and-push-protection/push-protection-for-users).

* Establishing an internal security policy in GitHub, so users know the appropriate steps to take and who to contact if an incident is suspected. For more information, see [Adding a security policy to your repository](/en/code-security/getting-started/adding-a-security-policy-to-your-repository).

For more detailed information about securing accounts, see [Best practices for securing accounts](/en/code-security/supply-chain-security/end-to-end-supply-chain/securing-accounts).

## Prevent data leaks

As an organization owner, you should limit and review access as appropriate for the type of your organization. Consider the following settings for tighter control:

| Recommendation                                                                                                                                                           | More information                                                                                                                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Disable the ability to fork repositories.                                                                                                                                | [Managing the forking policy for your repository](/en/repositories/managing-your-repositorys-settings-and-features/managing-repository-settings/managing-the-forking-policy-for-your-repository) |
| Disable changing repository visibility.                                                                                                                                  | [Restricting repository visibility changes in your organization](/en/organizations/managing-organization-settings/restricting-repository-visibility-changes-in-your-organization)                |
| Restrict repository creation to private or internal.                                                                                                                     | [Restricting repository creation in your organization](/en/organizations/managing-organization-settings/restricting-repository-creation-in-your-organization)                                    |
| Disable repository deletion and transfer.                                                                                                                                | [Setting permissions for deleting or transferring repositories](/en/organizations/managing-organization-settings/setting-permissions-for-deleting-or-transferring-repositories)                  |
|                                                                                                                                                                          |                                                                                                                                                                                                  |
| Scope personal access tokens to the minimum permissions necessary.                                                                                                       | None                                                                                                                                                                                             |
| Secure your code by converting public repositories to private whenever appropriate. You can alert the repository owners of this change automatically using a GitHub App. | [Prevent-Public-Repos](https://github.com/apps/prevent-public-repos) in GitHub Marketplace                                                                                                       |
| Confirm your organization’s identity by verifying your domain and restricting email notifications to only verified email domains.                                        | [Verifying or approving a domain for your organization](/en/organizations/managing-organization-settings/verifying-or-approving-a-domain-for-your-organization)                                  |
| Ensure your organization has upgraded to the GitHub Customer Agreement instead of using the Standard Terms of Service.                                                   | [Upgrading to the GitHub Customer Agreement](/en/organizations/managing-organization-settings/upgrading-to-the-github-customer-agreement)                                                        |
| Prevent contributors from making accidental commits.                                                                                                                     | [Removing sensitive data from a repository](/en/authentication/keeping-your-account-and-data-secure/removing-sensitive-data-from-a-repository#avoiding-accidental-commits-in-the-future)         |

## Detect data leaks

No matter how well you tighten your organization to prevent data leaks, some may still occur, and you can respond by using secret scanning, the audit log, and branch protection rules.

### Use secret scanning

Secret scanning helps secure code and keep secrets safe across organizations and repositories by scanning and detecting secrets that were accidentally committed over the full Git history of every branch in GitHub repositories. Any strings that match patterns provided by secret scanning partners, by other service providers, or defined by you or your organization, are reported as alerts in the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab of repositories.

There are two forms of secret scanning available: **Secret scanning alerts for partners** and **Secret scanning alerts for users**.

* Secret scanning alerts for partners: These are enabled by default and automatically run on all public repositories and public npm packages.
* Secret scanning alerts for users: To get additional scanning capabilities for your organization, you need to enable secret scanning alerts for users.

  When enabled, secret scanning alerts for users can be detected on the following types of repository:

  * Public repositories owned by personal accounts on GitHub.com
  * Public repositories owned by organizations
  * Private and internal repositories owned by organizations using GitHub Team or GitHub Enterprise Cloud, with a license for GitHub Code Security

> \[!TIP]
> Regardless of the enablement status of secret scanning and push protection, organizations on GitHub Team and GitHub Enterprise can run a free report to scan the code in the organization for leaked secrets. See [Secret security with GitHub](/en/code-security/securing-your-organization/understanding-your-organizations-exposure-to-leaked-secrets/about-secret-risk-assessment).

For more information about secret scanning, see [Secret scanning](/en/code-security/secret-scanning/introduction/about-secret-scanning).

You can also enable secret scanning as a push protection for a repository or an organization. When you enable this feature, secret scanning prevents contributors from pushing code with a detected secret. For more information, see [Push protection](/en/code-security/secret-scanning/protecting-pushes-with-secret-scanning). Finally, you can also extend the detection to include custom secret string structures. For more information, see [Defining custom patterns for secret scanning](/en/code-security/secret-scanning/using-advanced-secret-scanning-and-push-protection-features/custom-patterns/defining-custom-patterns-for-secret-scanning).

### Review the audit log for your organization

You can also proactively secure IP and maintain compliance for your organization by leveraging your organization's audit log, along with the GraphQL Audit Log API. For more information, see [Reviewing the audit log for your organization](/en/organizations/keeping-your-organization-secure/managing-security-settings-for-your-organization/reviewing-the-audit-log-for-your-organization) and [Enterprise administration](/en/graphql/reference/enterprise-admin#interface-auditentry).

### Set up branch protection rules

To ensure that all code is properly reviewed prior to being merged into the default branch, you can enable branch protection. By setting branch protection rules, you can enforce certain workflows or requirements before a contributor can push changes. For more information, see [About protected branches](/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches).

As an alternative to branch protection rules, you can create rulesets. Rulesets have a few advantages over branch protection rules, such as statuses, and better discoverability without requiring admin access. You can also apply multiple rulesets at the same time. For more information, see [About rulesets](/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/about-rulesets).

## Mitigate data leaks

If a user pushes sensitive data, ask them to remove it by using the `git filter-repo` tool. For more information, see [Removing sensitive data from a repository](/en/authentication/keeping-your-account-and-data-secure/removing-sensitive-data-from-a-repository). Also, if the sensitive data has not been pushed yet, you can just undo those changes locally; for more information, see [the GitHub Blog](https://github.blog/2015-06-08-how-to-undo-almost-anything-with-git/) (but note that `git revert` is not a valid way to undo the addition of sensitive data as it leaves the original sensitive commit in Git history).

If you're unable to coordinate directly with the repository owner to remove data that you're confident you own, you can fill out a DMCA takedown notice form and tell GitHub Support.  Make sure to include the problematic commit hashes.  For more information, see [DMCA takedown notice](https://support.github.com/contact/dmca-takedown).

> \[!NOTE]
> If one of your repositories has been taken down due to a false claim, you should fill out a DMCA
> counter notice form and alert GitHub Support. For more information, see [DMCA counter notice](https://support.github.com/contact/dmca-counter-notice).

### Revoke exposed tokens

If credentials have been exposed in a GitHub repository, GitHub secret scanning can be used to report and revoke the credentials. For more information, see [Resolving alerts from secret scanning](/en/code-security/secret-scanning/managing-alerts-from-secret-scanning/resolving-alerts#reporting-a-leaked-secret).

You can also revoke exposed credentials that you do not own and have been exposed outside of GitHub repositories. By doing this, you are contributing to the overall security of the GitHub community and can quickly limit the impact of these credentials. The API supports revoking:

* Personal access tokens (classic) with the `ghp_` prefix
* Fine-grained personal access tokens with the `github_pat_` prefix
* OAuth app tokens with the `gho_` prefix
* GitHub App user-to-server tokens with the `ghu_` prefix
* GitHub App refresh tokens with the `ghr_` prefix

If you find any exposed tokens either on GitHub or elsewhere, you can submit a revocation request using the REST API. See [Revocation](/en/rest/credentials/revoke#revoke-a-list-of-credentials) for the complete and authoritative list of supported credential types.

## Next steps

* [Best practices for securing code in your supply chain](/en/code-security/supply-chain-security/end-to-end-supply-chain/securing-code)
* [Best practices for securing your build system](/en/code-security/supply-chain-security/end-to-end-supply-chain/securing-builds)