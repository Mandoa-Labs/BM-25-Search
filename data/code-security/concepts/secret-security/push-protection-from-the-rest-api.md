# Working with push protection from the REST API

Learn your options for unblocking your push to GitHub using the REST API if secret scanning detects a secret in the content of your API request.

## About push protection from the REST API

Push protection prevents you from accidentally committing secrets to a repository by blocking pushes containing supported secrets.

The "Create a blob" and "Create or update file contents" endpoints in the REST API include push protection. See [REST API endpoints for Git blobs](/en/rest/git/blobs?apiVersion=2022-11-28#create-a-blob) and [REST API endpoints for repository contents](/en/rest/repos/contents?apiVersion=2022-11-28#create-or-update-file-contents).

If you make a request with these endpoints whose content includes a supported secret, the REST API will return a 409 error, indicating that a secret has been detected.

To resolve the error, you can either:

* **Remove** the secret from the content of your API request before trying again.
* **Create a push protection bypass:** You can bypass push protection using the "Create a push protection bypass" endpoint. For more information, see [REST API endpoints for secret scanning](/en/rest/secret-scanning/secret-scanning?apiVersion=2022-11-28#create-a-push-protection-bypass).

## Further reading

* [Working with push protection from the command line](/en/code-security/secret-scanning/working-with-secret-scanning-and-push-protection/working-with-push-protection-from-the-command-line)
* [Working with push protection in the GitHub UI](/en/code-security/secret-scanning/working-with-secret-scanning-and-push-protection/working-with-push-protection-in-the-github-ui)