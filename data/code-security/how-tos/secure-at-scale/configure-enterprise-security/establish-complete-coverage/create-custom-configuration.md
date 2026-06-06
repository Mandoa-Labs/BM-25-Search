# Creating a custom security configuration for your enterprise

Build a custom security configuration to meet the specific security needs of your enterprise.

## About custom security configurations

With custom security configurations, you can create collections of enablement settings for GitHub's security products to meet the specific security needs of your enterprise. For example, you can create a different custom security configuration for each organization or group of organizations to reflect their unique security requirements and compliance obligations.

You can also choose whether or not you want to include GitHub Code Security or GitHub Secret Protection features in a configuration.

If you do, keep in mind that these features incur usage costs (or require GitHub Advanced Security licenses) when applied to private and internal repositories. For more information, see [About GitHub Advanced Security](/en/enterprise-cloud@latest/get-started/learning-about-github/about-github-advanced-security).

> \[!IMPORTANT]
> The order and names of some settings will differ depending on whether you are using licenses for the original GitHub Advanced Security product, or for the two new products: GitHub Code Security and GitHub Secret Protection. See [Creating a GitHub Advanced Security configuration](#creating-a-github-advanced-security-configuration) or [Creating a Secret Protection and Code Security configuration](#creating-a-secret-protection-and-code-security-configuration).

## Creating a Secret Protection and Code Security configuration

<!-- This section describes the view for users with an unbundled GHAS license. That is, separate calculation of usage of Secret Protection and Code Security features. -->

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.

2. At the top of the page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> **Settings**.

3. In the left sidebar, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-codescan" aria-label="codescan" role="img"><path d="M8.47 4.97a.75.75 0 0 0 0 1.06L9.94 7.5 8.47 8.97a.75.75 0 1 0 1.06 1.06l2-2a.75.75 0 0 0 0-1.06l-2-2a.75.75 0 0 0-1.06 0ZM6.53 6.03a.75.75 0 0 0-1.06-1.06l-2 2a.75.75 0 0 0 0 1.06l2 2a.75.75 0 1 0 1.06-1.06L5.06 7.5l1.47-1.47Z"></path><path d="M12.246 13.307a7.501 7.501 0 1 1 1.06-1.06l2.474 2.473a.749.749 0 0 1-.326 1.275.749.749 0 0 1-.734-.215ZM1.5 7.5a6.002 6.002 0 0 0 3.608 5.504 6.002 6.002 0 0 0 6.486-1.117.748.748 0 0 1 .292-.293A6 6 0 1 0 1.5 7.5Z"></path></svg> Advanced SecurityCode security**.

4. In the "Security configurations" section, click **New configuration**.

5. To help identify your custom security configuration and clarify its purpose on the "Security configurations" page, name your configuration and create a description.

6. Optionally, enable "Secret Protection", a paid feature for private and internal  repositories. Enabling Secret Protection enables alerts for secret scanning. In addition, you can choose whether to enable, disable, or keep the existing settings for the following secret scanning features:
   * **Validity checks**. To learn more about validity checks for partner patterns, see [Evaluating alerts from secret scanning](/en/enterprise-cloud@latest/code-security/secret-scanning/managing-alerts-from-secret-scanning/evaluating-alerts#checking-a-secrets-validity).
   * **Extended metadata**. To learn more about extended metadata checks, see [About extended metadata checks](/en/enterprise-cloud@latest/code-security/concepts/secret-security/about-validity-checks#about-extended-metadata-checks) and [Evaluating alerts from secret scanning](/en/enterprise-cloud@latest/code-security/tutorials/remediate-leaked-secrets/evaluating-alerts#reviewing-extended-metadata-for-a-token).
   > \[!NOTE]
   > You can only enable extended metadata checks if validity checks are enabled.
   * **Non-provider patterns**. To learn more about scanning for non-provider patterns, see [Supported secret scanning patterns](/en/enterprise-cloud@latest/code-security/secret-scanning/introduction/supported-secret-scanning-patterns#non-provider-patterns) and [Viewing and filtering alerts from secret scanning](/en/enterprise-cloud@latest/code-security/secret-scanning/managing-alerts-from-secret-scanning/viewing-alerts).
   * **Scan for generic passwords**. To learn more, see [Application card: GitHub security and quality AI features](/en/enterprise-cloud@latest/code-security/secret-scanning/copilot-secret-scanning/responsible-ai-generic-secrets).
   * **Push protection**. To learn about push protection, see [Push protection](/en/enterprise-cloud@latest/code-security/secret-scanning/introduction/about-push-protection).
   * **Bypass privileges**. By assigning bypass privileges or exemptions, selected actors can bypass or skip push protection. There is a review and approval process for all other contributors. See [Delegated bypass for push protection](/en/enterprise-cloud@latest/code-security/secret-scanning/using-advanced-secret-scanning-and-push-protection-features/delegated-bypass-for-push-protection/about-delegated-bypass-for-push-protection).
   * **Prevent direct alert dismissals**. To learn more, see [Enabling delegated alert dismissal for secret scanning](/en/enterprise-cloud@latest/code-security/secret-scanning/using-advanced-secret-scanning-and-push-protection-features/enabling-delegated-alert-dismissal-for-secret-scanning).

7. Optionally, enable "Code Security", a paid feature for private and internal  repositories. You can choose whether to enable, disable, or keep the existing settings for the following code scanning features:
   * **Default setup**. To learn more about default setup, see [Configuring default setup for code scanning](/en/enterprise-cloud@latest/code-security/code-scanning/enabling-code-scanning/configuring-default-setup-for-code-scanning#about-default-setup).
     > \[!NOTE]
     > To create a configuration that you can apply to all repositories regardless of current code scanning setup, choose "Enabled with advanced setup allowed". This setting enables default setup only in repositories where CodeQL analysis is not actively run. *Option available from GitHub Enterprise Server 3.19.*
   * **Runner type**. If you want to target specific runners for code scanning, you can choose to use custom-labeled runners at this step. See [Configuring default setup for code scanning](/en/enterprise-cloud@latest/code-security/code-scanning/enabling-code-scanning/configuring-default-setup-for-code-scanning#assigning-labels-to-runners).
   * **Prevent direct alert dismissals**. To learn more, see [Enabling delegated alert dismissal for code scanning](/en/enterprise-cloud@latest/code-security/code-scanning/managing-your-code-scanning-configuration/enabling-delegated-alert-dismissal-for-code-scanning).

8. Still under "Code Security", in the "Dependency scanning" table, choose whether you want to enable, disable, or keep the existing settings for the following dependency scanning features:
   * **Dependency graph**. To learn about dependency graph, see [Dependency graph](/en/enterprise-cloud@latest/code-security/supply-chain-security/understanding-your-software-supply-chain/about-the-dependency-graph).
     > \[!TIP]
     > When both "Code Security" and Dependency graph are enabled, this enables dependency review, see [Dependency review](/en/enterprise-cloud@latest/code-security/supply-chain-security/understanding-your-software-supply-chain/about-dependency-review).
   * **Automatic dependency submission**. To learn about automatic dependency submission, see [Configuring automatic dependency submission for your repository](/en/enterprise-cloud@latest/code-security/supply-chain-security/understanding-your-software-supply-chain/configuring-automatic-dependency-submission-for-your-repository).
   * **Dependabot alerts**. To learn about Dependabot, see [Dependabot alerts](/en/enterprise-cloud@latest/code-security/dependabot/dependabot-alerts/about-dependabot-alerts).
   * **Security updates**. To learn about security updates, see [Dependabot security updates](/en/enterprise-cloud@latest/code-security/dependabot/dependabot-security-updates/about-dependabot-security-updates).
   * **Prevent direct alert dismissals**. To learn more, see [Enabling delegated alert dismissal for Dependabot](/en/enterprise-cloud@latest/code-security/dependabot/dependabot-alerts/enable-delegated-alert-dismissal).
   * **Malware alerts**. To learn more, see [Dependabot malware alerts](/en/enterprise-cloud@latest/code-security/concepts/supply-chain-security/dependabot-malware-alerts).

9. For "Private vulnerability reporting", choose whether you want to enable, disable, or keep the existing settings. To learn about private vulnerability reporting, see [Configuring private vulnerability reporting for a repository](/en/enterprise-cloud@latest/code-security/security-advisories/working-with-repository-security-advisories/configuring-private-vulnerability-reporting-for-a-repository).

10. Optionally, in the "Policy" section, you can use additional options to control how the configuration is applied:
    * **Use as default for newly created repositories**. Select the **None** <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-triangle-down" aria-label="triangle-down" role="img"><path d="m4.427 7.427 3.396 3.396a.25.25 0 0 0 .354 0l3.396-3.396A.25.25 0 0 0 11.396 7H4.604a.25.25 0 0 0-.177.427Z"></path></svg> dropdown menu, then click **Public**, **Private and internal**, or **All repositories**.
      > \[!NOTE]
      > The default security configuration for an organization is only automatically applied to new repositories created in your organization. If a repository is transferred into your organization, you will still need to apply an appropriate security configuration to the repository manually.

    * **Enforce configuration**. Block repository owners from changing features that are enabled or disabled by the configuration (features that are not set aren't enforced). Select **Enforce** from the dropdown menu.
    > \[!NOTE] Some situations can break the enforcement of security configurations. See [Security configuration enforcement](/en/enterprise-cloud@latest/code-security/reference/security-at-scale/security-configuration-enforcement).

11. To finish creating your custom security configuration, click **Save configuration**.

## Creating a GitHub Advanced Security configuration

<!-- This section describes the view for users with an bundled GHAS license. That is, a single calculation of usage of any GitHub Advanced Security features. -->

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.

2. At the top of the page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> **Settings**.

3. In the left sidebar, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-codescan" aria-label="codescan" role="img"><path d="M8.47 4.97a.75.75 0 0 0 0 1.06L9.94 7.5 8.47 8.97a.75.75 0 1 0 1.06 1.06l2-2a.75.75 0 0 0 0-1.06l-2-2a.75.75 0 0 0-1.06 0ZM6.53 6.03a.75.75 0 0 0-1.06-1.06l-2 2a.75.75 0 0 0 0 1.06l2 2a.75.75 0 1 0 1.06-1.06L5.06 7.5l1.47-1.47Z"></path><path d="M12.246 13.307a7.501 7.501 0 1 1 1.06-1.06l2.474 2.473a.749.749 0 0 1-.326 1.275.749.749 0 0 1-.734-.215ZM1.5 7.5a6.002 6.002 0 0 0 3.608 5.504 6.002 6.002 0 0 0 6.486-1.117.748.748 0 0 1 .292-.293A6 6 0 1 0 1.5 7.5Z"></path></svg> Advanced SecurityCode security**.

4. In the top section, click **New configuration**.

5. To help identify your custom security configuration and clarify its purpose on the "New configuration" page, name your configuration and create a description.

6. In the "GitHub Advanced Security features" row, choose whether to include or exclude GitHub Advanced Security (GHAS) features.

7. In the "Secret scanning" table, choose whether you want to enable, disable, or keep the existing settings for the following security features:
   * **Validity checks**. To learn more about validity checks for partner patterns, see [Evaluating alerts from secret scanning](/en/enterprise-cloud@latest/code-security/secret-scanning/managing-alerts-from-secret-scanning/evaluating-alerts#checking-a-secrets-validity).
   * **Non-provider patterns**. To learn more about scanning for non-provider patterns, see [Supported secret scanning patterns](/en/enterprise-cloud@latest/code-security/secret-scanning/introduction/supported-secret-scanning-patterns#non-provider-patterns) and [Viewing and filtering alerts from secret scanning](/en/enterprise-cloud@latest/code-security/secret-scanning/managing-alerts-from-secret-scanning/viewing-alerts).
   * **Scan for generic passwords**. To learn more, see [Application card: GitHub security and quality AI features](/en/enterprise-cloud@latest/code-security/secret-scanning/copilot-secret-scanning/responsible-ai-generic-secrets).
   * **Push protection**. To learn about push protection, see [Push protection](/en/enterprise-cloud@latest/code-security/secret-scanning/introduction/about-push-protection).
   * **Prevent direct alert dismissals**. To learn more, see [Enabling delegated alert dismissal for secret scanning](/en/enterprise-cloud@latest/code-security/secret-scanning/using-advanced-secret-scanning-and-push-protection-features/enabling-delegated-alert-dismissal-for-secret-scanning).

8. In the "Code scanning" table, choose whether you want to enable, disable, or keep the existing settings for code scanning default setup.
   * **Default setup**. To learn more, see [Configuring default setup for code scanning](/en/enterprise-cloud@latest/code-security/code-scanning/enabling-code-scanning/configuring-default-setup-for-code-scanning#about-default-setup).
     > \[!NOTE]
     > To create a configuration that you can apply to all repositories regardless of current code scanning setup, choose "Enabled with advanced setup allowed". This setting enables default setup only in repositories where CodeQL analysis is not actively run. *Option available from GitHub Enterprise Server 3.19.*
   * **Runner type**. If you want to target specific runners for code scanning, you can choose to use custom-labeled runners at this step. See [Configuring default setup for code scanning](/en/enterprise-cloud@latest/code-security/code-scanning/enabling-code-scanning/configuring-default-setup-for-code-scanning#assigning-labels-to-runners).
   * **Prevent direct alert dismissals**. To learn more, see [Enabling delegated alert dismissal for code scanning](/en/enterprise-cloud@latest/code-security/code-scanning/managing-your-code-scanning-configuration/enabling-delegated-alert-dismissal-for-code-scanning).

9. In the "Dependency scanning" table, choose whether you want to enable, disable, or keep the existing settings for the following dependency scanning features:
   * **Dependency graph**. To learn about dependency graph, see [Dependency graph](/en/enterprise-cloud@latest/code-security/supply-chain-security/understanding-your-software-supply-chain/about-the-dependency-graph).
     > \[!TIP]
     > When both "GitHub Advanced Security" and Dependency graph are enabled, this enables dependency review, see [Dependency review](/en/enterprise-cloud@latest/code-security/supply-chain-security/understanding-your-software-supply-chain/about-dependency-review).
   * **Automatic dependency submission**. To learn about automatic dependency submission, see [Configuring automatic dependency submission for your repository](/en/enterprise-cloud@latest/code-security/supply-chain-security/understanding-your-software-supply-chain/configuring-automatic-dependency-submission-for-your-repository).
   * **Dependabot alerts**. To learn about Dependabot, see [Dependabot alerts](/en/enterprise-cloud@latest/code-security/dependabot/dependabot-alerts/about-dependabot-alerts).
   * **Security updates**. To learn about security updates, see [Dependabot security updates](/en/enterprise-cloud@latest/code-security/dependabot/dependabot-security-updates/about-dependabot-security-updates).
   * **Prevent direct alert dismissals**. To learn more, see [Enabling delegated alert dismissal for Dependabot](/en/enterprise-cloud@latest/code-security/dependabot/dependabot-alerts/enable-delegated-alert-dismissal).
   * **Malware alerts**. To learn more, see [Dependabot malware alerts](/en/enterprise-cloud@latest/code-security/concepts/supply-chain-security/dependabot-malware-alerts).

10. For "Private vulnerability reporting", choose whether you want to enable, disable, or keep the existing settings. To learn about private vulnerability reporting, see [Configuring private vulnerability reporting for a repository](/en/enterprise-cloud@latest/code-security/security-advisories/working-with-repository-security-advisories/configuring-private-vulnerability-reporting-for-a-repository).

11. Optionally, in the "Policy" section, you can use additional options to control how the configuration is applied:
    * **Use as default for newly created repositories**. Select the **None** <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-triangle-down" aria-label="triangle-down" role="img"><path d="m4.427 7.427 3.396 3.396a.25.25 0 0 0 .354 0l3.396-3.396A.25.25 0 0 0 11.396 7H4.604a.25.25 0 0 0-.177.427Z"></path></svg> dropdown menu, then click **Public**, **Private and internal**, or **All repositories**.
      > \[!NOTE]
      > The default security configuration for an organization is only automatically applied to new repositories created in your organization. If a repository is transferred into your organization, you will still need to apply an appropriate security configuration to the repository manually.

    * **Enforce configuration**. Block repository owners from changing features that are enabled or disabled by the configuration (features that are not set aren't enforced). Select **Enforce** from the dropdown menu.
    > \[!NOTE] Some situations can break the enforcement of security configurations. See [Security configuration enforcement](/en/enterprise-cloud@latest/code-security/reference/security-at-scale/security-configuration-enforcement).

12. To finish creating your custom security configuration, click **Save configuration**.

## Next steps

To optionally configure additional secret scanning settings for the enterprise, see [Configuring additional secret scanning settings for your enterprise](/en/enterprise-cloud@latest/admin/managing-code-security/securing-your-enterprise/configuring-additional-secret-scanning-settings-for-your-enterprise).

To apply your custom security configuration to repositories in your organization, see [Applying a custom security configuration](/en/enterprise-cloud@latest/code-security/securing-your-organization/enabling-security-features-in-your-organization/applying-a-custom-security-configuration).

To learn how to edit your custom security configuration, see [Editing a custom security configuration](/en/enterprise-cloud@latest/code-security/securing-your-organization/managing-the-security-of-your-organization/editing-a-custom-security-configuration).