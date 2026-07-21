# Viewing code coverage on pull requests

Review the coverage summary posted on your pull requests to identify files with low or declining code coverage.

## Prerequisites

* Code coverage is configured for your repository. See [Setting up code coverage for your repository](/en/code-security/how-tos/maintain-quality-code/set-up-code-coverage).

## Reading the coverage summary comment

After code coverage is configured for your repository, the `github-code-quality[bot]` posts a coverage summary comment on each pull request. The comment includes:

* **Branch-vs-default-branch comparison:** The aggregate coverage percentage for the pull request branch and the default branch (for example, "65% on pull request branch, 44% on default branch").
* **Most impacted files:** The 10 files with the largest coverage changes between the default branch and the pull request branch. This list may include files not directly modified in the pull request. New or modified files are ranked above deleted files. Within each group, files are sorted by the absolute change in line coverage weighted by the number of lines in the file, with coverage magnitude and then filename as tiebreakers.
* **Per-file breakdown:** An expandable section listing each file with its coverage percentage and delta value. A positive delta means the file gained coverage on this branch. A negative delta indicates coverage decreased, which may signal untested code paths introduced by the change.

Use the coverage summary to identify files with low or declining coverage and prioritize review attention on untested changes.

If you need to extend coverage of your test suite, Copilot can help you write and update your tests. See [Testing code](/en/copilot/tutorials/copilot-cookbook/testing-code).

## Next steps

* [Resolving a block on your pull request](/en/code-security/how-tos/maintain-quality-code/unblock-your-pr)