# Enabling delegated bypass for push protection

Control who can push code containing secrets by requiring bypass approval from designated reviewers.

Delegated bypass for push protection lets you define who can push commits containing secrets and adds an approval process for other contributors. See [Delegated bypass for push protection](/en/code-security/secret-scanning/using-advanced-secret-scanning-and-push-protection-features/delegated-bypass-for-push-protection/about-delegated-bypass-for-push-protection).

To enable delegated bypass, create the teams or roles that will manage bypass requests. Alternatively, use fine-grained permissions for more granular control. See [Using fine-grained permissions to control who can review and manage bypass requests](#using-fine-grained-permissions-to-control-who-can-review-and-manage-bypass-requests).

## Enabling delegated bypass for a repository

> \[!NOTE]
> If an organization or enterprise owner configures delegated bypass at the organization or enterprise level, the repository-level settings are disabled.

1. On GitHub, navigate to the main page of the repository.

2. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> Settings**. If you cannot see the "Settings" tab, select the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="More" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>** dropdown menu, then click **Settings**.

   ![Screenshot of a repository header showing the tabs. The "Settings" tab is highlighted by a dark orange outline.](/assets/images/help/repository/repo-actions-settings.png)

3. In the "Security" section of the sidebar, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-codescan" aria-label="codescan" role="img"><path d="M8.47 4.97a.75.75 0 0 0 0 1.06L9.94 7.5 8.47 8.97a.75.75 0 1 0 1.06 1.06l2-2a.75.75 0 0 0 0-1.06l-2-2a.75.75 0 0 0-1.06 0ZM6.53 6.03a.75.75 0 0 0-1.06-1.06l-2 2a.75.75 0 0 0 0 1.06l2 2a.75.75 0 1 0 1.06-1.06L5.06 7.5l1.47-1.47Z"></path><path d="M12.246 13.307a7.501 7.501 0 1 1 1.06-1.06l2.474 2.473a.749.749 0 0 1-.326 1.275.749.749 0 0 1-.734-.215ZM1.5 7.5a6.002 6.002 0 0 0 3.608 5.504 6.002 6.002 0 0 0 6.486-1.117.748.748 0 0 1 .292-.293A6 6 0 1 0 1.5 7.5Z"></path></svg> Advanced Security**.

4. Under "Secret Protection," ensure that push protection is enabled for the repository.

5. Under "Push protection," to the right of "Who can bypass push protection for secret scanning," select the dropdown menu, then click **Specific roles or teams**.

6. Under "Bypass list," click **Add role or team**.

7. In the dialog box, select the roles and teams that you want to add to the bypass list, then click **Add selected**.

   > \[!NOTE]
   > You can't add secret teams to the bypass list.

8. Optionally, to fully exempt the actors from push protection, to the right of the actors' details, select <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="ACTOR-OR-ROLE-NAME bypass actor actions" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>, then click **Exempt**.

   > \[!WARNING]
   > Push protection exemptions are designed for trusted automation that needs to push many commits with minimal friction. Exemptions may lead to leaked secrets, and should be granted with caution.

## Enabling delegated bypass for an organization

1. On GitHub, navigate to the main page of the organization.

2. Under your organization name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> Settings**. If you cannot see the "Settings" tab, select the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="More" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>** dropdown menu, then click **Settings**.

   ![Screenshot of the tabs in an organization's profile. The "Settings" tab is outlined in dark orange.](/assets/images/help/discussions/org-settings-global-nav-update.png)

3. In the "Security" section of the sidebar, select the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-codescan" aria-label="codescan" role="img"><path d="M8.47 4.97a.75.75 0 0 0 0 1.06L9.94 7.5 8.47 8.97a.75.75 0 1 0 1.06 1.06l2-2a.75.75 0 0 0 0-1.06l-2-2a.75.75 0 0 0-1.06 0ZM6.53 6.03a.75.75 0 0 0-1.06-1.06l-2 2a.75.75 0 0 0 0 1.06l2 2a.75.75 0 1 0 1.06-1.06L5.06 7.5l1.47-1.47Z"></path><path d="M12.246 13.307a7.501 7.501 0 1 1 1.06-1.06l2.474 2.473a.749.749 0 0 1-.326 1.275.749.749 0 0 1-.734-.215ZM1.5 7.5a6.002 6.002 0 0 0 3.608 5.504 6.002 6.002 0 0 0 6.486-1.117.748.748 0 0 1 .292-.293A6 6 0 1 0 1.5 7.5Z"></path></svg> Advanced Security** dropdown menu, then click **Configurations**.

4. Create a new custom security configuration, or edit an existing one. See [Creating a custom security configuration](/en/code-security/securing-your-organization/enabling-security-features-in-your-organization/creating-a-custom-security-configuration#creating-a-custom-security-configuration).

5. When defining the custom security configuration, under "Secret scanning," ensure that "Push protection" is set to **Enabled**.

6. Under "Push protection," to the right of "Bypass privileges," select the dropdown menu, then click **Specific actors**.

7. Select the <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-plus" aria-label="plus" role="img"><path d="M7.75 2a.75.75 0 0 1 .75.75V7h4.25a.75.75 0 0 1 0 1.5H8.5v4.25a.75.75 0 0 1-1.5 0V8.5H2.75a.75.75 0 0 1 0-1.5H7V2.75A.75.75 0 0 1 7.75 2Z"></path></svg> **Select actors** <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-triangle-down" aria-label="triangle-down" role="img"><path d="m4.427 7.427 3.396 3.396a.25.25 0 0 0 .354 0l3.396-3.396A.25.25 0 0 0 11.396 7H4.604a.25.25 0 0 0-.177.427Z"></path></svg> dropdown menu, then choose the actors you want to add to the bypass list.

   > \[!NOTE]
   >
   > * You can't add secret teams to the bypass list.
   > * In addition to assigning bypass privileges to roles and teams, you can also grant *individual* organization members the ability to review and manage bypass requests using fine-grained permissions. See [Using fine-grained permissions to control who can review and manage bypass requests](#using-fine-grained-permissions-to-control-who-can-review-and-manage-bypass-requests).

8. Optionally, to fully exempt the actors from push protection, to the right of the actors' details, select <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="ACTOR-OR-ROLE-NAME bypass actor actions" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>, then click **Exempt**.

   > \[!WARNING]
   > Push protection exemptions are designed for trusted automation that needs to push many commits with minimal friction. Exemptions may lead to leaked secrets, and should be granted with caution.

9. Click **Save configuration**.

10. Apply the security configuration to repositories in your organization. See [Applying a custom security configuration](/en/code-security/securing-your-organization/enabling-security-features-in-your-organization/applying-a-custom-security-configuration).

## Enabling delegated bypass for an enterprise

1. Navigate to your enterprise. For example, from the [Enterprises](https://github.com/settings/enterprises?ref_product=ghec\&ref_type=engagement\&ref_style=text) page on GitHub.com.

2. At the top of the page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> **Settings**.

3. In the left sidebar, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-codescan" aria-label="codescan" role="img"><path d="M8.47 4.97a.75.75 0 0 0 0 1.06L9.94 7.5 8.47 8.97a.75.75 0 1 0 1.06 1.06l2-2a.75.75 0 0 0 0-1.06l-2-2a.75.75 0 0 0-1.06 0ZM6.53 6.03a.75.75 0 0 0-1.06-1.06l-2 2a.75.75 0 0 0 0 1.06l2 2a.75.75 0 1 0 1.06-1.06L5.06 7.5l1.47-1.47Z"></path><path d="M12.246 13.307a7.501 7.501 0 1 1 1.06-1.06l2.474 2.473a.749.749 0 0 1-.326 1.275.749.749 0 0 1-.734-.215ZM1.5 7.5a6.002 6.002 0 0 0 3.608 5.504 6.002 6.002 0 0 0 6.486-1.117.748.748 0 0 1 .292-.293A6 6 0 1 0 1.5 7.5Z"></path></svg> Advanced SecurityCode security**.

4. In the "Security" section of the sidebar, select the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-codescan" aria-label="codescan" role="img"><path d="M8.47 4.97a.75.75 0 0 0 0 1.06L9.94 7.5 8.47 8.97a.75.75 0 1 0 1.06 1.06l2-2a.75.75 0 0 0 0-1.06l-2-2a.75.75 0 0 0-1.06 0ZM6.53 6.03a.75.75 0 0 0-1.06-1.06l-2 2a.75.75 0 0 0 0 1.06l2 2a.75.75 0 1 0 1.06-1.06L5.06 7.5l1.47-1.47Z"></path><path d="M12.246 13.307a7.501 7.501 0 1 1 1.06-1.06l2.474 2.473a.749.749 0 0 1-.326 1.275.749.749 0 0 1-.734-.215ZM1.5 7.5a6.002 6.002 0 0 0 3.608 5.504 6.002 6.002 0 0 0 6.486-1.117.748.748 0 0 1 .292-.293A6 6 0 1 0 1.5 7.5Z"></path></svg> Advanced Security** dropdown menu, then click **Configurations**.

5. Create a new custom security configuration, or edit an existing one. See [Creating a custom security configuration for your enterprise](/en/enterprise-cloud@latest/admin/managing-code-security/securing-your-enterprise/creating-a-custom-security-configuration-for-your-enterprise).

6. Under **Secret scanning**, ensure **Push protection** is enabled.

7. Under "Push protection," to the right of "Bypass privileges," select the dropdown menu, then click **Specific actors**.

   > \[!NOTE]
   > You can't add secret teams to the bypass list.

8. Select the <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-plus" aria-label="plus" role="img"><path d="M7.75 2a.75.75 0 0 1 .75.75V7h4.25a.75.75 0 0 1 0 1.5H8.5v4.25a.75.75 0 0 1-1.5 0V8.5H2.75a.75.75 0 0 1 0-1.5H7V2.75A.75.75 0 0 1 7.75 2Z"></path></svg> **Select actors** <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-triangle-down" aria-label="triangle-down" role="img"><path d="m4.427 7.427 3.396 3.396a.25.25 0 0 0 .354 0l3.396-3.396A.25.25 0 0 0 11.396 7H4.604a.25.25 0 0 0-.177.427Z"></path></svg> dropdown menu, then choose the actors you want to add to the bypass list.

9. Optionally, to fully exempt the actors from push protection, to the right of the actors' details, select <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="ACTOR-OR-ROLE-NAME bypass actor actions" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>, then click **Exempt**.

   > \[!WARNING]
   > Push protection exemptions are designed for trusted automation that needs to push many commits with minimal friction. Exemptions may lead to leaked secrets, and should be granted with caution.

10. Click **Save configuration**.

11. Apply the security configuration to organizations and repositories in your enterprise. See [Applying a custom security configuration to your enterprise](/en/code-security/how-tos/secure-at-scale/configure-enterprise-security/establish-complete-coverage/applying-a-custom-security-configuration-to-your-enterprise).

## Using fine-grained permissions to control who can review and manage bypass requests

You can grant specific individuals or teams in your organization the ability to review and manage bypass requests using fine-grained permissions.

1. Ensure that delegated bypass is enabled for the organization. For more information, follow steps 1-3 in [Enabling delegated bypass for your organization](/en/code-security/secret-scanning/using-advanced-secret-scanning-and-push-protection-features/delegated-bypass-for-push-protection/enabling-delegated-bypass-for-push-protection#enabling-delegated-bypass-for-an-organization) and ensure you have saved and applied the security configuration to your selected repositories.
2. Create (or edit) a custom organization role. For information on creating and editing custom roles, see [Managing custom organization roles](/en/organizations/managing-peoples-access-to-your-organization-with-roles/managing-custom-organization-roles#creating-a-custom-role).
3. When choosing which permissions to add to the custom role, select the "Review and manage secret scanning bypass requests" permission.
4. Assign the custom role to individual members or teams in your organization. For more information on assigning custom roles, see [Using organization roles](/en/organizations/managing-peoples-access-to-your-organization-with-roles/using-organization-roles#assigning-an-organization-role).