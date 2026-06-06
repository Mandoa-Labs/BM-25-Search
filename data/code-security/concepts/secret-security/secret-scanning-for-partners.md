# Secret scanning for partners

When secret scanning detects authentication details for a service provider in a public repository on GitHub, an alert is sent directly to the provider. This allows service providers who are GitHub partners to promptly take action to secure their systems.

## About secret scanning alerts for partners

GitHub scans public repositories and public npm packages for secrets issued by specific service providers who joined our partnership program, and alerts the relevant service provider whenever a secret is detected in a commit. The service provider validates the string and then decides whether they should revoke the secret, issue a new secret, or contact you directly. Their action will depend on the associated risks to you or them.
To find out about our partner program, see [Secret scanning partner program](/en/code-security/secret-scanning/secret-scanning-partnership-program/secret-scanning-partner-program).

> \[!NOTE]You cannot change the configuration of secret scanning for partner patterns on public repositories.

Secret scanning alerts for partners scans:

* Descriptions and comments in issues
* Titles, descriptions, and comments, in open and closed *historical* issues
* Titles, descriptions, and comments in pull requests
* Titles, descriptions, and comments in GitHub Discussions
* Wikis
* Secret gists

The reason partner alerts are directly sent to the secret providers whenever a leak is detected for one of their secrets is that this enables the provider to take immediate action to protect you and protect their resources. The notification process for regular alerts is different. Regular alerts are displayed on the repository's **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab on GitHub for you to resolve.

If access to a resource requires paired credentials, then secret scanning will create an alert only when both parts of the pair are detected in the same file. This ensures that the most critical leaks are not hidden behind information about partial leaks. Pair matching also helps reduce false positives since both elements of a pair must be used together to access the provider's resource.

## What are the supported secrets

For information about the secrets and service providers supported by push protection, see [Supported secret scanning patterns](/en/code-security/secret-scanning/introduction/supported-secret-scanning-patterns#supported-secrets).

## Further reading

* [Secret scanning](/en/code-security/secret-scanning/introduction/about-secret-scanning)
* [Supported secret scanning patterns](/en/code-security/secret-scanning/introduction/supported-secret-scanning-patterns)
* [Secret scanning partner program](/en/code-security/secret-scanning/secret-scanning-partnership-program/secret-scanning-partner-program)