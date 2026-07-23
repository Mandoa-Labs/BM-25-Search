# Creating a repository for your project on GitHub

Create a repository on GitHub to store your code, track its history, and build a software project you can share.

In this tutorial, you'll create the repository you'll use throughout this series. You'll build a small software project called `stargazers-log`. By the end of the journey, you'll plan work, write code, review changes, and deploy your code to a live website.

`stargazers-log` is a simple website that tracks and displays repositories you have starred. It helps you build a personal catalog of tools and code examples you care about. Starring repositories also helps you bookmark projects for later and show appreciation to maintainers.

> \[!NOTE]
> As you follow this series, if you use GitHub Enterprise Cloud with data residency or GitHub Enterprise Server, you will need to substitute references and links to GitHub.com with your enterprise's dedicated URL.

## Prerequisites

* An account on GitHub. To sign up, go to [https://github.com/signup](https://github.com/signup?ref_product=github\&ref_type=engagement\&ref_style=text).

## What is a repository?

A repository is where you keep code and files for a software project on GitHub. It stores your files, tracks each change as a commit, and gives collaborators a shared place to work. Most software projects—from a single web page to a large application—live in their own repository.

## Creating your repository

Follow these steps to create the repository for this series.

1. In the upper-right corner of any page on GitHub, select <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-plus" aria-label="Create new" role="img"><path d="M7.75 2a.75.75 0 0 1 .75.75V7h4.25a.75.75 0 0 1 0 1.5H8.5v4.25a.75.75 0 0 1-1.5 0V8.5H2.75a.75.75 0 0 1 0-1.5H7V2.75A.75.75 0 0 1 7.75 2Z"></path></svg>, then click **New repository**.

   Alternatively, go to [new repository page on GitHub.com](https://github.com/new?ref_product=github\&ref_type=engagement\&ref_style=text) to open the new repository form directly.

2. Use the **Owner** dropdown menu to select your personal account to own the repository.

3. In the **Repository name** field, type `stargazers-log`.

4. In the **Description** field, type a short description, such as "A log of the repositories I've starred."

5. Use the **Choose visibility** dropdown menu to select **Public** so you can publish your software project to a live site later in this series.

6. Select **Add README**. This gives your repository a starting file and a place to describe your software project.

7. You do not need to add a `.gitignore` or license file for this software project, so leave those options unchanged.

8. Click **Create repository**.

## Adding a starter web page

Your software project will grow into a small web page, so add an `index.html` file to hold its content.

1. On the main page of your `stargazers-log` repository above the list of files, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-plus" aria-label="plus" role="img"><path d="M7.75 2a.75.75 0 0 1 .75.75V7h4.25a.75.75 0 0 1 0 1.5H8.5v4.25a.75.75 0 0 1-1.5 0V8.5H2.75a.75.75 0 0 1 0-1.5H7V2.75A.75.75 0 0 1 7.75 2Z"></path></svg>**, then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-plus" aria-label="plus" role="img"><path d="M7.75 2a.75.75 0 0 1 .75.75V7h4.25a.75.75 0 0 1 0 1.5H8.5v4.25a.75.75 0 0 1-1.5 0V8.5H2.75a.75.75 0 0 1 0-1.5H7V2.75A.75.75 0 0 1 7.75 2Z"></path></svg> Create new file**.

2. In the file name field, type `index.html`.

3. In the file editor, add the following starter content.

   ```html copy
   <!DOCTYPE html>
   <html lang="en">
     <head>
       <meta charset="utf-8">
       <title>Stargazers log</title>
     </head>
     <body>
       <h1>Stargazers log</h1>
       <p>A log of the repositories I've starred.</p>
     </body>
   </html>
   ```

4. Click **Commit changes**.

5. In the dialog that opens, keep the default option to commit directly to the `main` branch, then click **Commit changes**.

## What you accomplished

| Task                 | Outcome                                                                |
| -------------------- | ---------------------------------------------------------------------- |
| Created a repository | You created `stargazers-log` to store your software project on GitHub. |
| Added a README       | You gave your software project a place to describe itself.             |
| Added a web page     | You created `index.html` as the starting point for your site.          |

## Next steps

* Now that your software project has a home, plan the work you want to do. Continue to [Planning your work](/en/get-started/start-your-journey/planning-your-work).