# Finding existing vulnerabilities in code

Copilot Chat can help find common vulnerabilities in your code and suggest fixes.

While they may be considered "common knowledge" by many developers, the vast majority of newly introduced security weaknesses are due to vulnerabilities like cross-site scripting (XSS), SQL injection, and cross-site request forgery (CSRF). These vulnerabilities can be mitigated by following secure coding practices, such as using parameterized queries, input validation, and avoiding hard-coded sensitive data. GitHub Copilot can help detect and resolve these issues.

> \[!NOTE] While Copilot Chat can help find some common security vulnerabilities and help you fix them, you should not rely on Copilot for a comprehensive security analysis. Using code scanning will more thoroughly ensure your code is secure. For more information on setting up code scanning, see [Configuring default setup for code scanning](/en/code-security/code-scanning/enabling-code-scanning/configuring-default-setup-for-code-scanning).

## Example scenario

The JavaScript code below has a potential XSS vulnerability that could be exploited if the `name` parameter is not properly sanitized before being displayed on the page.

```javascript id=potential-xss
function displayName(name) {
  const nameElement = document.getElementById('name-display');
  nameElement.innerHTML = `Showing results for "${name}"`
}
```

## Example prompt

You can ask Copilot Chat to analyze code for common security vulnerabilities and provide explanations and fixes for the issues it finds.

```copilot copy prompt ref=potential-xss
Analyze this code for potential security vulnerabilities and suggest fixes.
```

## Example response

> \[!NOTE] The following response is an example. Copilot Chat responses are non-deterministic, so you may get a different response from the one shown here.

Copilot responds with an explanation of the vulnerability, and suggested changes to the code to fix it.

```javascript
function displayName(name) {
  const nameElement = document.getElementById('name-display');
  nameElement.textContent = `Showing results for "${name}"`;
}
```

## Further reading

* [Prompt engineering for GitHub Copilot Chat](/en/copilot/using-github-copilot/prompt-engineering-for-github-copilot)
* [Best practices for using GitHub Copilot](/en/copilot/using-github-copilot/best-practices-for-using-github-copilot)
* [About code scanning](/en/code-security/code-scanning/introduction-to-code-scanning/about-code-scanning)