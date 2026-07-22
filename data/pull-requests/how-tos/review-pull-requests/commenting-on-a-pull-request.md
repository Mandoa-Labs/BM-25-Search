# Commenting on a pull request

Leave comments on pull requests in GitHub, including general feedback, line-specific suggestions, and file-level discussions to enhance collaboration and code reviews.

## About pull request comments

You can comment on a pull request's **Conversation** tab to leave general comments, questions, or praise. You can also suggest changes that the pull request author can apply directly from your comment.

You can also comment on specific files or sections of a file in a pull request's **Files changed** tab as individual line or file comments, or as part of a pull request review. Adding line or file comments is a great way to discuss questions about implementation or give feedback to the author. See [Pull request reviews](/en/pull-requests/reference/pull-request-reviews).

See [Reviewing proposed changes in a pull request](/en/pull-requests/how-tos/review-pull-requests/reviewing-proposed-changes-in-a-pull-request).

> \[!NOTE]
> If you reply to a pull request via email, your comment will be added on the **Conversation** tab and will not be part of a pull request review.

To reply to an existing line or file comment, navigate to the comment on either the **Conversation** tab or **Files changed** tab. Then, add another comment below it.

> \[!TIP]
>
> * Pull request comments support the same [formatting](/en/get-started/writing-on-github) as regular comments on GitHub, such as @mentions, emoji, and references.
> * You can add reactions to comments in pull requests in the **Files changed** tab.

## Adding comments to a pull request

1. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-git-pull-request" aria-label="git-pull-request" role="img"><path d="M1.5 3.25a2.25 2.25 0 1 1 3 2.122v5.256a2.251 2.251 0 1 1-1.5 0V5.372A2.25 2.25 0 0 1 1.5 3.25Zm5.677-.177L9.573.677A.25.25 0 0 1 10 .854V2.5h1A2.5 2.5 0 0 1 13.5 5v5.628a2.251 2.251 0 1 1-1.5 0V5a1 1 0 0 0-1-1h-1v1.646a.25.25 0 0 1-.427.177L7.177 3.427a.25.25 0 0 1 0-.354ZM3.75 2.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm0 9.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm8.25.75a.75.75 0 1 0 1.5 0 .75.75 0 0 0-1.5 0Z"></path></svg> Pull requests**.
2. In the list of pull requests, click the pull request where you want to leave line comments.
3. On the pull request, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-file-diff" aria-label="file-diff" role="img"><path d="M1 1.75C1 .784 1.784 0 2.75 0h7.586c.464 0 .909.184 1.237.513l2.914 2.914c.329.328.513.773.513 1.237v9.586A1.75 1.75 0 0 1 13.25 16H2.75A1.75 1.75 0 0 1 1 14.25Zm1.75-.25a.25.25 0 0 0-.25.25v12.5c0 .138.112.25.25.25h10.5a.25.25 0 0 0 .25-.25V4.664a.25.25 0 0 0-.073-.177l-2.914-2.914a.25.25 0 0 0-.177-.073ZM8 3.25a.75.75 0 0 1 .75.75v1.5h1.5a.75.75 0 0 1 0 1.5h-1.5v1.5a.75.75 0 0 1-1.5 0V7h-1.5a.75.75 0 0 1 0-1.5h1.5V4A.75.75 0 0 1 8 3.25Zm-3 8a.75.75 0 0 1 .75-.75h4.5a.75.75 0 0 1 0 1.5h-4.5a.75.75 0 0 1-.75-.75Z"></path></svg> Files changed**.

   ![Screenshot of the tabs for a pull request. The "Files changed" tab is outlined in dark orange.](/assets/images/help/pull_requests/pull-request-tabs-changed-files.png)
4. Hover over the line of code where you'd like to add a comment, and click the blue comment icon.

   ![Screenshot of a diff in a pull request. Next to a line number, a blue plus icon is highlighted with an orange outline.](/assets/images/help/commits/hover-comment-icon.png)
