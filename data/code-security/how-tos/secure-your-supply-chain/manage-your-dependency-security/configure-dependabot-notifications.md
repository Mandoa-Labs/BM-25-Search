# Configuring notifications for Dependabot alerts

Optimize how you receive notifications about Dependabot alerts.

By default, GitHub sends notifications about new alerts by email to people with write, maintain, or admin permissions to a repository. See [Dependabot alerts](/en/code-security/concepts/supply-chain-security/about-dependabot-alerts#notifications-for-alerts).

## Configuring notifications for Dependabot alerts

You can configure notification settings for yourself or your organization from the Manage notifications drop-down <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-bell" aria-label="The notifications bell" role="img"><path d="M8 16a2 2 0 0 0 1.985-1.75c.017-.137-.097-.25-.235-.25h-3.5c-.138 0-.252.113-.235.25A2 2 0 0 0 8 16ZM3 5a5 5 0 0 1 10 0v2.947c0 .05.015.098.042.139l1.703 2.555A1.519 1.519 0 0 1 13.482 13H2.518a1.516 1.516 0 0 1-1.263-2.36l1.703-2.554A.255.255 0 0 0 3 7.947Zm5-3.5A3.5 3.5 0 0 0 4.5 5v2.947c0 .346-.102.683-.294.97l-1.703 2.556a.017.017 0 0 0-.003.01l.001.006c0 .002.002.004.004.006l.006.004.007.001h10.964l.007-.001.006-.004.004-.006.001-.007a.017.017 0 0 0-.003-.01l-1.703-2.554a1.745 1.745 0 0 1-.294-.97V5A3.5 3.5 0 0 0 8 1.5Z"></path></svg> shown at the top of each page. For more information, see [Configuring notifications](/en/account-and-profile/managing-subscriptions-and-notifications-on-github/setting-up-notifications/configuring-notifications#choosing-your-notification-settings).

You can choose to receive notifications:

* In your inbox, as web notifications. A web notification is sent when Dependabot is enabled for a repository, when a new manifest file is committed to the repository, and when a new vulnerability with a critical or high severity is found (**On GitHub** option).
* By email. An email is sent when Dependabot is enabled for a repository, when a new manifest file is committed to the repository, and when a new vulnerability with a critical or high severity is found (**Email** option).
* On the command line. Warnings are displayed as callbacks when you push to repositories with any insecure dependencies (**CLI** option).
* On GitHub Mobile, as web notifications. For more information, see [Configuring notifications](/en/account-and-profile/managing-subscriptions-and-notifications-on-github/setting-up-notifications/configuring-notifications#enabling-push-notifications-with-github-mobile).

> \[!NOTE]
> The email and web/GitHub Mobile notifications are:
>
> * *Per repository* when Dependabot is enabled on the repository, or when a new manifest file is committed to the repository.
> * *Per organization* when a new vulnerability is discovered.
> * Sent when a new vulnerability is discovered. GitHub doesn't send notifications when vulnerabilities are updated.

You can customize the way you are notified about Dependabot alerts. For example, you can receive a daily or weekly digest email summarizing alerts for up to 10 of your repositories using the **Email weekly digest** option.

![Screenshot of the notification options for Dependabot alerts. A dropdown menu with frequency options is outlined in orange.](/assets/images/help/dependabot/dependabot-notification-frequency.png)

> \[!NOTE]
> You can filter your notifications on GitHub to show Dependabot alerts. For more information, see [Managing notifications from your inbox](/en/account-and-profile/managing-subscriptions-and-notifications-on-github/viewing-and-triaging-notifications/managing-notifications-from-your-inbox#dependabot-custom-filters).

Email notifications for Dependabot alerts that affect one or more repositories include the `X-GitHub-Severity` header field. You can use the value of the `X-GitHub-Severity` header field to filter email notifications for Dependabot alerts. For more information, see [Configuring notifications](/en/account-and-profile/managing-subscriptions-and-notifications-on-github/setting-up-notifications/configuring-notifications#filtering-email-notifications).

## Further reading

* [Configuring notifications](/en/account-and-profile/managing-subscriptions-and-notifications-on-github/setting-up-notifications/configuring-notifications)
* [Managing notifications from your inbox](/en/account-and-profile/managing-subscriptions-and-notifications-on-github/viewing-and-triaging-notifications/managing-notifications-from-your-inbox#supported-is-queries)