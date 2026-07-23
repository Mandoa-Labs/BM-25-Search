# Deploying your website automatically

Automate your code deployment with GitHub Actions and GitHub Pages to publish updates to a live site with every push to the main branch.

Your feature is merged, so now you can share it. In this tutorial, you'll set up automatic deployment so every push to `main` publishes your software project to a live website.

> \[!NOTE]
> The URL of your GitHub Pages site depends on which version of GitHub you use.
>
> * On GitHub.com, your site is published at `YOUR-USERNAME.github.io/REPOSITORY`.
> * If you use GitHub with data residency on GHE.com, your site is published at `pages.SUBDOMAIN.ghe.com/YOUR-USERNAME/REPOSITORY`, where `SUBDOMAIN` is your enterprise's subdomain.
> * On GitHub Enterprise Server, your site is published at `pages.HOSTNAME/YOUR-USERNAME/REPOSITORY`, where `HOSTNAME` is the hostname of your GitHub Enterprise Server instance.

## Prerequisites

* A `stargazers-log` repository with your merged feature. If you haven't merged it yet, see [Reviewing your proposed changes](/en/get-started/start-your-journey/reviewing-your-proposed-changes).

## Enabling GitHub Pages

Set up GitHub Pages to host your site, and use GitHub Actions to build and publish it.

1. On GitHub, navigate to your `stargazers-log` repository.
2. Under your repository name, click **Settings**.
3. In the sidebar, in the "Code and automation" section, click **Pages**.
4. Under "Build and deployment", from the **Source** dropdown, select **GitHub Actions**.

Leave the other settings at their defaults. Next, you'll create **your own workflow** to build and deploy your site automatically.

## Creating a deployment workflow

A workflow is a set of automated steps that GitHub Actions runs for you. Add one that builds and deploys your site whenever you push to `main`.

1. In your repository, create a file named `.github/workflows/deploy.yml`.
   1. On the main page of your `stargazers-log` repository above the list of files, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-plus" aria-label="plus" role="img"><path d="M7.75 2a.75.75 0 0 1 .75.75V7h4.25a.75.75 0 0 1 0 1.5H8.5v4.25a.75.75 0 0 1-1.5 0V8.5H2.75a.75.75 0 0 1 0-1.5H7V2.75A.75.75 0 0 1 7.75 2Z"></path></svg>**, then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-plus" aria-label="plus" role="img"><path d="M7.75 2a.75.75 0 0 1 .75.75V7h4.25a.75.75 0 0 1 0 1.5H8.5v4.25a.75.75 0 0 1-1.5 0V8.5H2.75a.75.75 0 0 1 0-1.5H7V2.75A.75.75 0 0 1 7.75 2Z"></path></svg> Create new file**.
   2. In the file name field, type `.github/workflows/deploy.yml`.

2. Add the following workflow content.

   ```yaml copy
   name: Deploy to GitHub Pages

   on:
     push:
       branches:
         - main

   permissions:
     contents: read
     pages: write
     id-token: write

   jobs:
     deploy:
       runs-on: ubuntu-latest
       environment:
         name: github-pages
         url: ${{ steps.deployment.outputs.page_url }}
       steps:
         - name: Checkout
           uses: actions/checkout@v6
         - name: Setup Pages
           uses: actions/configure-pages@v5
         - name: Upload artifact
           uses: actions/upload-pages-artifact@v4
           with:
             path: '.'
         - name: Deploy to GitHub Pages
           id: deployment
           uses: actions/deploy-pages@v4
   ```

3. Commit the file directly to the `main` branch.

## Understanding the workflow

Each part of the workflow has a job to do:

* **`on`** tells GitHub Actions to run the workflow on every push to `main`.
* **`permissions`** grant the workflow the access it needs to publish to GitHub Pages.
* **`environment`** connects the job to your GitHub Pages site and exposes the published URL as `${{ steps.deployment.outputs.page_url }}`.
* **`steps`** check out your code, prepare GitHub Pages, upload your files as an artifact, and deploy them to your live site.

## Viewing your live site

After you commit the workflow, GitHub Actions runs it automatically.

1. In your repository, click the **Actions** tab to watch the workflow run.
2. Click the latest workflow run to see a summary of the job details.
3. When the run completes, open your published site at `https://YOUR-USERNAME.github.io/stargazers-log/`. Replace `YOUR-USERNAME` with your username.
   * For example, if your GitHub account username is `octocat`, your site is at `https://octocat.github.io/stargazers-log/`.

From now on, every push to `main` redeploys your site with your latest changes.

## What you built

Across this series, you built a complete software project and practiced the GitHub workflow:

| Stage                          | What you learned                          |
| ------------------------------ | ----------------------------------------- |
| Creating your software project | Repositories, README files                |
| Planning your work             | Issues, Projects (project boards)         |
| Connecting locally             | GitHub Desktop, cloning                   |
| Writing and storing code       | Branches, commits, pull requests, Copilot |
| Reviewing changes              | Pull request reviews, Copilot             |
| Deploying automatically        | GitHub Actions, GitHub Pages              |

## Next steps

* Expand your understanding of Git and GitHub. For more information, see [Git and GitHub learning resources](/en/get-started/start-your-journey/git-and-github-learning-resources).
* Explore Copilot Chat to learn faster and get help as you code. For more information, see [About GitHub Copilot Chat](/en/copilot/concepts/chat).
* Go deeper with AI and learn how agents can act like a practical coding partner by turning ideas into small actionable steps, generating examples, and handling repetitive work. For more information, see [Concepts for GitHub Copilot agents](/en/copilot/concepts/agents).
* Learn more about automating your software projects with GitHub Actions workflows. For more information, see [Understanding GitHub Actions](/en/actions/get-started/understand-github-actions).
* Add a custom domain or explore more ways to publish your website with GitHub Pages. For more information, see [Getting started with GitHub Pages](/en/pages/getting-started-with-github-pages).