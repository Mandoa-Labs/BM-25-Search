# Managing pull requests for dependency updates

You manage pull requests raised by Dependabot in much the same way as other pull requests, but there are some extra options.

## Viewing Dependabot pull requests

1. On GitHub, navigate to the main page of the repository.
2. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-git-pull-request" aria-label="git-pull-request" role="img"><path d="M1.5 3.25a2.25 2.25 0 1 1 3 2.122v5.256a2.251 2.251 0 1 1-1.5 0V5.372A2.25 2.25 0 0 1 1.5 3.25Zm5.677-.177L9.573.677A.25.25 0 0 1 10 .854V2.5h1A2.5 2.5 0 0 1 13.5 5v5.628a2.251 2.251 0 1 1-1.5 0V5a1 1 0 0 0-1-1h-1v1.646a.25.25 0 0 1-.427.177L7.177 3.427a.25.25 0 0 1 0-.354ZM3.75 2.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm0 9.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm8.25.75a.75.75 0 1 0 1.5 0 .75.75 0 0 0-1.5 0Z"></path></svg> Pull requests**.

   ![Screenshot of the main page of a repository. In the horizontal navigation bar, a tab, labeled "Pull requests," is outlined in dark orange.](/assets/images/help/repository/repo-tabs-pull-requests-global-nav-update.png)
3. Any pull requests for security or version updates are easy to identify.
   * The author is [dependabot](https://github.com/dependabot), the bot account used by Dependabot.
   * By default, they have the `dependencies` label.

## Changing the rebase strategy for Dependabot pull requests

By default, Dependabot automatically rebases pull requests to resolve any conflicts. If a pull request has not been merged for 30 days, Dependabot will stop rebasing the pull request. You can still manually rebase and merge the pull request. If you'd prefer to handle merge conflicts manually, you can disable this using the `rebase-strategy` option. For details, see [Dependabot options reference](/en/code-security/dependabot/working-with-dependabot/dependabot-options-reference#rebase-strategy--).

## Allowing Dependabot to rebase and force push over extra commits

By default, Dependabot will stop rebasing a pull request once extra commits have been pushed to it. To allow Dependabot to force push over commits added to its branches, include any of the following strings: `[dependabot skip]` , `[skip dependabot]`, `[dependabot-skip]`, or `[skip-dependabot]`, in either lower or uppercase, to the commit message.

## Managing Dependabot pull requests with comment commands

You can use comment commands on Dependabot pull requests to manage and customize your dependency updates. For details, see [Dependabot pull request comment commands](/en/code-security/reference/supply-chain-security/dependabot-pull-request-comment-commands).

Dependabot will react with a "thumbs up" emoji to acknowledge the command, and may respond with a comment on the pull request. While Dependabot usually responds quickly, some commands may take several minutes to complete if Dependabot is busy processing other updates or commands.

If you run any of the commands for ignoring dependencies or versions, Dependabot stores the preferences for the repository centrally. While this is a quick solution, for repositories with more than one contributor it is better to explicitly define the dependencies and versions to ignore in the configuration file. This makes it easy for all contributors to see why a particular dependency isn't being updated automatically.

For more information, see [Dependabot options reference](/en/code-security/dependabot/working-with-dependabot/dependabot-options-reference#ignore--).