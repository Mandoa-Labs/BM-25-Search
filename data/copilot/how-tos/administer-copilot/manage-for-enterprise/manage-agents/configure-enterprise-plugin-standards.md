# Configuring enterprise plugin standards for Copilot CLI

Configure enterprise plugin standards by defining a settings.json file in your enterprise's .github-private repository.

> \[!NOTE] This feature is in public preview and subject to change.

1. In your enterprise's `.github-private` repository, navigate to the `.github/copilot/` directory. If you don't have a `.github-private` repository yet, see [Preparing to use custom agents in your enterprise](/en/copilot/how-tos/administer-copilot/manage-for-enterprise/manage-agents/prepare-for-custom-agents).

2. Create or edit the `settings.json` file at `.github/copilot/settings.json`.

3. Add your plugin policy configuration to the file. The `settings.json` file supports the following top-level properties:

   ```json copy
   {
     "extraKnownMarketplaces": {
       "MARKETPLACE-NAME": {
         "source": {
           "source": "github",
           "repo": "OWNER/REPO"
         }
       }
     },
     "enabledPlugins": {
       "PLUGIN-NAME@MARKETPLACE-NAME": true
     }
   }
   ```

   * `extraKnownMarketplaces`: Defines additional plugin marketplaces available to CLI users. Each entry is a named marketplace object containing a `source` property that specifies the provider (`"github"`) and the repository in `OWNER/REPO` format.
   * `enabledPlugins`: Defines plugins that are automatically installed for all enterprise users. Each entry uses the format `PLUGIN-NAME@MARKETPLACE-NAME` as the key, with a boolean value of `true` to enable the plugin.

4. Commit and push your changes to the default branch of the `.github-private` repository.

Once the configuration is committed, enterprise users will see the specified marketplaces and pre-installed plugins the next time they authenticate with Copilot CLI.