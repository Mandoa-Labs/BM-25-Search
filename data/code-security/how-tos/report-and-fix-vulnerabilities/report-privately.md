# Privately reporting a security vulnerability

Some public repositories configure security advisories so that anyone can report security vulnerabilities directly and privately to the maintainers.

Owners and administrators of public repositories can enable private vulnerability reporting on their repositories. See [Configuring private vulnerability reporting for a repository](/en/code-security/security-advisories/working-with-repository-security-advisories/configuring-private-vulnerability-reporting-for-a-repository).

> \[!NOTE]
>
> * If you have admin or security permissions for a public repository, you don’t need to submit a vulnerability report. Instead, create a draft security advisory directly. See [Creating a repository security advisory](/en/code-security/security-advisories/working-with-repository-security-advisories/creating-a-repository-security-advisory).
> * Private vulnerability reporting is separate from a repository’s `SECURITY.md` file. You can only report vulnerabilities privately for repositories where this feature is enabled, and you don’t need to follow the instructions in `SECURITY.md`.

If a public repository has private vulnerability reporting enabled, anyone can submit a private vulnerability report to the repository maintainers.

If the repository doesn't have private vulnerability reporting enabled, you need to initiate the reporting process by following the instructions in the security policy for the repository, or by creating an issue asking the maintainers for a preferred security contact. See [Coordinated disclosure of security vulnerabilities](/en/code-security/security-advisories/guidance-on-reporting-and-writing-information-about-vulnerabilities/about-coordinated-disclosure-of-security-vulnerabilities#about-reporting-and-disclosing-vulnerabilities-in-projects-on-github).

1. On GitHub, navigate to the main page of the repository.

2. Under the repository name, click the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab. If you cannot see the "<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality" tab, select the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-kebab-horizontal" aria-label="kebab-horizontal" role="img"><path d="M8 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3ZM1.5 9a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Zm13 0a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z"></path></svg>** dropdown menu, and then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality**.

3. Click **Report a vulnerability** to open the advisory form.

4. Fill in the advisory details form.

   > \[!TIP]
   > In this form, only the title and description are mandatory. (In the general draft security advisory form, which the repository maintainer initiates, specifying the ecosystem is also required.) However, we recommend security researchers provide as much information as possible on the form so that the maintainers can make an informed decision about the submitted report. You can adopt the template used by our security researchers from the GitHub Security Lab, which is available on the [`github/securitylab` repository](https://github.com/github/securitylab/blob/main/docs/report-template.md).

   For more information about the fields available and guidance on filling in the form, see [Creating a repository security advisory](/en/code-security/security-advisories/working-with-repository-security-advisories/creating-a-repository-security-advisory) and [Best practices for writing repository security advisories](/en/code-security/security-advisories/guidance-on-reporting-and-writing-information-about-vulnerabilities/best-practices-for-writing-repository-security-advisories).

5. At the bottom of the form, click **Submit report**. GitHub will display a message letting you know that maintainers have been notified and that you have a pending credit for this security advisory.

   > \[!TIP]
   > When the report is submitted, GitHub automatically adds the reporter of the vulnerability as a collaborator and as a credited user on the proposed advisory.

6. Optionally, click **Start a temporary private fork** if you want to start to fix the issue. Note that only the repository maintainer can merge changes from that private fork into the parent repository.

   ![Screenshot of the bottom of a security advisory. A button, labeled "Start a temporary fork" is outlined in dark orange.](/assets/images/help/security/advisory-start-a-temporary-private-fork-button.png)

The next steps depend on the action taken by the repository maintainer. See [Managing privately reported security vulnerabilities](/en/code-security/security-advisories/guidance-on-reporting-and-writing-information-about-vulnerabilities/managing-privately-reported-security-vulnerabilities).