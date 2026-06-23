# About the backup service for GitHub Enterprise Server

Learn what the built-in backup service offers and how it differs from a High Availability replica.

## About the GitHub Enterprise Server Backup Service

The GitHub Enterprise Server Backup Service is a managed backup solution built directly into GitHub Enterprise Server. It offers a simplified alternative to the legacy GitHub Enterprise Server Backup Utilities.

With this service, you can:

* Configure scheduled backups from the Management Console.
* View backup status and history.

Compared to the legacy backup utilities, the GitHub Enterprise Server Backup Service:

* Can be configured through the Management Console.
* Doesn’t require a separate host for backup software.
* Stores backups on a dedicated storage volume directly accessible by your instance.

## How does the backup service differ from a High Availability replica?

While both the backup service and a High Availability (HA) replica contribute to data protection, they serve different purposes and are recommended together for a robust deployment.

### High Availability replica

An HA replica is a redundant, passive GitHub Enterprise Server instance that stays in sync with the primary instance via datastore replication. It minimizes service disruption during hardware failure or network outages.

However, it’s not a replacement for backups—because any data corruption or loss on the primary can be immediately replicated to the HA node.

### GitHub Enterprise Server Backup Service

The backup service is a disaster recovery solution. It captures full, timestamped snapshots of instance data that can be used to restore an instance or spin up a new one—without needing an always-on replica.

## Further reading

* [Understanding the backup service](/en/enterprise-server@3.21/admin/backing-up-and-restoring-your-instance/understanding-the-backup-service)
* [Configuring the backup service](/en/enterprise-server@3.21/admin/backing-up-and-restoring-your-instance/configuring-the-backup-service)
* [Restoring from a backup](/en/enterprise-server@3.21/admin/backing-up-and-restoring-your-instance/restoring-from-a-backup)
* [Restoring with GitHub Actions enabled](/en/enterprise-server@3.21/admin/backing-up-and-restoring-your-instance/restoring-with-github-actions-enabled)