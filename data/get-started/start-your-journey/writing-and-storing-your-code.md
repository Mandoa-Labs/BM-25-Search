# Writing and storing your code

Follow the core developer workflow to create a branch, write code, and open a pull request using Copilot and GitHub Desktop.

Now you'll build the website feature you planned: a page that lists starred repositories. Along the way, you'll follow the core developer workflow—setting up a space for your work, making and saving your changes, and proposing them for review—using branches, commits, and a pull request.

## Prerequisites

* A local clone of your `stargazers-log` repository. If you haven't set this up yet, see [Connecting to your code locally](/en/get-started/start-your-journey/connecting-to-your-code-locally).

## Creating a branch

A branch lets you work on your feature in its own space, without changing the `main` copy of your code until you're ready.

1. Open GitHub Desktop.
2. At the top of the app, click **Current Branch**, then click **New Branch**.
3. Name the branch `add-starred-list`, then click **Create Branch**.
4. Click **Publish branch** to make the branch available on GitHub.

## Building the website's code

Your feature needs a few files: sample data, a stylesheet, a script to display the data, and an updated home page.

You can write these files yourself or ask Copilot, an AI assistant, to generate them. Every GitHub account includes access to GitHub Copilot Free and an allowance of AI credits, so you can start using Copilot right away.

To learn about the Copilot plans available and how usage works, see [Plans for GitHub Copilot](/en/copilot/get-started/plans).

Open Copilot Chat in your editor and ask it to create the files with a prompt like the following.

<!-- markdownlint-disable search-replace -->

```text copy
Create a starred repositories page for my software project. Add:
- events.json with sample data for a few starred repositories
- style.css to style a simple list
- script.js to fetch events.json and render the list
- an update to index.html that links style.css and script.js

Use the code written in https://docs.github.com/get-started/start-your-journey/creating-and-changing-your-code.
```

<!-- markdownlint-enable search-replace -->

<a href="vscode://GitHub.Copilot-Chat?ref_product=copilot&ref_type=engagement&ref_style=button" target="_blank" class="btn btn-primary mt-3 mr-3 no-underline" aria-label="Open Copilot Chat in Visual Studio Code">
<span>Open Copilot Chat in VS Code</span> <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-link-external" aria-label="link external icon" role="img"><path d="M3.75 2h3.5a.75.75 0 0 1 0 1.5h-3.5a.25.25 0 0 0-.25.25v8.5c0 .138.112.25.25.25h8.5a.25.25 0 0 0 .25-.25v-3.5a.75.75 0 0 1 1.5 0v3.5A1.75 1.75 0 0 1 12.25 14h-8.5A1.75 1.75 0 0 1 2 12.25v-8.5C2 2.784 2.784 2 3.75 2Zm6.854-1h4.146a.25.25 0 0 1 .25.25v4.146a.25.25 0 0 1-.427.177L13.03 4.03 9.28 7.78a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042l3.75-3.75-1.543-1.543A.25.25 0 0 1 10.604 1Z"></path></svg>
</a><br><br>

Review what Copilot generates, then adjust the files to match the examples below.

If you didn't use Copilot, use your code editor to create the files below in the `add-starred-list` branch.

1. Create a file named `events.json` with the following sample data. Save the file.

   ```json copy
   [
     { "name": "octocat/Hello-World", "starred": "2024-01-15" },
     { "name": "github/docs", "starred": "2024-02-02" },
     { "name": "octo-org/octo-repo", "starred": "2024-03-21" }
   ]
   ```

2. Create a file named `style.css` with the following styles. Save the file.

   ```scss copy
   body {
     font-family: sans-serif;
     margin: 2rem;
   }

   ul {
     list-style: none;
     padding: 0;
   }

   li {
     padding: 0.5rem 0;
     border-bottom: 1px solid #ddd;
   }
   ```

3. Create a file named `script.js` with the following code. Save the file.

   ```javascript copy
   fetch("events.json")
     .then((response) => response.json())
     .then((events) => {
       const list = document.querySelector("#starred");
       events.forEach((event) => {
         const item = document.createElement("li");
         item.textContent = `${event.name} — starred ${event.starred}`;
         list.appendChild(item);
       });
     });
   ```

4. Update `index.html` to link the new files and hold the list. Save the file.

   ```html copy
   <!DOCTYPE html>
   <html lang="en">
     <head>
       <meta charset="utf-8">
       <title>Stargazers log</title>
       <link rel="stylesheet" href="style.css">
     </head>
     <body>
       <h1>Stargazers log</h1>
       <p>A log of the repositories I've starred.</p>
       <ul id="starred"></ul>
       <script src="script.js"></script>
     </body>
   </html>
   ```

## Committing and pushing your changes

Committing saves a snapshot of your changes, and pushing sends them to GitHub where they will be stored in your repository.

1. In GitHub Desktop, review your changed files in the left sidebar.
2. At the bottom of the sidebar, in the **Summary** field, type a commit message such as `Add starred repositories list`.
3. Click **Commit 4 files to add-starred-list**.
4. Click **Push origin** to send your commit to GitHub.

## Opening a pull request

A pull request proposes your branch's changes for review before they merge into `main`.

1. In GitHub Desktop, click **Preview Pull Request**, then click **Create Pull Request**. Your browser opens to the pull request form on GitHub.
2. Review the title and description, then add a note about what your feature does.
3. Click **Create pull request**.

## What you accomplished

| Task                  | Outcome                                                                                  |
| --------------------- | ---------------------------------------------------------------------------------------- |
| Created a branch      | You made an isolated space for your feature with `add-starred-list`.                     |
| Wrote the code        | You added the feature's files to your branch, with an optional assist from Copilot Chat. |
| Pushed your changes   | You stored your branch's changes on GitHub.                                              |
| Opened a pull request | You proposed your changes for review.                                                    |

## Further reading

* [About individual GitHub Copilot plans and benefits](/en/copilot/concepts/billing/individual-plans)
* [Usage-based billing for individuals](/en/copilot/concepts/billing/usage-based-billing-for-individuals)
* [Monitoring your GitHub AI Credits usage](/en/copilot/how-tos/manage-and-track-spending/monitor-ai-usage)

## Next steps

* Before you merge, review your own changes to catch issues early. Continue to [Reviewing your proposed changes](/en/get-started/start-your-journey/reviewing-your-proposed-changes).