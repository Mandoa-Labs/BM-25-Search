# Disabling automatic command approval in Copilot clients

Disable yolo mode to stop agents from running commands without approval.

> \[!NOTE] This feature is in public preview and subject to change.

You can prevent users from using modes that enable automatic approval of agent commands in Copilot CLI and VS Code. The `disableBypassPermissionsMode` setting is defined in your enterprise's `managed-settings.json` file and applies to users on your enterprise's Copilot plan.

This setting blocks users from using:

* The `--yolo` or `--allow-all` flag
* The `/yolo` or `/allow-all` command
* All runtime paths that enable combined bypass mode

This setting does **not** block individual flags such as `--allow-all-tools` or `--allow-all-paths`.

1. In your enterprise's `.github-private` repository, navigate to the `.github/copilot/` directory. If you haven't set a `.github-private` repository as your enterprise's source of agent configuration, see [Preparing to use custom agents in your enterprise](/en/copilot/how-tos/administer-copilot/manage-for-enterprise/manage-agents/prepare-for-custom-agents).
2. Create or edit the `managed-settings.json` file. (This file was previously named `settings.json`, which is also supported.)
3. Add the following property.

   ```json copy
   {
     "permissions": {
       "disableBypassPermissionsMode": "disable"
     }
   }
   ```