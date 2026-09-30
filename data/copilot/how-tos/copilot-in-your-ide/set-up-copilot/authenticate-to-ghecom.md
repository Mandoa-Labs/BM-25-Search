# Using GitHub Copilot with an account on GHE.com

Update your development environment to access a Copilot plan for an account on GHE.com.

To use GitHub Copilot in an IDE or the command line, you must authenticate to an account on GitHub that has a Copilot license.

If you receive access to Copilot through a managed user account owned by an enterprise on GHE.com, you may need to adjust some settings in your IDE before you can authenticate to your account.

Use the **tabs at the top of this article** to see instructions for your environment.

<div class="ghd-tool vscode">

## Authenticating from VS Code

1. To open your VS Code settings, press <kbd>Command</kbd>+<kbd>,</kbd> (Mac) or <kbd>Ctrl</kbd>+<kbd>,</kbd> (Windows).

2. In the search bar, search for `enterprise`.

3. For the `Github-enterprise: Uri` setting, enter the URL where you access GitHub. For example: `https://octocorp.ghe.com`.

4. In the VS Code settings, search for `copilot`.

5. Under "GitHub > Copilot: Advanced," click **Edit in settings.json**.

6. Inside the `github.copilot.advanced` property, add `"authProvider": "github-enterprise"`. For example:

   ```json copy
   "github.copilot.advanced": {
        "authProvider": "github-enterprise"
   },
   ```

7. Save the `settings.json` file.

8. You will be shown a prompt asking you to sign in to use GitHub Copilot. Click **Sign in to GitHub**, then follow the prompts to authorize your account.

   If you **don't see the prompt**, try restarting VS Code.

If you ever need to switch to an account on GitHub.com, remove the `authProvider` setting from `settings.json`.

</div>

<div class="ghd-tool jetbrains">

## Authenticating from JetBrains IDEs

To authenticate to GHE.com in a JetBrains editor, you must install version 1.4.11 or later of the Copilot extension. You must then configure the extension to work with GHE.com.

1. To open the editor preferences or settings dialog, press <kbd>Command</kbd>+<kbd>,</kbd> (Mac) or <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>S</kbd> (Windows).
2. In the left sidebar, expand the "Tools" section, then click **GitHub Copilot**.
3. In the "General" section, look for the "Authentication Provider" field and enter the hostname where you access GitHub. For example: `octocorp.ghe.com`.
4. To save your changes, click **OK**.
5. Follow the prompts to sign in to use GitHub Copilot.

