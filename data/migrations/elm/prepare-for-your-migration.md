# Preparing for your live migration from GitHub Enterprise Server to GHE.com

Key questions to consider before getting started with Enterprise Live Migrations.

> \[!NOTE] Enterprise Live Migrations is in public preview and subject to change.

## Is our GitHub Enterprise Server instance ready?

<!-- expires 2026-05-12 -->

<!-- when the 3.21 RC is released, update this to indicate it's also available in all major releases from 3.21 -->

<!-- And update the min versions and wording in this reusable to indicate the minimum required versions to follow these instructions -->

ELM has been backported to supported releases. To use it, you must upgrade to one of the following minor versions or later:

* `3.20.2`
* `3.19.6`
* `3.18.9`
* `3.17.15`

<!-- end expires 2026-05-12 -->

Your GitHub Enterprise Server instance must also:

* Use an **HTTPS** URL. HTTP URLs are not supported.
* Have migrations enabled and blob storage configured. You can check these settings in the "Migrations" section of the Management Console. If you don't already have these settings configured, we will explain how to set them to default values in [Migrating your repository with Enterprise Live Migrations](/en/migrations/elm/migrate-your-repository).

## What will our destination organization look like?

You can migrate repositories to a new or existing organization on GHE.com. ELM creates the target organization if it doesn't already exist.

A platform migration is a good opportunity to reconsider your organization and team structure. See [Best practices for organizing work in your enterprise](/en/enterprise-cloud@latest/admin/concepts/enterprise-best-practices/organize-work).

## Which repositories will we migrate?

ELM supports up to **10** concurrent repository migrations from a single GitHub Enterprise Server instance, and **20** concurrent migrations per destination enterprise.

Plan which repositories you will migrate with ELM first, and which you can migrate later or using a different migration tool. Repositories that are most likely to benefit from ELM are:

* Important repositories where long periods of downtime would disrupt your business
* Large monorepos that are too big for other migration tools

Public repositories are not available on GHE.com, and these will be rejected by ELM. You can change the visibility of these repositories on GitHub Enterprise Server before you start.

You should check that the repositories you choose don't contain release assets that are over 2GB, as this is the limit for ELM.

## Who will run the migration?

The person who runs an ELM migration must:

* Have site admin access to the GitHub Enterprise Server instance
* Be an enterprise owner on the GHE.com enterprise

This person will need to perform the following tasks:

* Before the migration, create personal access tokens (classic) on both the source and destination enterprise.
* During the migration, monitor the migration status and respond to issues.

For concurrent ELM migrations from a GitHub Enterprise Server instance, the same person must run all the `elm` commands, using the same tokens.

After the migration, someone will need to perform some follow-up tasks on GHE.com. Any organization owner can do this.

## What should my developers know?

Before you start, communicate with developers that:

* The repository is moving to a new location. Users can continue to use the source repository during the migration until the operator begins the final cutover to the new location.
* While the migration is in progress, developers should avoid force pushes to the repository, because these will disrupt the Git history in a way that ELM cannot resolve.
* Certain actions that developers perform during the migration process may not be reflected in the migrated repository. For details, see the unsupported actions in [Migrated data for live migrations from GitHub Enterprise Server to GHE.com](/en/migrations/elm/migrated-data-reference#events-included-in-live-updates).

## Next steps

When you're ready to run a migration, see [Migrating your repository with Enterprise Live Migrations](/en/migrations/elm/migrate-your-repository).