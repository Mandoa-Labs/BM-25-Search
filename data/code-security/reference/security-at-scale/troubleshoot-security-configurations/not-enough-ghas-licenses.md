# Not enough GitHub Advanced Security licenses

If you are on a subscription-based billing model for GHAS, you need available GHAS licenses to enable GHAS features on a private repository.

If you are on a volume / subscription-based billing model for GitHub Advanced Security (GHAS), you must have an available GHAS license for any additional unique active committers to enable GHAS features on a private repository. To learn about GHAS licensing, as well as unique and active committers, see [GitHub Advanced Security license billing](/en/billing/managing-billing-for-your-products/managing-billing-for-github-advanced-security/about-billing-for-github-advanced-security).

If you try to apply a security configuration with GHAS features to your repositories and don't have enough GHAS licenses, the configuration will only be successfully applied to public repositories. For private repositories, only free security features will be enabled due to the license limitation, resulting in the following outcomes:

* Free security features enabled in the configuration *will* be enabled for *all* private repositories.
* GHAS features *will not* be enabled for *any* private repositories.
* The security configuration *will not* be applied to *any* private repositories, since only some features from the configuration are enabled.

For more information on managing GHAS licenses for your organization, see [Managing your paid use of Advanced Security](/en/code-security/securing-your-organization/managing-the-security-of-your-organization/managing-your-github-advanced-security-license-usage).