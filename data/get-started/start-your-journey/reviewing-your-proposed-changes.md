# Reviewing your proposed changes

Review your own pull request before you merge to catch bugs and improve quality, with an optional AI assist from Copilot.

A pull request is a chance to look at your work with fresh eyes before it becomes part of `main`. In this tutorial, you'll review your own changes, apply improvements, and merge the first feature for your website.

## Prerequisites

* An open pull request for your `add-starred-list` branch. If you haven't opened one yet, see [Writing and storing your code](/en/get-started/start-your-journey/writing-and-storing-your-code).

## Why review code?

Reviewing changes before you merge helps you catch bugs, spot missing error handling, and improve readability while the work is still fresh. Even when you work alone, a deliberate review builds a habit that keeps your software projects healthy and makes collaboration easier later.

## Reviewing your changes in the pull request

The **Files changed** tab in a pull request on GitHub shows a diff of everything your branch adds or modifies. Review it carefully.

1. Click [View your pull requests](https://github.com/pulls?ref_product=github\&ref_type=engagement\&ref_style=button) to go to your pull requests inbox on GitHub. Alternatively, navigate to your `stargazers-log` repository and click the **Pull requests** tab.
2. Click on the title to open your pull request for the `add-starred-list` branch.
3. Click the **Files changed** tab.
4. Read the diff for each file, looking for:
   * Bugs or logic errors, such as a mismatched file name in `script.js`.
   * Missing error handling, such as what happens if `events.json` fails to load.
   * Accessibility issues, such as missing text alternatives or unclear labels.
   * Anything unclear that a future reader might struggle with.
5. To note something you want to change, hover over a line, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-plus" aria-label="Add a comment" role="img"><path d="M7.75 2a.75.75 0 0 1 .75.75V7h4.25a.75.75 0 0 1 0 1.5H8.5v4.25a.75.75 0 0 1-1.5 0V8.5H2.75a.75.75 0 0 1 0-1.5H7V2.75A.75.75 0 0 1 7.75 2Z"></path></svg>, type a comment, then click **Comment**.

## Optional: Getting an AI second opinion

You can also ask Copilot Chat in your editor to review the same changes and offer a second perspective.

1. In your editor, open Copilot Chat.

2. Ask it to review your changes with a prompt like the following.

   ```text copy
   Review my changes for bugs, missing error handling, and accessibility issues.
   ```

3. Read the suggestions and decide which ones improve your feature. You're always in control of which changes to make.

> \[!TIP]
> If you enjoyed using Copilot to review your own code, you can [sign up for a paid plan](https://github.com/github-copilot/signup?ref_product=copilot\&ref_type=purchase\&ref_style=text\&ref_plan=pro) to get additional AI credits and Copilot code review, which can review your pull requests automatically when you add Copilot as a reviewer.
>
> For more information, see [Setting up GitHub Copilot for yourself](/en/copilot/how-tos/set-up/set-up-for-self) and [About GitHub Copilot code review](/en/copilot/concepts/agents/code-review).

## Applying feedback

Turn your review notes and any Copilot Chat suggestions you agree with into updates.

1. In your editor, update the affected files to address what you found.
2. In GitHub Desktop, enter a commit message such as `Address review feedback`, then click **Commit # files to add-starred-list**.
3. Click **Push origin** to update your pull request with the new commit.

## Merging the pull request

Once you're satisfied with your changes, merge them into `main`.

1. On GitHub, return to your pull request and refresh the page.
2. Click the **Conversation** tab.
3. Click **Merge pull request**, then click **Confirm merge**.
4. Click **Delete branch** to clean up your `add-starred-list` branch.

## Checking your progress

Update your project board to reflect the completed work.

1. On GitHub, navigate to your `Stargazers log` project board from the **Projects** tab in your repository.
2. Drag the `Display a list of starred repositories` item from **In Progress** to **Done**.

If you have more features to build, create new issues and move them to **In Progress** when you start the next cycle.

## The complete workflow

You've now run through the full developer workflow:

* Planned the work with an issue and a project board.
* Created a branch and built your feature.
* Opened a pull request.
* Reviewed your own changes (optionally with help from Copilot).
* Merged your feature into `main`.
* Updated your project board to reflect your progress.

## What you accomplished

| Task                                           | Outcome                                                            |
| ---------------------------------------------- | ------------------------------------------------------------------ |
| Reviewed changes in the Files changed tab      | You opened the pull request's Files changed tab and read the diff. |
| Applied feedback and got an optional AI assist | You applied changes, and possibly asked Copilot Chat for a review. |
| Merged your feature                            | You merged your changes into `main`.                               |
| Updated your progress                          | You moved the issue to **Done** on your project board.             |

## Next steps

* Publish your software project to a live URL that updates your website automatically. Continue to [Deploying your website automatically](/en/get-started/start-your-journey/deploying-your-website-automatically).