# Integration with code scanning

You can perform code scanning externally and then display the results in GitHub, or configure webhooks that listen to code scanning activity in your repository.

## About integration with code scanning

As an alternative to running code scanning within GitHub, you can perform analysis elsewhere, using the CodeQL CLI or another static analysis tool, and then upload the results. For more information, see [Using code scanning with your existing CI system](/en/code-security/code-scanning/integrating-with-code-scanning/using-code-scanning-with-your-existing-ci-system).

If you run code scanning using multiple configurations, an alert will sometimes have multiple analysis origins. If an alert has multiple analysis origins, you can view the status of the alert for each analysis origin on the alert page. For more information, see [Code scanning alerts](/en/code-security/code-scanning/managing-code-scanning-alerts/about-code-scanning-alerts#about-analysis-origins).

## Integrations with webhooks

You can use code scanning webhooks to build or configure integrations, such as [GitHub Apps](/en/apps/creating-github-apps/setting-up-a-github-app) or [OAuth apps](/en/apps/oauth-apps/building-oauth-apps), that subscribe to code scanning events in your repository. For example, you could build an integration that creates an issue on GitHub or sends you a Slack notification when a new code scanning alert is added in your repository. For more information, see [Webhooks documentation](/en/webhooks) and [Webhook events and payloads](/en/webhooks-and-events/webhooks/webhook-events-and-payloads#code_scanning_alert).

## Further reading

* [Code scanning](/en/code-security/code-scanning/introduction-to-code-scanning/about-code-scanning)
* [Using code scanning with your existing CI system](/en/code-security/code-scanning/integrating-with-code-scanning/using-code-scanning-with-your-existing-ci-system)
* [SARIF support for code scanning](/en/code-security/code-scanning/integrating-with-code-scanning/sarif-support-for-code-scanning)