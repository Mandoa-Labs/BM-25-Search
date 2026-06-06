# Secret scanning detection scope

Secret scanning uses pattern matching and validation to detect secrets. Detection varies based on pattern pairs, token types, and push protection settings.

## Detection of pattern pairs

Secret scanning will only detect pattern pairs, such as AWS Access Keys and Secrets, if the ID and the secret are found in the same file, and both are pushed to the repository. Pair matching helps reduce false positives since both elements of a pair (the ID and the secret) must be used together to access the provider's resource.

Pairs pushed to different files, or not pushed to the same repository, will not result in alerts. For more information about the supported pattern pairs, see the table in [Supported secret scanning patterns](/en/code-security/secret-scanning/introduction/supported-secret-scanning-patterns).

## About legacy GitHub tokens

For GitHub tokens, we check the validity of the secret to determine whether the secret is active or inactive. This means that for legacy tokens, secret scanning won't detect a GitHub Enterprise Server personal access token on GitHub Enterprise Cloud. Similarly, a GitHub Enterprise Cloud personal access token won't be found on GitHub Enterprise Server.

## Push protection limitations

If push protection did not detect a secret that you think should have been detected, then you should first check that push protection supports the secret type in the list of supported secrets. For further information, see [Supported secret scanning patterns](/en/code-security/secret-scanning/introduction/supported-secret-scanning-patterns#supported-secrets).

If your secret is in the supported list, there are various reasons why push protection may not detect it.

* Push protection only blocks leaked secrets on a subset of the most identifiable user-alerted patterns. Contributors can trust security defenses when such secrets are blocked as these are the patterns that have the lowest number of false positives.
* The version of your secret may be old. Older versions of certain tokens may not be supported by push protection as these tokens may generate a higher number of false positives than their most recent version. Push protection may also not apply to legacy tokens. For tokens such as Azure Storage Keys, GitHub only supports *recently created* tokens, not tokens that match the legacy patterns.
* The push may be too large, for example, if you're trying to push thousands of large files. A push protection scan may time out and not block a user if the push is too large. GitHub will still scan and create alerts, if needed, after the push.
* If the push results in the detection of over five new secrets, we will only show you the first five (we will always show you a maximum of five secrets at one time).
* If a push contains over 1,000 existing secrets (that is, secrets for which alerts have already been created), push protection will not block the push.
* If a push in a public repository is larger than 50 MB, push protection will skip it and won't scan it.
* If you see a bypass request without commit or file path details, it means that push protection ran out of time. The push was too large or the history too complex to locate the commit that introduced the secret.