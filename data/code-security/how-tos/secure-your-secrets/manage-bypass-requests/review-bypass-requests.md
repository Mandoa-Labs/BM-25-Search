# Reviewing requests to bypass push protection

Approve or deny requests from contributors who need to push commits containing secrets to your organization's repositories.

## Prerequisites

Before you can review bypass requests, delegated bypass must be enabled for your organization or repositories. See [Enabling delegated bypass for push protection](/en/code-security/how-tos/secure-your-secrets/manage-bypass-requests/enabling-delegated-bypass-for-push-protection).

You can review and manage these requests in security overview.

## Reviewing bypass requests for an organization

1. On GitHub, navigate to the main page of the organization.

2. Under your organization name, click the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab.

3. In the sidebar, under "Requests", click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-key" aria-label="key" role="img"><path d="M10.5 0a5.499 5.499 0 1 1-1.288 10.848l-.932.932a.749.749 0 0 1-.53.22H7v.75a.749.749 0 0 1-.22.53l-.5.5a.749.749 0 0 1-.53.22H5v.75a.749.749 0 0 1-.22.53l-.5.5a.749.749 0 0 1-.53.22h-2A1.75 1.75 0 0 1 0 14.25v-2c0-.199.079-.389.22-.53l4.932-4.932A5.5 5.5 0 0 1 10.5 0Zm-4 5.5c-.001.431.069.86.205 1.269a.75.75 0 0 1-.181.768L1.5 12.56v1.69c0 .138.112.25.25.25h1.69l.06-.06v-1.19a.75.75 0 0 1 .75-.75h1.19l.06-.06v-1.19a.75.75 0 0 1 .75-.75h1.19l1.023-1.025a.75.75 0 0 1 .768-.18A4 4 0 1 0 6.5 5.5ZM11 6a1 1 0 1 1 0-2 1 1 0 0 1 0 2Z"></path></svg> Push protection bypass**.

4. Select the **All statuses** dropdown menu, then click **Open** to view requests that are awaiting review, or that have been approved but for which the commits haven't been pushed to the repository yet.

5. Click the request that you want to review.

6. Review the details of the request.

7. Optionally, add a review comment. The comment will be added to the review request timeline and the secret scanning alert timeline. For example, you may wish to explain the reason for the approval or denial of the request for auditing and reporting reasons, and suggest next steps for the contributor to take.

8. To allow the contributor to push the commit containing the secret, click **Approve bypass request**. Or, to require the contributor to remove the secret from the commit, click **Deny bypass request**.

## Filtering requests

You can filter requests by repository, approver (member who has reviewed the request), requester (contributor making the request), timeframe, and status.

### Filtering by status

The following statuses are assigned to a request:

| Status      | Description                                                                                                      |
| ----------- | ---------------------------------------------------------------------------------------------------------------- |
|             |                                                                                                                  |
| `Approved`  | The request has been approved, but the commit(s) have not yet been pushed to the repository.                     |
|             |                                                                                                                  |
| `Cancelled` | The request has been cancelled by the contributor.                                                               |
| `Completed` | The request has been approved and the commit(s) have been pushed to the repository, or the request was rejected. |
| `Denied`    | The request has been reviewed and denied.                                                                        |
| `Expired`   | The request has expired. Requests are valid for 7 days.                                                          |
| `Open`      | The request has not yet been reviewed.                                                                           |

## Further reading

* [Delegated bypass for push protection](/en/code-security/secret-scanning/using-advanced-secret-scanning-and-push-protection-features/delegated-bypass-for-push-protection/about-delegated-bypass-for-push-protection)
* [Enabling delegated bypass for push protection](/en/code-security/secret-scanning/using-advanced-secret-scanning-and-push-protection-features/delegated-bypass-for-push-protection/enabling-delegated-bypass-for-push-protection)