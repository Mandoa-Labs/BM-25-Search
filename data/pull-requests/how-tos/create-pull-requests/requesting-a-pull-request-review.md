# Requesting a pull request review

Request reviews for your pull requests from individuals or teams to ensure thorough feedback and collaboration.

To request a review, you need write access to the repository. You can request a review from a person or team with read access to the repository, and they  receive a notification. For complete details on permissions for requesting reviews, see [Pull request reviews](/en/pull-requests/reference/pull-request-reviews#requesting-and-requiring-reviews).

## Requesting reviews from collaborators and organization members

Suggested reviewers are based on [git blame data](/en/repositories/working-with-files/using-files/viewing-and-understanding-files). After someone reviews your pull request and you make changes, you can request another review from the same reviewer.

1. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-git-pull-request" aria-label="git-pull-request" role="img"><path d="M1.5 3.25a2.25 2.25 0 1 1 3 2.122v5.256a2.251 2.251 0 1 1-1.5 0V5.372A2.25 2.25 0 0 1 1.5 3.25Zm5.677-.177L9.573.677A.25.25 0 0 1 10 .854V2.5h1A2.5 2.5 0 0 1 13.5 5v5.628a2.251 2.251 0 1 1-1.5 0V5a1 1 0 0 0-1-1h-1v1.646a.25.25 0 0 1-.427.177L7.177 3.427a.25.25 0 0 1 0-.354ZM3.75 2.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm0 9.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm8.25.75a.75.75 0 1 0 1.5 0 .75.75 0 0 0-1.5 0Z"></path></svg> Pull requests**.

2. In the list of pull requests, click the pull request that you want a specific person or team to review.

3. To request a review from a suggested person under **Reviewers**, next to their username, click **Request**.

   ![Screenshot of the "Reviewers" section of a pull request's sidebar. To the right of @octocat, a "Request" link is outlined in dark orange.](/assets/images/help/pull_requests/request-suggested-review.png)

4. Optionally, to request a review from someone other than a suggested person, click **Reviewers**.

   If you know the name of the person or team you want a review from, type the username of the person or the name of the team you're asking to review your changes. Click their team name or username to request a review.

5. After your pull request is reviewed and you make the necessary changes, you can ask a reviewer to review your pull request again. Navigate to **Reviewers** in the right sidebar and click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-sync" aria-label="Re-request review" role="img"><path d="M1.705 8.005a.75.75 0 0 1 .834.656 5.5 5.5 0 0 0 9.592 2.97l-1.204-1.204a.25.25 0 0 1 .177-.427h3.646a.25.25 0 0 1 .25.25v3.646a.25.25 0 0 1-.427.177l-1.38-1.38A7.002 7.002 0 0 1 1.05 8.84a.75.75 0 0 1 .656-.834ZM8 2.5a5.487 5.487 0 0 0-4.131 1.869l1.204 1.204A.25.25 0 0 1 4.896 6H1.25A.25.25 0 0 1 1 5.75V2.104a.25.25 0 0 1 .427-.177l1.38 1.38A7.002 7.002 0 0 1 14.95 7.16a.75.75 0 0 1-1.49.178A5.5 5.5 0 0 0 8 2.5Z"></path></svg> next to the reviewer's name whose review you want.

   ![Screenshot of the "Reviewers" section of a pull request's sidebar. To the right of @octocat, a sync icon is outlined in dark orange.](/assets/images/help/pull_requests/request-re-review.png)

## Requesting a review from GitHub Copilot

> \[!NOTE]
> Copilot features require a Copilot plan. See [Plans for GitHub Copilot](/en/copilot/get-started/plans).

You can also request that Copilot review your code and provide feedback and suggested changes on your work. See [Using GitHub Copilot code review](/en/copilot/how-tos/use-copilot-agents/request-a-code-review/use-code-review).

## Further reading

* [Pull request reviews](/en/pull-requests/reference/pull-request-reviews)