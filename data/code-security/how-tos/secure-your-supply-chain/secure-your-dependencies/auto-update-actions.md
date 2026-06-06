# Keeping your actions up to date with Dependabot

You can use Dependabot to keep the actions you use updated to the latest versions.

When you enable Dependabot version updates for GitHub Actions, Dependabot will help ensure that references to actions in a repository's *workflow\.yml* file and reusable workflows used inside workflows are kept up to date. For more information, see [Dependabot version updates](/en/code-security/concepts/supply-chain-security/about-dependabot-version-updates).

## Enabling Dependabot version updates for actions

1. If you have already enabled Dependabot version updates for other ecosystems or package managers, simply open the existing `dependabot.yml` file. Otherwise, create a `dependabot.yml` configuration file in the `.github` directory of your repository. For more information, see [Configuring Dependabot version updates](/en/code-security/dependabot/dependabot-version-updates/configuring-dependabot-version-updates#enabling-dependabot-version-updates).
2. Specify `"github-actions"` as a `package-ecosystem` to monitor.
3. Set the `directory` to `"/"` to check for workflow files in `.github/workflows`.
4. Set a `schedule.interval` to specify how often to check for new versions.
5. Check the `dependabot.yml` configuration file in to the `.github` directory of the repository. If you have edited an existing file, save your changes.

You can also enable Dependabot version updates on forks. For more information, see [Configuring Dependabot version updates](/en/code-security/dependabot/dependabot-version-updates/configuring-dependabot-version-updates#enabling-version-updates-on-forks).

## Example `dependabot.yml` file for GitHub Actions

The example `dependabot.yml` file below configures version updates for GitHub Actions. The `directory` must be set to `"/"` to check for workflow files in `.github/workflows`. The `schedule.interval` is set to `"weekly"`. After this file has been checked in or updated, Dependabot checks for new versions of your actions. Dependabot will raise pull requests for version updates for any outdated actions that it finds. After the initial version updates, Dependabot will continue to check for outdated versions of actions once a week.

```yaml copy
# Set update schedule for GitHub Actions

version: 2
updates:

  - package-ecosystem: "github-actions"
    directory: "/"
    schedule:
      # Check for updates to GitHub Actions every week
      interval: "weekly"
```

## Configuring Dependabot version updates for actions

When enabling Dependabot version updates for actions, you must specify values for `package-ecosystem`, `directory`, and `schedule.interval`. There are many more optional properties that you can set to further customize your version updates. For more information, see [Dependabot options reference](/en/code-security/dependabot/working-with-dependabot/dependabot-options-reference).

## Further reading

* [Writing workflows](/en/actions/learn-github-actions)