To sign in and out of GitHub at any time, click the **Copilot Chat** icon (<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copilot" aria-label="copilot" role="img"><path d="M7.998 15.035c-4.562 0-7.873-2.914-7.998-3.749V9.338c.085-.628.677-1.686 1.588-2.065.013-.07.024-.143.036-.218.029-.183.06-.384.126-.612-.201-.508-.254-1.084-.254-1.656 0-.87.128-1.769.693-2.484.579-.733 1.494-1.124 2.724-1.261 1.206-.134 2.262.034 2.944.765.05.053.096.108.139.165.044-.057.094-.112.143-.165.682-.731 1.738-.899 2.944-.765 1.23.137 2.145.528 2.724 1.261.566.715.693 1.614.693 2.484 0 .572-.053 1.148-.254 1.656.066.228.098.429.126.612.012.076.024.148.037.218.924.385 1.522 1.471 1.591 2.095v1.872c0 .766-3.351 3.795-8.002 3.795Zm0-1.485c2.28 0 4.584-1.11 5.002-1.433V7.862l-.023-.116c-.49.21-1.075.291-1.727.291-1.146 0-2.059-.327-2.71-.991A3.222 3.222 0 0 1 8 6.303a3.24 3.24 0 0 1-.544.743c-.65.664-1.563.991-2.71.991-.652 0-1.236-.081-1.727-.291l-.023.116v4.255c.419.323 2.722 1.433 5.002 1.433ZM6.762 2.83c-.193-.206-.637-.413-1.682-.297-1.019.113-1.479.404-1.713.7-.247.312-.369.789-.369 1.554 0 .793.129 1.171.308 1.371.162.181.519.379 1.442.379.853 0 1.339-.235 1.638-.54.315-.322.527-.827.617-1.553.117-.935-.037-1.395-.241-1.614Zm4.155-.297c-1.044-.116-1.488.091-1.681.297-.204.219-.359.679-.242 1.614.091.726.303 1.231.618 1.553.299.305.784.54 1.638.54.922 0 1.28-.198 1.442-.379.179-.2.308-.578.308-1.371 0-.765-.123-1.242-.37-1.554-.233-.296-.693-.587-1.713-.7Z"></path><path d="M6.25 9.037a.75.75 0 0 1 .75.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 .75-.75Zm4.25.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 1.5 0Z"></path></svg>) in the status bar, then click **Login to GitHub**. Follow the prompts to sign in.

If you ever need to switch to an account on GitHub.com, remove the value you entered in the "Authentication Provider" field.

</div>

<div class="ghd-tool xcode">

## Authenticating from Xcode

1. Open the "GitHub Copilot for Xcode" application.
2. Click the **Advanced** tab.
3. In the "Auth provider URL" field, enter the URL where you access GitHub. For example: `https://octocorp.ghe.com`.
4. Authorize the extension by following the instructions in [Signing in to GitHub Copilot](/en/copilot/how-tos/copilot-in-your-ide/set-up-copilot/install-copilot-extension?tool=xcode#signing-in-to-github-copilot).

</div>

<div class="ghd-tool copilotcli">

## Authenticating from the command line

To use Copilot CLI, you must:

1. Download and install Copilot CLI. See [Installing GitHub Copilot CLI](/en/copilot/how-tos/copilot-cli/set-up-copilot-cli/install-copilot-cli).
2. Authenticate to the account on GHE.com where you receive your Copilot license with `copilot login --host SUBDOMAIN.ghe.com`.

For general information on using Copilot CLI, see [GitHub Copilot CLI](/en/copilot/how-tos/copilot-cli).

</div>

<div class="ghd-tool visualstudio">

## Authenticating from Visual Studio

To authenticate from Visual Studio, follow the steps in [Add your GitHub accounts to your Visual Studio keychain](https://learn.microsoft.com/en-us/visualstudio/ide/work-with-github-accounts?view=vs-2022\&ref_product=copilot\&ref_type=engagement\&ref_style=text\&ref_plan=enterprise#enabling-github-enterprise-accounts) on Microsoft Learn.

For the "GitHub Enterprise URL" field, enter the URL where you access GitHub. For example: `https://octocorp.ghe.com`.

</div>

<div class="ghd-tool eclipse">

## Authenticating from Eclipse

1. In the IDE, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copilot" aria-label="copilot" role="img"><path d="M7.998 15.035c-4.562 0-7.873-2.914-7.998-3.749V9.338c.085-.628.677-1.686 1.588-2.065.013-.07.024-.143.036-.218.029-.183.06-.384.126-.612-.201-.508-.254-1.084-.254-1.656 0-.87.128-1.769.693-2.484.579-.733 1.494-1.124 2.724-1.261 1.206-.134 2.262.034 2.944.765.05.053.096.108.139.165.044-.057.094-.112.143-.165.682-.731 1.738-.899 2.944-.765 1.23.137 2.145.528 2.724 1.261.566.715.693 1.614.693 2.484 0 .572-.053 1.148-.254 1.656.066.228.098.429.126.612.012.076.024.148.037.218.924.385 1.522 1.471 1.591 2.095v1.872c0 .766-3.351 3.795-8.002 3.795Zm0-1.485c2.28 0 4.584-1.11 5.002-1.433V7.862l-.023-.116c-.49.21-1.075.291-1.727.291-1.146 0-2.059-.327-2.71-.991A3.222 3.222 0 0 1 8 6.303a3.24 3.24 0 0 1-.544.743c-.65.664-1.563.991-2.71.991-.652 0-1.236-.081-1.727-.291l-.023.116v4.255c.419.323 2.722 1.433 5.002 1.433ZM6.762 2.83c-.193-.206-.637-.413-1.682-.297-1.019.113-1.479.404-1.713.7-.247.312-.369.789-.369 1.554 0 .793.129 1.171.308 1.371.162.181.519.379 1.442.379.853 0 1.339-.235 1.638-.54.315-.322.527-.827.617-1.553.117-.935-.037-1.395-.241-1.614Zm4.155-.297c-1.044-.116-1.488.091-1.681.297-.204.219-.359.679-.242 1.614.091.726.303 1.231.618 1.553.299.305.784.54 1.638.54.922 0 1.28-.198 1.442-.379.179-.2.308-.578.308-1.371 0-.765-.123-1.242-.37-1.554-.233-.296-.693-.587-1.713-.7Z"></path><path d="M6.25 9.037a.75.75 0 0 1 .75.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 .75-.75Zm4.25.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 1.5 0Z"></path></svg> Copilot** to open the menu.
2. Click **Edit Preferences...**.
3. In the **GitHub Enterprise Authentication Endpoint** field, enter the URL where you access GitHub. For example: `https://octocorp.ghe.com`.
4. Click **Apply**.
5. Open the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copilot" aria-label="copilot" role="img"><path d="M7.998 15.035c-4.562 0-7.873-2.914-7.998-3.749V9.338c.085-.628.677-1.686 1.588-2.065.013-.07.024-.143.036-.218.029-.183.06-.384.126-.612-.201-.508-.254-1.084-.254-1.656 0-.87.128-1.769.693-2.484.579-.733 1.494-1.124 2.724-1.261 1.206-.134 2.262.034 2.944.765.05.053.096.108.139.165.044-.057.094-.112.143-.165.682-.731 1.738-.899 2.944-.765 1.23.137 2.145.528 2.724 1.261.566.715.693 1.614.693 2.484 0 .572-.053 1.148-.254 1.656.066.228.098.429.126.612.012.076.024.148.037.218.924.385 1.522 1.471 1.591 2.095v1.872c0 .766-3.351 3.795-8.002 3.795Zm0-1.485c2.28 0 4.584-1.11 5.002-1.433V7.862l-.023-.116c-.49.21-1.075.291-1.727.291-1.146 0-2.059-.327-2.71-.991A3.222 3.222 0 0 1 8 6.303a3.24 3.24 0 0 1-.544.743c-.65.664-1.563.991-2.71.991-.652 0-1.236-.081-1.727-.291l-.023.116v4.255c.419.323 2.722 1.433 5.002 1.433ZM6.762 2.83c-.193-.206-.637-.413-1.682-.297-1.019.113-1.479.404-1.713.7-.247.312-.369.789-.369 1.554 0 .793.129 1.171.308 1.371.162.181.519.379 1.442.379.853 0 1.339-.235 1.638-.54.315-.322.527-.827.617-1.553.117-.935-.037-1.395-.241-1.614Zm4.155-.297c-1.044-.116-1.488.091-1.681.297-.204.219-.359.679-.242 1.614.091.726.303 1.231.618 1.553.299.305.784.54 1.638.54.922 0 1.28-.198 1.442-.379.179-.2.308-.578.308-1.371 0-.765-.123-1.242-.37-1.554-.233-.296-.693-.587-1.713-.7Z"></path><path d="M6.25 9.037a.75.75 0 0 1 .75.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 .75-.75Zm4.25.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 1.5 0Z"></path></svg> Copilot** menu again then click **Sign In to GitHub**.

</div>