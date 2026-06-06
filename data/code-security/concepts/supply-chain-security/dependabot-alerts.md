# Dependabot alerts

Dependabot alerts help you find and fix vulnerable dependencies before they become security risks.

Software often relies on packages from various sources, creating dependency relationships that can unknowingly introduce security vulnerabilities. When your code depends on packages with known security vulnerabilities, you become a target for attackers seeking to exploit your system—potentially gaining access to your code, data, customers, or contributors. Dependabot alerts notify you about vulnerable dependencies so you can upgrade to secure versions and protect your project.

## When Dependabot sends alerts

Dependabot scans your repository's default branch and sends alerts when:

* A new vulnerability is added to the GitHub Advisory Database
* Your dependency graph changes—for example, when you push commits that update packages or versions

For supported ecosystems, see [Dependency graph supported package ecosystems](/en/code-security/supply-chain-security/understanding-your-software-supply-chain/dependency-graph-supported-package-ecosystems#supported-package-ecosystems).

## Understanding alerts

When GitHub detects a vulnerable dependency, a Dependabot alert appears on the repository's **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab and dependency graph. Each alert includes:

* A link to the affected file
* Details about the vulnerability and its severity
* Information about a fixed version (when available)

For information about viewing and managing alerts, see [Viewing and updating Dependabot alerts](/en/code-security/dependabot/dependabot-alerts/viewing-and-updating-dependabot-alerts).

## Who can enable alerts?

Repository administrators and organization owners can enable Dependabot alerts for their repositories and organizations. When enabled, GitHub immediately generates the dependency graph and creates alerts for any vulnerable dependencies it identifies.  Repository administrators can grant access to additional people or teams.

See [Configuring Dependabot alerts](/en/code-security/dependabot/dependabot-alerts/configuring-dependabot-alerts).

## Alert ownership and assignments

Users with write access or higher can assign Dependabot alerts to repository collaborators, teams, or AI agents to establish clear ownership for vulnerability remediation. Assignments help track who's responsible for each alert and prevent vulnerabilities from being overlooked.

You can assign alerts to the following types of agents:

* **Copilot**, GitHub's built-in AI agent.
* **Third-party agents**,such as Codex or Claude, when enabled in your repository settings.

When an alert is assigned to a person or team, the assignee receives a notification and the alert displays their name in the alert list. You can filter alerts by assignee to track progress.

When an alert is assigned to an agent, the agent automatically creates a session and opens a draft pull request with a proposed fix. If the agent can't generate a fix, it remains as an assignee, and you can click **View Session** on the alert timeline to review the agent's log.

> \[!NOTE]
> Assignment visibility is currently scoped to the repository-level alerts view. The organization-wide security overview does not display alert assignments.

When an alert's assignees change, GitHub sends an `assignees_changed` webhook event. You can use this event to trigger workflows or sync assignment data with external systems. For more information, see [Webhook events and payloads](/en/webhooks/webhook-events-and-payloads#dependabot_alert).

### Automation and integrations

You can manage alert assignments programmatically using the REST API. For more information, see [REST API endpoints for Dependabot alerts](/en/rest/dependabot/alerts).

For information about assigning alerts, see [Viewing and updating Dependabot alerts](/en/code-security/how-tos/manage-security-alerts/manage-dependabot-alerts/viewing-and-updating-dependabot-alerts#viewing-and-prioritizing-dependabot-alerts).

## How alert notifications work

By default, GitHub sends email notifications about new alerts to people who both:

* Have write, maintain, or admin permissions to a repository
* Are watching the repository and have enabled notifications for security alerts or for all activity on the repository

You can override the default behavior by choosing the type of notifications you want to receive, or switching notifications off altogether in the settings page for your user notifications at <https://github.com/settings/notifications>.

Regardless of your notification preferences, when Dependabot is first enabled, GitHub does not send notifications for all vulnerable dependencies found in your repository. Instead, you will receive notifications for new vulnerable dependencies identified after Dependabot is enabled, if your notification preferences allow it.

If you are concerned about receiving too many notifications, we recommend leveraging Dependabot auto-triage rules to auto-dismiss low-risk alerts. Rules are applied before alert notifications are sent, so alerts that are auto-dismissed upon creation do not send notifications. See [Dependabot auto-triage rules](/en/code-security/dependabot/dependabot-auto-triage-rules/about-dependabot-auto-triage-rules).

Alternatively, you can opt into the weekly email digest, or even completely turn off notifications while keeping Dependabot alerts enabled.

## Limitations

Dependabot alerts have some limitations:

* Alerts can't catch every security issue. Always review your dependencies and keep manifest and lock files up to date for accurate detection.
* New vulnerabilities may take time to appear in the GitHub Advisory Database and trigger alerts.
* Only advisories reviewed by GitHub trigger alerts.
* Dependabot doesn't scan archived repositories.
* For GitHub Actions, alerts are only generated for actions that use semantic versioning, not SHA versioning.

GitHub never publicly discloses vulnerabilities for any repository.

## Further reading

* [Dependabot malware alerts](/en/code-security/concepts/supply-chain-security/dependabot-malware-alerts)
* [Viewing and updating Dependabot alerts](/en/code-security/dependabot/dependabot-alerts/viewing-and-updating-dependabot-alerts)
* [Dependabot security updates](/en/code-security/dependabot/dependabot-security-updates/about-dependabot-security-updates)
* [Auditing security alerts](/en/code-security/getting-started/auditing-security-alerts)