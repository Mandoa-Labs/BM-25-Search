# Finding public code that matches GitHub Copilot suggestions

Learn how to view code references when GitHub Copilot makes suggestions that matches publicly available code.

<div class="ghd-tool jetbrains">

This version of this article is for Copilot in JetBrains IDEs. For Copilot on other platforms, click the appropriate tab above.

</div>

<div class="ghd-tool vscode">

This version of this article is for Copilot in Visual Studio Code. For Copilot on other platforms, click the appropriate tab above.

</div>

<div class="ghd-tool webui">

This version of this article is for Copilot on the GitHub website. For Copilot on other platforms, click the appropriate tab above.

</div>

<div class="ghd-tool visualstudio">

This version of this article is for Copilot in Visual Studio. For Copilot on other platforms, click the appropriate tab above.

</div>

## Introduction

If you allow GitHub Copilot to make suggestions that match publicly available code or use a product that does not support "Block" mode, Copilot will display references to any similar code that is found. See [GitHub Copilot code referencing](/en/copilot/concepts/completions/code-referencing).

### Prerequisites

References to matching code are only generated if you use a product that does not support "Block" mode, or if Copilot is configured to allow suggestions that match publicly available code. This is configured in either your personal or  organization settings.

For more information, see [Managing GitHub Copilot policies as an individual subscriber](/en/copilot/how-tos/manage-your-account/manage-policies#enabling-or-disabling-suggestions-matching-public-code) or  [Managing policies and features for GitHub Copilot in your organization](/en/copilot/how-tos/administer-copilot/manage-for-organization/manage-policies#enabling-copilot-features-and-models-in-your-organization).

<div class="ghd-tool jetbrains">

## View code references for inline suggestions

You can view code references in the log file for your JetBrains IDE.

1. In your JetBrains IDE, select **Help** > **Show Log in Finder/Explorer**.

   The log file is displayed in your file manager. For example, for IntelliJ IDEA the log file is called `idea.log`.

2. Open the log file in your JetBrains IDE.

3. Search for "\[Public Code References]."

### Example log entry

```text
2025-02-26 09:22:12,045 [5581906] INFO - #copilot - [Public Code References] Text found matching public code in file:///Users/mona-lisa/git-repos/test-repo/fizzbuzz.js [Ln 1, Col 10] near fizzBuzz() ...:
  1) [NOASSERTION] https://github.com/nixsticks/todos/blob/ae427a721c7784da64a619ba17f60637fe1cc819/Loops/fizzbuzz/fizzbuzz.js
  2) [GPL-3.0] https://github.com/voloslg/algocasts/blob/34b423517486f908ca167b390d3b8bd05653829f/exercises/fizzbuzz/index.js
```

The log entry includes the following details:

* The date and time you accepted the suggestion.
* A "Public Code References" message telling you that similar code was found.
* The path to the file in which the suggestion was added.
* The line and column number where the suggestion was added.
* A list of matches, including:
  * The license type for the matching code—or `NOASSERTION` if no license was found.
  * The URL of the file on GitHub.com where the matching code was found.

### Verifying the code referencing functionality

You can verify that code referencing is working by prompting Copilot to add some commonly used code and checking the output in the log.

1. Create a file called `fizz-buzz.js` and open it in the editor.

2. Display the log as described in the previous section.

3. In the editor, type:

   ```javascript
   function fizzBuzz()
   ```

   With a space after the closing parenthesis.

   GitHub Copilot should suggest code to complete the function. Typically the suggestion will be a common implementation of the fizz buzz algorithm that will match publicly available code on the GitHub website.

4. To accept the suggestion, press <kbd>Tab</kbd>.

5. Check whether any entries for similar code have been added to the log.

</div>

<div class="ghd-tool vscode">

## View code references for inline suggestions

You can find code references in one of the GitHub Copilot logs in Visual Studio Code.

1. In Visual Studio Code, open the **Output** window by selecting **View** > **Output** from the menu bar.
2. In the dropdown menu at the right of the **Output** window, select **GitHub Copilot Log (Code References)**.
3. Leave the **GitHub Copilot Log (Code References)** view displayed while you use GitHub Copilot in Visual Studio Code.

   When you accept an inline suggestion that matches code in a public GitHub repository, an entry is added to the log.

   The log entry includes the following details:

   * The date and time you accepted the suggestion.
   * The name of the file in which the suggestion was added.
   * "Similar code at" followed by the location in the file where the suggestion was added.
   * An extract of the code that was added by the inline suggestion.
   * The license type for the matching code, if found, otherwise `unknown`.
   * The URL of the file on GitHub.com where the similar code was found.

### Example log entry

```text
2025-03-27 12:17:54.759 [info] file:///Users/monalisa/fizzbuzz.js Similar code at  [Ln 2, Col 8] let i = 1; i <= 100; i++) {  let output = '';  if (i % 3 === 0) {  output += 'Fizz';...
2025-03-27 12:17:54.759 [info] License: unknown, URL: https://github.com/octo-org/octo-repo/blob/8563f3b1d4f33952b22212b86e745539d1567ed1/examples/fizzBuzz.js
2025-03-27 12:17:54.759 [info] License: MIT, URL: https://github.com/octo-org/monalisa/blob/7e974691f4c8e6bc55f9b50688f05d746d1bc52b/exercises/2/fizz-buzz.js
```

### Verifying the code referencing functionality

You can verify that code referencing is working by prompting Copilot to add some commonly used code and checking the output in the log.

1. Create a file called `fizz-buzz.js` and open it in the editor.

2. Display the log as described in the previous section.

3. In the editor, type:

   ```javascript
   function fizzBuzz()
   ```

   With a space after the closing parenthesis.

   GitHub Copilot should suggest code to complete the function. Typically the suggestion will be a common implementation of the fizz buzz algorithm that will match publicly available code on the GitHub website.

4. To accept the suggestion, press <kbd>Tab</kbd>.

5. Check whether any entries for similar code have been added to the log.

</div>

<div class="ghd-tool visualstudio">

## View code references for inline suggestions

You can find code references in the GitHub Copilot log in Visual Studio.

1. In the menu bar, click **View**.
2. In the dropdown menu, click **Output**.
3. In Output view, click the box to the right of "Show output from" and select **GitHub Copilot**.
4. Leave the log displayed while you use GitHub Copilot in Visual Studio Code.

   When you accept an inline suggestion that matches code in a public GitHub repository, an entry is added to the log.

   The log entry includes the following details:

   * The time you accepted the suggestion. Click the "Show Timestamp" clock icon if the time is not displayed.
   * The description `[Completions Public Code Match Information]`.
   * The license type for the matching code, if found, otherwise `NOASSERTION`.
   * The URL of the file on GitHub.com where the similar code was found.

### Example log entry

```text
09:39:16:203	[Completions Public Code Match Information] Similar code with license type [MIT] https://github.com/octo-org/octo-repo/blob/34deb75eb6a2e22483ed465a6aec38c02eb2536e/routines/quicksort.js
```

### Verifying the code referencing functionality

You can verify that code referencing is working by prompting Copilot to add some commonly used code and checking the output in the log.

1. Create a file called `fizz-buzz.js` and open it in the editor.

2. Display the log as described in the previous section.

3. In the editor, type:

   ```javascript
   function fizzBuzz()
   ```

   With a space after the closing parenthesis.

   GitHub Copilot should suggest code to complete the function. Typically the suggestion will be a common implementation of the fizz buzz algorithm that will match publicly available code on the GitHub website.

4. To accept the suggestion, press <kbd>Tab</kbd>.

5. Check whether any entries for similar code have been added to the log.

</div>

## View code references for Copilot Chat

<div class="ghd-tool jetbrains">

If a response in Copilot Chat includes matching code, this is indicated at the end of the response by the following text:

> Similar code found with *n* license types - **View matches**

1. Click **View matches** to display details of the matched code in a new editor tab.

   For each example of matching code, the editor displays:

   * The license type for the matching code, if known.
   * The URL of the file on GitHub.com where the matching code was found.
   * A code snippet showing the matching code.

2. In the editor, <kbd>Ctrl</kbd>+click (Windows/Linux) or <kbd>Command</kbd>+click (Mac) a URL to view the full file on GitHub.com.

</div>

<div class="ghd-tool vscode">

If a response in Copilot Chat includes matching code, this is indicated at the end of the response by the following text:

> Similar code found with *n* license types - **View matches**

1. Click **View matches** to display details of the matched code in a new editor tab.

   For each example of matching code, the editor displays:

   * The license type for the matching code, if known.
   * The URL of the file on GitHub.com where the matching code was found.
   * A code snippet showing the matching code.

2. In the editor, <kbd>Ctrl</kbd>+click (Windows/Linux) or <kbd>Command</kbd>+click (Mac) a URL to view the full file on GitHub.com.

</div>

<div class="ghd-tool visualstudio">

If a response in Copilot Chat includes matching code, this is below the suggested code by the following text:

> Found similar code in public repos. **View matches**

Click **View matches** to open the GitHub Copilot log, if it is not already open, and add details of the matched code.

The details include:

* The time you added the details to the log. Click the "Show Timestamp" clock icon if the time is not displayed.
* The description `[Code Match]` as the first log entry before the list of matching code.
* The license type—if found—for each instance of similar code.
* The URL of the file on GitHub.com where the matching code was found.
* A code snippet showing the matching code.

### Logging example

````text
09:24:10:525	[Code Match] Similar code with 2 license type(s) [MIT, NOASSERTION]
09:24:10:525	## License: MIT
09:24:10:525	https://github.com/octo-org/octo-repo/tree/127aac4ab27a42706af01be80f7aae3b83f44fbc/buzzfizz.py
09:24:10:525	```
09:24:10:525	for i in range(1, n + 1):
09:24:10:525	        if i % 3 == 0 and i % 5 == 0:
09:24:10:525	            print('FizzBuzz')
09:24:10:525	        elif i % 3 == 0:
09:24:10:525	            print('Fizz')
09:24:10:525	        elif i % 5 == 0:
09:24:10:525	```
09:24:10:525	## License: NOASSERTION
09:24:10:525	https://github.com/octo-org/monalisa/tree/011308746e53b26b128fa53c044a2527c39231f0/fizz-buzz.py
09:24:10:525	```
09:24:10:525	i % 3 == 0 and i % 5 == 0:
09:24:10:525	            print('FizzBuzz')
09:24:10:525	        elif i % 3 == 0:
09:24:10:525	            print('Fizz')
09:24:10:525	        elif i % 5 == 0:
09:24:10:525	            print('Buzz')
09:24:10:525	        else:
09:24:10:525	            print(i)
09:24:10:525	```
````

</div>

<div class="ghd-tool webui">

## View code references for Copilot Chat

When Copilot Chat provides a response that includes code that matches code in a public GitHub repository, this is indicated beneath the code suggestion:

> < > Public code references from *n* repositories

To see details of the matching code:

1. Click the "Public code references..." text, under the code suggestion.

   A list of GitHub repositories containing matching code is displayed in a dropdown, together with licensing information, if found.

   ![Screenshot of an inline suggestion in Copilot Chat with a link to view code references.](/assets/images/help/copilot/code-reference-dotcom.png)

2. Click the name of a repository to display that repository on GitHub.com.

## View code references for Copilot cloud agent

When Copilot provides a response that includes code that matches code in a public GitHub repository, this is indicated in the agent session logs with a link to display details of the matched code. For more information, see [Managing agent sessions](/en/copilot/how-tos/copilot-on-github/use-copilot-agents/manage-and-track-agents).

</div>

## Further reading

* [GitHub Copilot code referencing](/en/copilot/concepts/completions/code-referencing)