5. Optionally, you can add a comment on multiple lines. To select a range of lines, click the line number of the first line you want to comment on, then either drag down to the final line, or hold down <kbd>Shift</kbd> and click on the last line number. You can then click the blue comment icon on the last line you want to comment on. Alternatively, you can click the blue comment icon next to the first line you want to comment on, then drag down to the last line you want to comment on.
6. In the comment field, type your comment.
7. Optionally, to suggest a specific change to the line or lines, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-file-diff" aria-label="Suggestion" role="img"><path d="M1 1.75C1 .784 1.784 0 2.75 0h7.586c.464 0 .909.184 1.237.513l2.914 2.914c.329.328.513.773.513 1.237v9.586A1.75 1.75 0 0 1 13.25 16H2.75A1.75 1.75 0 0 1 1 14.25Zm1.75-.25a.25.25 0 0 0-.25.25v12.5c0 .138.112.25.25.25h10.5a.25.25 0 0 0 .25-.25V4.664a.25.25 0 0 0-.073-.177l-2.914-2.914a.25.25 0 0 0-.177-.073ZM8 3.25a.75.75 0 0 1 .75.75v1.5h1.5a.75.75 0 0 1 0 1.5h-1.5v1.5a.75.75 0 0 1-1.5 0V7h-1.5a.75.75 0 0 1 0-1.5h1.5V4A.75.75 0 0 1 8 3.25Zm-3 8a.75.75 0 0 1 .75-.75h4.5a.75.75 0 0 1 0 1.5h-4.5a.75.75 0 0 1-.75-.75Z"></path></svg>, then edit the text within the suggestion block.

   ![Screenshot of a review comment box. The file diff icon to suggest a specific change is outlined in dark orange.](/assets/images/help/pull_requests/suggestion-block.png)
8. To comment directly on a file, to the right of the file, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-comment" aria-label="The comment icon" role="img"><path d="M1 2.75C1 1.784 1.784 1 2.75 1h10.5c.966 0 1.75.784 1.75 1.75v7.5A1.75 1.75 0 0 1 13.25 12H9.06l-2.573 2.573A1.458 1.458 0 0 1 4 13.543V12H2.75A1.75 1.75 0 0 1 1 10.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h2a.75.75 0 0 1 .75.75v2.19l2.72-2.72a.749.749 0 0 1 .53-.22h4.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path></svg> and type your comment.

   ![Screenshot of an image file on the "Files changed" page of a pull request. To the right of the file, a comment icon is outlined in orange.](/assets/images/help/pull_requests/pull-request-comment-on-file.png)
9. When you're done:

   * If you only want to add this **one comment**, click **Add single comment**.

   * If you want to add **multiple comments**, click **Start a review**, then continue adding comments.

     When you're finished, click **Finish your review**, leave a summary of your review, and click **Submit review**.

Anyone watching the pull request or repository will receive a notification of your comments. Batching your comments avoids sending multiple notifications.

If you are commenting on a pull request created by Copilot, batching your comments prevents Copilot from starting to work on individual comments before you have completed your review. See [Starting GitHub Copilot sessions](/en/copilot/how-tos/use-copilot-agents/cloud-agent/start-copilot-sessions).

### Resolving conversations

You can resolve a conversation in a pull request if you opened the pull request or if you have write access to the repository where the pull request was opened.

To indicate that a conversation on the **Files changed** tab is complete, click **Resolve conversation**.

The entire conversation will collapse and be marked as resolved. This makes it easier to find conversations that still need to be addressed.

If the suggestion in a comment is out of your pull request's scope, you can open a new issue that tracks the feedback and links back to the original comment. See [Creating an issue](/en/issues/tracking-your-work-with-issues/using-issues/creating-an-issue#creating-an-issue-from-a-comment).

#### Discovering and navigating conversations

You can discover and navigate to all the conversations in your pull request with the **Conversations** menu on the **Files changed** tab.

In this view, you can see which conversations are unresolved, resolved, and outdated. This makes it easy to discover and resolve conversations.

![Screenshot of the "Conversations" menu on the "Files Changed" tab of a pull request.](/assets/images/help/pull_requests/conversations-menu.png)

## Further reading

* [Writing on GitHub](/en/get-started/writing-on-github)
* [Reporting abuse or spam](/en/communities/maintaining-your-safety-on-github/reporting-abuse-or-spam)