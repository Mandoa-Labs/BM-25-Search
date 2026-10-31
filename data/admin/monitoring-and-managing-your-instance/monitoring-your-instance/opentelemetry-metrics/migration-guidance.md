# Migrating from collectd to OpenTelemetry

This guide describes the migration of a GitHub Enterprise Server instance from collectd to the OpenTelemetry metrics stack.

GitHub Enterprise Server is transitioning from the collectd metrics stack to OpenTelemetry. Collectd is retired in version 3.23, and upgrading to 3.23 disables it.

## Migration timeline

| Version        | Default for new installations | Default for instances upgraded from earlier releases | Notes                                                            |
| :------------- | :---------------------------- | :--------------------------------------------------- | :--------------------------------------------------------------- |
| 3.18           | Collectd                      | Collectd                                             | OpenTelemetry is opt-in.                                         |
| 3.19 to 3.22   | OpenTelemetry                 | Collectd                                             | Migration to OpenTelemetry is possible before upgrading to 3.23. |
| 3.23 and later | OpenTelemetry                 | OpenTelemetry                                        | Collectd is retired and cannot be used. The upgrade disables it. |

## Preparing to migrate

Before you migrate, complete the following preparations:

* Test the migration on a staging instance before applying it in production.
* Identify the monitoring integrations that depend on collectd metrics, such as external dashboards and alerts.
* If you plan to run both metrics stacks during a transition period, review the caveats in [Running both metrics stacks](#running-both-metrics-stacks).

## Migrating to OpenTelemetry

You can migrate to OpenTelemetry on instances running version 3.19 to 3.22. On version 3.18, OpenTelemetry is opt-in, so you can also enable it there. We recommend migrating before you upgrade to 3.23, so that you can verify your monitoring setup while you can still use collectd.

If you don't migrate, upgrading to version 3.23 or later does it for you: collectd is disabled and cannot be re-enabled, and OpenTelemetry metrics are enabled and become the only metrics stack.

Migration requires enabling OpenTelemetry metrics and disabling collectd. Both settings are available through the Management Console or the command line.

### Using the Management Console

1. From an administrative account on GitHub Enterprise Server, in the upper-right corner of any page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="Site admin" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg>.

2. If you're not already on the "Site admin" page, in the upper-left corner, click **Site admin**.

3. In the "<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="rocket" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Site admin" sidebar, click **Management Console**.

4. In the monitoring settings, select **Enable OpenTelemetry**.

5. Under **Metrics - Collectd**, select **Disable collectd metrics**.

6. Under the "Settings" sidebar, click **Save settings**.

   > [!NOTE]
   > Saving settings in the Management Console restarts system services, which could result in user-visible downtime.

7. Wait for the configuration run to complete.

### Using the command line

1. SSH into your GitHub Enterprise Server instance. If your instance comprises multiple nodes, for example if high availability or geo-replication are configured, SSH into the primary node. If you use a cluster, you can SSH into any node. Replace HOSTNAME with the hostname for your instance, or the hostname or IP address of a node. For more information, see [Accessing the administrative shell (SSH)](/en/enterprise-server@3.22/admin/administering-your-instance/administering-your-instance-from-the-command-line/accessing-the-administrative-shell-ssh).

   ```shell copy
   ssh -p 122 admin@HOSTNAME
   ```

2. To enable OpenTelemetry metrics and disable collectd, run the following commands.

   ```shell
   ghe-config observability.metrics.next-enabled true
   ghe-config observability.metrics.legacy-disabled true
   ```

3. To apply the configuration, run the following command.

   > [!NOTE]
   > During a configuration run, services on your GitHub Enterprise Server instance may restart, which can cause brief downtime for users.

   ```shell copy
   ghe-config-apply
   ```

4. Wait for the configuration run to complete.

### Running both metrics stacks

On version 3.18 to 3.22, running the collectd and OpenTelemetry stacks at the same time is possible but **not recommended**. This configuration has the following caveats:

* Some metric names may differ to remain compatible with the collectd format.
* Some OpenTelemetry metrics do not include labels.
* Increased resource utilization to deliver metrics to both solutions.

Collectd is retired in version 3.23, so running both stacks is not possible after upgrading.

## Post-upgrade checks

After the configuration run completes, whether you migrated manually or upgraded to version 3.23 or later:

* Verify that the metrics are visible and collected in the **Monitoring** tab of the Management Console.
* Update monitoring integrations that depend on collectd metrics. For information about connecting external tools, see [Setting up external monitoring with OpenTelemetry](/en/enterprise-server@3.22/admin/monitoring-and-managing-your-instance/monitoring-your-instance/opentelemetry-metrics/setting-up-external-monitoring-with-opentelemetry).
* For information about analyzing metrics, see [Using Grafana to analyze OpenTelemetry metrics](/en/enterprise-server@3.22/admin/monitoring-and-managing-your-instance/monitoring-your-instance/opentelemetry-metrics/using-grafana-to-analyze-opentelemetry-metrics).

### Viewing historical collectd data

Since patches 3.22.3, 3.21.8, 3.20.10, and 3.19.14, the **Monitoring** tab includes collectd dashboards for viewing historical data. These dashboards display collectd metrics recorded up to the time the collectd stack was disabled.