# Configuring default setup for code scanning at scale

You can quickly configure code scanning for repositories across your organization using default setup.

With default setup for code scanning, you can quickly secure code in repositories across your organization. For more information, see [About setup types for code scanning](/en/code-security/concepts/code-scanning/setup-types).

For repositories that are not suitable for default setup, you can configure advanced setup at the repository level, or at the organization level using a script.

## Prerequisites

A repository must meet all the following criteria to be eligible for default setup:

* Advanced setup for code scanning is not already enabled.
* GitHub Actions is enabled.
* It is publicly visible, or GitHub Code Security is enabled.

## Configuring default setup for all eligible repositories in an organization

You can enable default setup for all eligible repositories in your organization. For more information, see [Enabling security features at scale](/en/code-security/securing-your-organization/introduction-to-securing-your-organization-at-scale/about-enabling-security-features-at-scale).

### Extending CodeQL coverage in default setup

Through your organization's security settings page, you can extend coverage in default setup using model packs for all eligible repositories in your organization. For more information, see [Editing your configuration of default setup](/en/code-security/code-scanning/managing-your-code-scanning-configuration/editing-your-configuration-of-default-setup#extending-coverage-for-all-repositories-in-an-organization).

## Configuring default setup for a subset of repositories in an organization

You can filter for specific repositories you would like to configure default setup for. For more information, see [Applying a custom security configuration](/en/code-security/securing-your-organization/enabling-security-features-in-your-organization/applying-a-custom-security-configuration).

## Providing default setup access to private registries

When a repository uses code stored in a private registry, default setup needs access to the registry to work effectively. For more information, see [Giving security features access to private registries](/en/code-security/securing-your-organization/enabling-security-features-in-your-organization/giving-org-access-private-registries).