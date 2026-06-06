# Secret scanning

Prevent fraudulent use of your secrets by automatically detecting exposed credentials before they can be exploited.

When credentials like API keys and passwords are committed to repositories as hardcoded secrets, they become targets for unauthorized access. Secret scanning automatically detects credential leaks so you can secure them before they're exploited.

> \[!TIP]
> At any time, you can run a free assessment of your organization's code for leaked secrets.
>
> To generate a report, open the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab for your organization, display the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-key" aria-label="key" role="img"><path d="M10.5 0a5.499 5.499 0 1 1-1.288 10.848l-.932.932a.749.749 0 0 1-.53.22H7v.75a.749.749 0 0 1-.22.53l-.5.5a.749.749 0 0 1-.53.22H5v.75a.749.749 0 0 1-.22.53l-.5.5a.749.749 0 0 1-.53.22h-2A1.75 1.75 0 0 1 0 14.25v-2c0-.199.079-.389.22-.53l4.932-4.932A5.5 5.5 0 0 1 10.5 0Zm-4 5.5c-.001.431.069.86.205 1.269a.75.75 0 0 1-.181.768L1.5 12.56v1.69c0 .138.112.25.25.25h1.69l.06-.06v-1.19a.75.75 0 0 1 .75-.75h1.19l.06-.06v-1.19a.75.75 0 0 1 .75-.75h1.19l1.023-1.025a.75.75 0 0 1 .768-.18A4 4 0 1 0 6.5 5.5ZM11 6a1 1 0 1 1 0-2 1 1 0 0 1 0 2Z"></path></svg> Assessments** page, then click **Scan your organization**.

## How secret scanning protects your code

Secret scanning scans your entire Git history on all branches of your repository for hardcoded credentials, including API keys, passwords, tokens, and other known secret types. This helps you identify secret sprawl, the uncontrolled proliferation of credentials across repositories, before it becomes a security risk. GitHub also periodically rescans repositories when new secret types are added.

GitHub also automatically scans:

* Descriptions and comments in issues
* Titles, descriptions, and comments, in open and closed *historical* issues
* Titles, descriptions, and comments in pull requests
* Titles, descriptions, and comments in GitHub Discussions
* Wikis
* Secret gists

### Secret scanning alerts and remediation

When secret scanning detects a credential leak, GitHub generates an alert on your repository's **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab with details about the exposed credential.

When you receive an alert, rotate the affected credential immediately to prevent unauthorized access. While you can also remove secrets from your Git history, this is time-intensive and often unnecessary if you've already revoked the credential.

### Partner integration

GitHub partners with a large variety of service providers to validate detected secrets. When a partner secret is detected, we notify the provider so they can take action, such as revoking the credential. Partner secrets are reported directly to the provider and aren't displayed in your repository alerts. For more information, see [Secret scanning partner program](/en/code-security/secret-scanning/secret-scanning-partnership-program/secret-scanning-partner-program).

## Customizability

Beyond the default detection of partner and provider secrets, you can expand and customize secret scanning to fit your needs.

* **Non-provider patterns.** Expand detection to secrets that aren't tied to a specific service provider, such as private keys, connection strings, and generic API keys.

* **Custom patterns.** Define your own regular expressions to detect organization-specific secrets that aren't covered by default patterns.

* **Validity checks.** Prioritize remediation by checking whether detected secrets are still active.

* **Copilot secret scanning.** Use AI to detect unstructured secrets like passwords, or to generate regular expressions for custom patterns.

### About validity checks

Validity checks help you prioritize which secrets to remediate first by verifying whether a detected secret is still active. When you enable validity checks, secret scanning may contact the secret's issuing service to determine if the credential has been revoked.

Validity checks are separate from secret scanning's partner program. While partner secrets are automatically reported to service providers for revocation, validity checks verify the status of secrets you manage in your own alerts. For more information, see [Validity checks](/en/code-security/concepts/secret-security/about-validity-checks).

## How can I access this feature?

Secret scanning is available for the following repository types:

* **Public repositories**: Secret scanning runs automatically for free.
* **Organization-owned private and internal repositories**: Available with [GitHub Secret Protection](/en/get-started/learning-about-github/about-github-advanced-security) enabled on GitHub Team or GitHub Enterprise Cloud.
* **User-owned repositories**: Available on GitHub Enterprise Cloud with Enterprise Managed Users. Available on GitHub Enterprise Server when the enterprise has [GitHub Secret Protection](/en/get-started/learning-about-github/about-github-advanced-security) enabled.