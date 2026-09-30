# Configuring the GitHub MCP Server for GitHub Enterprise

Learn how to configure the GitHub Model Context Protocol (MCP) server to work with GitHub Enterprise Server or GitHub Enterprise Cloud with data residency.

The GitHub MCP server can be configured to work with GitHub Enterprise Server and GitHub Enterprise Cloud with data residency. The configuration steps differ depending on whether you are using the remote or local MCP server.

## About enterprise MCP server configuration

The GitHub MCP server supports two enterprise deployment types:

* **[GitHub Enterprise Cloud with data residency](#configuring-the-remote-mcp-server-for-github-enterprise-cloud-with-data-residency)**: Supports both remote and local MCP server configurations
* **[GitHub Enterprise Server](#configuring-the-local-mcp-server-for-enterprise)**: Supports **only local MCP server configuration**

> \[!IMPORTANT]
> GitHub Enterprise Server does **not** support remote MCP server hosting. If you are using GitHub Enterprise Server, you **must** use the local MCP server configuration described in [Configuring the local MCP server for enterprise](#configuring-the-local-mcp-server-for-enterprise). Skip the remote MCP server configuration section below.

## Prerequisites

* A GitHub Enterprise Server instance or GitHub Enterprise Cloud account with data residency
* The GitHub MCP server configured in your editor. See [Setting up the GitHub MCP Server](/en/copilot/how-tos/copilot-in-your-ide/customize-copilot/extend-copilot-with-tools-and-context/set-up-the-github-mcp-server).

## Configuring the remote MCP server for GitHub Enterprise Cloud with data residency

> \[!NOTE]
> This section applies **only** to GitHub Enterprise Cloud with data residency. If you are using GitHub Enterprise Server, skip to [Configuring the local MCP server for enterprise](#configuring-the-local-mcp-server-for-enterprise).

<div class="ghd-tool vscode">

GitHub Enterprise Cloud with data residency can use the remote MCP server. To configure it, you need to update the MCP server URL to point to your GitHub Enterprise Cloud instance.

For example, if your GitHub Enterprise Cloud instance is `https://octocorp.ghe.com`, the MCP server URL would be `https://copilot-api.octocorp.ghe.com/mcp`.

1. In Visual Studio Code, open the command palette by pressing <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (Windows/Linux) / <kbd>Command</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (Mac).

2. Type and select **MCP: Open User Configuration**.

3. In the settings file, locate the `servers` section. If you have already configured the GitHub MCP server, you will see a `github` entry.

4. Update the `url` field to point to your GitHub Enterprise Cloud instance.

   **Option A: With PAT authentication**

   ```json copy
   {
     "servers": {
       "github": {
         "type": "http",
         "url": "https://copilot-api.SUBDOMAIN.ghe.com/mcp",
         "headers": {
           "Authorization": "Bearer ${input:github_mcp_pat}"
         }
       }
     },
     "inputs": [
       {
         "type": "promptString",
         "id": "github_mcp_pat",
         "description": "GitHub PAT",
         "password": true
       }
     ]
   }
   ```

   **Option B: With OAuth authentication**

   ```json copy
   {
     "servers": {
       "github": {
         "type": "http",
         "url": "https://copilot-api.SUBDOMAIN.ghe.com/mcp"
       }
     }
   }
   ```

   Replace `SUBDOMAIN.ghe.com` with your GHE.com subdomain.

5. Save the file.

6. When using OAuth with GitHub Enterprise Cloud with data residency, configure your VS Code settings to point to your GitHub Enterprise Cloud instance. Add the following to your [VS Code user settings](https://code.visualstudio.com/docs/configure/settings#_user-settings):

   ```json
   {
     "github-enterprise.uri": "https://copilot-api.SUBDOMAIN.ghe.com/mcp"
   }
   ```

7. Restart Visual Studio Code or reload the window for the changes to take effect.

</div>

<div class="ghd-tool visualstudio">

GitHub Enterprise Cloud with data residency can use the remote MCP server. To configure it, you need to update the MCP server URL to point to your GitHub Enterprise Cloud instance.

For example, if your GitHub Enterprise Cloud instance is `https://octocorp.ghe.com`, the MCP server URL would be `https://copilot-api.octocorp.ghe.com/mcp`.

1. In the Visual Studio menu bar, click **View**, then click **GitHub Copilot Chat**.
2. At the bottom of the chat panel, select **Agent** from the mode dropdown.
3. In the Copilot Chat window, click the tools icon, then click the plus icon in the tool picker window.
4. In the "Configure MCP server" pop-up window, fill out the fields.
   1. For "Server ID", type `github`.
   2. For "Type", select "HTTP/SSE" from the dropdown.
   3. For "URL", type `https://copilot-api.YOURSUBDOMAIN.ghe.com/mcp`, replacing `YOURSUBDOMAIN` with your GitHub Enterprise Cloud subdomain.
   4. Add a new header under "Headers", called "Authorization" and set to the value `Bearer YOUR_GITHUB_PAT`, replacing "YOUR\_GITHUB\_PAT" with your personal access token.
5. Click **Save**.

</div>

<div class="ghd-tool jetbrains">

GitHub Enterprise Cloud with data residency can use the remote MCP server. To configure it, you need to update the MCP server URL to point to your GitHub Enterprise Cloud instance.

For example, if your GitHub Enterprise Cloud instance is `https://octocorp.ghe.com`, the MCP server URL would be `https://copilot-api.octocorp.ghe.com/mcp`.

1. In the lower right corner, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copilot" aria-label="copilot" role="img"><path d="M7.998 15.035c-4.562 0-7.873-2.914-7.998-3.749V9.338c.085-.628.677-1.686 1.588-2.065.013-.07.024-.143.036-.218.029-.183.06-.384.126-.612-.201-.508-.254-1.084-.254-1.656 0-.87.128-1.769.693-2.484.579-.733 1.494-1.124 2.724-1.261 1.206-.134 2.262.034 2.944.765.05.053.096.108.139.165.044-.057.094-.112.143-.165.682-.731 1.738-.899 2.944-.765 1.23.137 2.145.528 2.724 1.261.566.715.693 1.614.693 2.484 0 .572-.053 1.148-.254 1.656.066.228.098.429.126.612.012.076.024.148.037.218.924.385 1.522 1.471 1.591 2.095v1.872c0 .766-3.351 3.795-8.002 3.795Zm0-1.485c2.28 0 4.584-1.11 5.002-1.433V7.862l-.023-.116c-.49.21-1.075.291-1.727.291-1.146 0-2.059-.327-2.71-.991A3.222 3.222 0 0 1 8 6.303a3.24 3.24 0 0 1-.544.743c-.65.664-1.563.991-2.71.991-.652 0-1.236-.081-1.727-.291l-.023.116v4.255c.419.323 2.722 1.433 5.002 1.433ZM6.762 2.83c-.193-.206-.637-.413-1.682-.297-1.019.113-1.479.404-1.713.7-.247.312-.369.789-.369 1.554 0 .793.129 1.171.308 1.371.162.181.519.379 1.442.379.853 0 1.339-.235 1.638-.54.315-.322.527-.827.617-1.553.117-.935-.037-1.395-.241-1.614Zm4.155-.297c-1.044-.116-1.488.091-1.681.297-.204.219-.359.679-.242 1.614.091.726.303 1.231.618 1.553.299.305.784.54 1.638.54.922 0 1.28-.198 1.442-.379.179-.2.308-.578.308-1.371 0-.765-.123-1.242-.37-1.554-.233-.296-.693-.587-1.713-.7Z"></path><path d="M6.25 9.037a.75.75 0 0 1 .75.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 .75-.75Zm4.25.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 1.5 0Z"></path></svg>**.
2. From the menu, select "Open Chat", make sure you are in Agent mode, then click the tools icon (called "Configure your MCP server") at the bottom of the chat window.
3. Click **Add MCP Tools**.
4. In the `mcp.json` file, add the following configuration, replacing `YOURSUBDOMAIN` with your GitHub Enterprise Cloud subdomain and `YOUR_GITHUB_PAT` with your personal access token:

   ```json copy
   {
     "servers": {
       "github": {
         "url": "https://copilot-api.YOURSUBDOMAIN.ghe.com/mcp",
         "requestInit": {
           "headers": {
             "Authorization": "Bearer YOUR_GITHUB_PAT"
           }
         }
       }
     }
   }
   ```

</div>

<div class="ghd-tool xcode">

GitHub Enterprise Cloud with data residency can use the remote MCP server. To configure it, you need to update the MCP server URL to point to your GitHub Enterprise Cloud instance.

For example, if your GitHub Enterprise Cloud instance is `https://octocorp.ghe.com`, the MCP server URL would be `https://copilot-api.octocorp.ghe.com/mcp`.

1. Open the GitHub Copilot for Xcode extension and go to "Settings".
   * Alternatively, in an active Xcode workspace, you can find the settings by clicking **Editor** in the menu bar, selecting **GitHub Copilot**, then clicking **Open GitHub Copilot for Xcode Settings**.
2. Select the **MCP** tab, then click **Edit Config**.
3. Add the following configuration, replacing `YOURSUBDOMAIN` with your GitHub Enterprise Cloud subdomain and `YOUR_GITHUB_PAT` with your personal access token:

   ```json copy
   {
     "servers": {
       "github": {
         "url": "https://copilot-api.YOURSUBDOMAIN.ghe.com/mcp",
         "requestInit": {
           "headers": {
             "Authorization": "Bearer YOUR_GITHUB_PAT"
           }
         }
       }
     }
   }
   ```

</div>

<div class="ghd-tool eclipse">

GitHub Enterprise Cloud with data residency can use the remote MCP server. To configure it, you need to update the MCP server URL to point to your GitHub Enterprise Cloud instance.

For example, if your GitHub Enterprise Cloud instance is `https://octocorp.ghe.com`, the MCP server URL would be `https://copilot-api.octocorp.ghe.com/mcp`.

1. Click the Copilot icon (<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copilot" aria-label="copilot" role="img"><path d="M7.998 15.035c-4.562 0-7.873-2.914-7.998-3.749V9.338c.085-.628.677-1.686 1.588-2.065.013-.07.024-.143.036-.218.029-.183.06-.384.126-.612-.201-.508-.254-1.084-.254-1.656 0-.87.128-1.769.693-2.484.579-.733 1.494-1.124 2.724-1.261 1.206-.134 2.262.034 2.944.765.05.053.096.108.139.165.044-.057.094-.112.143-.165.682-.731 1.738-.899 2.944-.765 1.23.137 2.145.528 2.724 1.261.566.715.693 1.614.693 2.484 0 .572-.053 1.148-.254 1.656.066.228.098.429.126.612.012.076.024.148.037.218.924.385 1.522 1.471 1.591 2.095v1.872c0 .766-3.351 3.795-8.002 3.795Zm0-1.485c2.28 0 4.584-1.11 5.002-1.433V7.862l-.023-.116c-.49.21-1.075.291-1.727.291-1.146 0-2.059-.327-2.71-.991A3.222 3.222 0 0 1 8 6.303a3.24 3.24 0 0 1-.544.743c-.65.664-1.563.991-2.71.991-.652 0-1.236-.081-1.727-.291l-.023.116v4.255c.419.323 2.722 1.433 5.002 1.433ZM6.762 2.83c-.193-.206-.637-.413-1.682-.297-1.019.113-1.479.404-1.713.7-.247.312-.369.789-.369 1.554 0 .793.129 1.171.308 1.371.162.181.519.379 1.442.379.853 0 1.339-.235 1.638-.54.315-.322.527-.827.617-1.553.117-.935-.037-1.395-.241-1.614Zm4.155-.297c-1.044-.116-1.488.091-1.681.297-.204.219-.359.679-.242 1.614.091.726.303 1.231.618 1.553.299.305.784.54 1.638.54.922 0 1.28-.198 1.442-.379.179-.2.308-.578.308-1.371 0-.765-.123-1.242-.37-1.554-.233-.296-.693-.587-1.713-.7Z"></path><path d="M6.25 9.037a.75.75 0 0 1 .75.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 .75-.75Zm4.25.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 1.5 0Z"></path></svg>) in the status bar at the bottom of Eclipse.

2. From the menu, select **Open Chat** and, in the chat window, click the "Configure Tools..." icon.
   * Alternatively, you can select **Edit preferences**, then in the left pane, expand GitHub Copilot and click **MCP**.

3. Add the following configuration under "Server Configurations", replacing `YOURSUBDOMAIN` with your GitHub Enterprise Cloud subdomain and `YOUR_GITHUB_PAT` with your personal access token:

   ```json copy
   {
     "servers": {
       "github": {
         "url": "https://copilot-api.YOURSUBDOMAIN.ghe.com/mcp",
         "requestInit": {
           "headers": {
             "Authorization": "Bearer YOUR_GITHUB_PAT"
           }
         }
       }
     }
   }
   ```

4. Click **Apply**.

</div>

## Configuring the local MCP server for enterprise

Both GitHub Enterprise Server and GitHub Enterprise Cloud with data residency support the local MCP server. You can configure the local server using either the `GITHUB_HOST` environment variable or the `--gh-host` command-line flag.

### Important considerations

* **For GitHub Enterprise Server**: Prefix the hostname with the `https://` URI scheme, as it otherwise defaults to `http://`, which GitHub Enterprise Server does not support.
* **For GitHub Enterprise Cloud with data residency**: Use `https://YOURSUBDOMAIN.ghe.com` as the hostname.

### Configuration with Docker

<div class="ghd-tool vscode">

To configure the local MCP server with Docker in Visual Studio Code:

1. In Visual Studio Code, open the command palette by pressing <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (Windows/Linux) / <kbd>Command</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (Mac).

2. Type and select **MCP: Open User Configuration**.

3. In the settings file, locate the `servers` section or create it if it doesn't exist.

4. Add the following configuration:

   **For GitHub Enterprise Server:**

   ```json copy
   {
     "inputs": [
       {
         "type": "promptString",
         "id": "github_token",
         "description": "GitHub PAT",
         "password": true
       }
     ],
     "servers": {
       "github": {
         "command": "docker",
         "args": [
           "run",
           "-i",
           "--rm",
           "-e",
           "GITHUB_PERSONAL_ACCESS_TOKEN",
           "-e",
           "GITHUB_HOST",
           "ghcr.io/github/github-mcp-server"
         ],
         "env": {
           "GITHUB_PERSONAL_ACCESS_TOKEN": "${input:github_token}",
           "GITHUB_HOST": "https://YOUR_GHES_HOSTNAME"
         }
       }
     }
   }
   ```

   Replace `YOUR_GHES_HOSTNAME` with your GitHub Enterprise Server hostname (for example, `https://github.example.com`).

   **For GitHub Enterprise Cloud with data residency:**

   ```json copy
   {
     "inputs": [
       {
         "type": "promptString",
         "id": "github_token",
         "description": "GitHub PAT",
         "password": true
       }
     ],
     "servers": {
       "github": {
         "command": "docker",
         "args": [
           "run",
           "-i",
           "--rm",
           "-e",
           "GITHUB_PERSONAL_ACCESS_TOKEN",
           "-e",
           "GITHUB_HOST",
           "ghcr.io/github/github-mcp-server"
         ],
         "env": {
           "GITHUB_PERSONAL_ACCESS_TOKEN": "${input:github_token}",
           "GITHUB_HOST": "https://YOURSUBDOMAIN.ghe.com"
         }
       }
     }
   }
   ```

   Replace `YOURSUBDOMAIN` with your GitHub Enterprise Cloud subdomain.

5. Save the file.

6. Restart Visual Studio Code or reload the window for the changes to take effect.

</div>

<div class="ghd-tool visualstudio">

To configure the local MCP server with Docker in Visual Studio, you need to manually edit the `mcp.json` file.

1. Open the `mcp.json` file in Visual Studio. The file is typically located in your user profile directory.

2. Add the following configuration:

   **For GitHub Enterprise Server:**

   ```json copy
   {
     "mcp": {
       "inputs": [
         {
           "type": "promptString",
           "id": "github_token",
           "description": "GitHub PAT",
           "password": true
         }
       ],
       "servers": {
         "github": {
           "command": "docker",
           "args": [
             "run",
             "-i",
             "--rm",
             "-e",
             "GITHUB_PERSONAL_ACCESS_TOKEN",
             "-e",
             "GITHUB_HOST",
             "ghcr.io/github/github-mcp-server"
           ],
           "env": {
             "GITHUB_PERSONAL_ACCESS_TOKEN": "${input:github_token}",
             "GITHUB_HOST": "https://YOUR_GHES_HOSTNAME"
           }
         }
       }
     }
   }
   ```

   Replace `YOUR_GHES_HOSTNAME` with your GitHub Enterprise Server hostname (for example, `https://github.example.com`).

   **For GitHub Enterprise Cloud with data residency:**

   ```json copy
   {
     "mcp": {
       "inputs": [
         {
           "type": "promptString",
           "id": "github_token",
           "description": "GitHub PAT",
           "password": true
         }
       ],
       "servers": {
         "github": {
           "command": "docker",
           "args": [
             "run",
             "-i",
             "--rm",
             "-e",
             "GITHUB_PERSONAL_ACCESS_TOKEN",
             "-e",
             "GITHUB_HOST",
             "ghcr.io/github/github-mcp-server"
           ],
           "env": {
             "GITHUB_PERSONAL_ACCESS_TOKEN": "${input:github_token}",
             "GITHUB_HOST": "https://YOURSUBDOMAIN.ghe.com"
           }
         }
       }
     }
   }
   ```

   Replace `YOURSUBDOMAIN` with your GitHub Enterprise Cloud subdomain.

3. Save the file.

</div>

<div class="ghd-tool jetbrains">

To configure the local MCP server with Docker in JetBrains IDEs:

1. In the lower right corner, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copilot" aria-label="copilot" role="img"><path d="M7.998 15.035c-4.562 0-7.873-2.914-7.998-3.749V9.338c.085-.628.677-1.686 1.588-2.065.013-.07.024-.143.036-.218.029-.183.06-.384.126-.612-.201-.508-.254-1.084-.254-1.656 0-.87.128-1.769.693-2.484.579-.733 1.494-1.124 2.724-1.261 1.206-.134 2.262.034 2.944.765.05.053.096.108.139.165.044-.057.094-.112.143-.165.682-.731 1.738-.899 2.944-.765 1.23.137 2.145.528 2.724 1.261.566.715.693 1.614.693 2.484 0 .572-.053 1.148-.254 1.656.066.228.098.429.126.612.012.076.024.148.037.218.924.385 1.522 1.471 1.591 2.095v1.872c0 .766-3.351 3.795-8.002 3.795Zm0-1.485c2.28 0 4.584-1.11 5.002-1.433V7.862l-.023-.116c-.49.21-1.075.291-1.727.291-1.146 0-2.059-.327-2.71-.991A3.222 3.222 0 0 1 8 6.303a3.24 3.24 0 0 1-.544.743c-.65.664-1.563.991-2.71.991-.652 0-1.236-.081-1.727-.291l-.023.116v4.255c.419.323 2.722 1.433 5.002 1.433ZM6.762 2.83c-.193-.206-.637-.413-1.682-.297-1.019.113-1.479.404-1.713.7-.247.312-.369.789-.369 1.554 0 .793.129 1.171.308 1.371.162.181.519.379 1.442.379.853 0 1.339-.235 1.638-.54.315-.322.527-.827.617-1.553.117-.935-.037-1.395-.241-1.614Zm4.155-.297c-1.044-.116-1.488.091-1.681.297-.204.219-.359.679-.242 1.614.091.726.303 1.231.618 1.553.299.305.784.54 1.638.54.922 0 1.28-.198 1.442-.379.179-.2.308-.578.308-1.371 0-.765-.123-1.242-.37-1.554-.233-.296-.693-.587-1.713-.7Z"></path><path d="M6.25 9.037a.75.75 0 0 1 .75.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 .75-.75Zm4.25.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 1.5 0Z"></path></svg>**.
2. From the menu, select "Open Chat", make sure you are in Agent mode, then click the tools icon (called "Configure your MCP server") at the bottom of the chat window.
3. Click **Add MCP Tools**.
4. Add the following configuration:

   **For GitHub Enterprise Server:**

   ```json copy
   {
     "inputs": [
       {
         "type": "promptString",
         "id": "github_token",
         "description": "GitHub PAT",
         "password": true
       }
     ],
     "servers": {
       "github": {
         "command": "docker",
         "args": [
           "run",
           "-i",
           "--rm",
           "-e",
           "GITHUB_PERSONAL_ACCESS_TOKEN",
           "-e",
           "GITHUB_HOST",
           "ghcr.io/github/github-mcp-server"
         ],
         "env": {
           "GITHUB_PERSONAL_ACCESS_TOKEN": "${input:github_token}",
           "GITHUB_HOST": "https://YOUR_GHES_HOSTNAME"
         }
       }
     }
   }
   ```

   Replace `YOUR_GHES_HOSTNAME` with your GitHub Enterprise Server hostname (for example, `https://github.example.com`).

   **For GitHub Enterprise Cloud with data residency:**

   ```json copy
   {
     "inputs": [
       {
         "type": "promptString",
         "id": "github_token",
         "description": "GitHub PAT",
         "password": true
       }
     ],
     "servers": {
       "github": {
         "command": "docker",
         "args": [
           "run",
           "-i",
           "--rm",
           "-e",
           "GITHUB_PERSONAL_ACCESS_TOKEN",
           "-e",
           "GITHUB_HOST",
           "ghcr.io/github/github-mcp-server"
         ],
         "env": {
           "GITHUB_PERSONAL_ACCESS_TOKEN": "${input:github_token}",
           "GITHUB_HOST": "https://YOURSUBDOMAIN.ghe.com"
         }
       }
     }
   }
   ```

   Replace `YOURSUBDOMAIN` with your GitHub Enterprise Cloud subdomain.

</div>

<div class="ghd-tool xcode">

To configure the local MCP server with Docker in Xcode:

1. Open the GitHub Copilot for Xcode extension and go to "Settings".
   * Alternatively, in an active Xcode workspace, you can find the settings by clicking **Editor** in the menu bar, selecting **GitHub Copilot**, then clicking **Open GitHub Copilot for Xcode Settings**.
2. Select the **MCP** tab, then click **Edit Config**.
3. Add the following configuration:

   **For GitHub Enterprise Server:**

   ```json copy
   {
     "inputs": [
       {
         "type": "promptString",
         "id": "github_token",
         "description": "GitHub PAT",
         "password": true
       }
     ],
     "servers": {
       "github": {
         "command": "docker",
         "args": [
           "run",
           "-i",
           "--rm",
           "-e",
           "GITHUB_PERSONAL_ACCESS_TOKEN",
           "-e",
           "GITHUB_HOST",
           "ghcr.io/github/github-mcp-server"
         ],
         "env": {
           "GITHUB_PERSONAL_ACCESS_TOKEN": "${input:github_token}",
           "GITHUB_HOST": "https://YOUR_GHES_HOSTNAME"
         }
       }
     }
   }
   ```

   Replace `YOUR_GHES_HOSTNAME` with your GitHub Enterprise Server hostname (for example, `https://github.example.com`).

   **For GitHub Enterprise Cloud with data residency:**

   ```json copy
   {
     "inputs": [
       {
         "type": "promptString",
         "id": "github_token",
         "description": "GitHub PAT",
         "password": true
       }
     ],
     "servers": {
       "github": {
         "command": "docker",
         "args": [
           "run",
           "-i",
           "--rm",
           "-e",
           "GITHUB_PERSONAL_ACCESS_TOKEN",
           "-e",
           "GITHUB_HOST",
           "ghcr.io/github/github-mcp-server"
         ],
         "env": {
           "GITHUB_PERSONAL_ACCESS_TOKEN": "${input:github_token}",
           "GITHUB_HOST": "https://YOURSUBDOMAIN.ghe.com"
         }
       }
     }
   }
   ```

   Replace `YOURSUBDOMAIN` with your GitHub Enterprise Cloud subdomain.

</div>

<div class="ghd-tool eclipse">

To configure the local MCP server with Docker in Eclipse:

1. Click the Copilot icon (<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copilot" aria-label="copilot" role="img"><path d="M7.998 15.035c-4.562 0-7.873-2.914-7.998-3.749V9.338c.085-.628.677-1.686 1.588-2.065.013-.07.024-.143.036-.218.029-.183.06-.384.126-.612-.201-.508-.254-1.084-.254-1.656 0-.87.128-1.769.693-2.484.579-.733 1.494-1.124 2.724-1.261 1.206-.134 2.262.034 2.944.765.05.053.096.108.139.165.044-.057.094-.112.143-.165.682-.731 1.738-.899 2.944-.765 1.23.137 2.145.528 2.724 1.261.566.715.693 1.614.693 2.484 0 .572-.053 1.148-.254 1.656.066.228.098.429.126.612.012.076.024.148.037.218.924.385 1.522 1.471 1.591 2.095v1.872c0 .766-3.351 3.795-8.002 3.795Zm0-1.485c2.28 0 4.584-1.11 5.002-1.433V7.862l-.023-.116c-.49.21-1.075.291-1.727.291-1.146 0-2.059-.327-2.71-.991A3.222 3.222 0 0 1 8 6.303a3.24 3.24 0 0 1-.544.743c-.65.664-1.563.991-2.71.991-.652 0-1.236-.081-1.727-.291l-.023.116v4.255c.419.323 2.722 1.433 5.002 1.433ZM6.762 2.83c-.193-.206-.637-.413-1.682-.297-1.019.113-1.479.404-1.713.7-.247.312-.369.789-.369 1.554 0 .793.129 1.171.308 1.371.162.181.519.379 1.442.379.853 0 1.339-.235 1.638-.54.315-.322.527-.827.617-1.553.117-.935-.037-1.395-.241-1.614Zm4.155-.297c-1.044-.116-1.488.091-1.681.297-.204.219-.359.679-.242 1.614.091.726.303 1.231.618 1.553.299.305.784.54 1.638.54.922 0 1.28-.198 1.442-.379.179-.2.308-.578.308-1.371 0-.765-.123-1.242-.37-1.554-.233-.296-.693-.587-1.713-.7Z"></path><path d="M6.25 9.037a.75.75 0 0 1 .75.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 .75-.75Zm4.25.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 1.5 0Z"></path></svg>) in the status bar at the bottom of Eclipse.

2. From the menu, select **Open Chat** and, in the chat window, click the "Configure Tools..." icon.
   * Alternatively, you can select **Edit preferences**, then in the left pane, expand GitHub Copilot and click **MCP**.

3. Add the following configuration under "Server Configurations":

   **For GitHub Enterprise Server:**

   ```json copy
   {
     "inputs": [
       {
         "type": "promptString",
         "id": "github_token",
         "description": "GitHub PAT",
         "password": true
       }
     ],
     "servers": {
       "github": {
         "command": "docker",
         "args": [
           "run",
           "-i",
           "--rm",
           "-e",
           "GITHUB_PERSONAL_ACCESS_TOKEN",
           "-e",
           "GITHUB_HOST",
           "ghcr.io/github/github-mcp-server"
         ],
         "env": {
           "GITHUB_PERSONAL_ACCESS_TOKEN": "${input:github_token}",
           "GITHUB_HOST": "https://YOUR_GHES_HOSTNAME"
         }
       }
     }
   }
   ```

   Replace `YOUR_GHES_HOSTNAME` with your GitHub Enterprise Server hostname (for example, `https://github.example.com`).

   **For GitHub Enterprise Cloud with data residency:**

   ```json copy
   {
     "inputs": [
       {
         "type": "promptString",
         "id": "github_token",
         "description": "GitHub PAT",
         "password": true
       }
     ],
     "servers": {
       "github": {
         "command": "docker",
         "args": [
           "run",
           "-i",
           "--rm",
           "-e",
           "GITHUB_PERSONAL_ACCESS_TOKEN",
           "-e",
           "GITHUB_HOST",
           "ghcr.io/github/github-mcp-server"
         ],
         "env": {
           "GITHUB_PERSONAL_ACCESS_TOKEN": "${input:github_token}",
           "GITHUB_HOST": "https://YOURSUBDOMAIN.ghe.com"
         }
       }
     }
   }
   ```

   Replace `YOURSUBDOMAIN` with your GitHub Enterprise Cloud subdomain.

4. Click **Apply**.

</div>

### Configuration when building from source

If you are building the MCP server from source instead of using Docker, you can set the `GITHUB_HOST` environment variable or use the `--gh-host` command-line flag:

**Using environment variable:**

```bash
export GITHUB_HOST="https://YOUR_GHES_OR_GHEC_HOSTNAME"
./github-mcp-server stdio
```

**Using command-line flag:**

```bash
./github-mcp-server --gh-host \
  "https://YOUR_GHES_OR_GHEC_HOSTNAME" stdio
```

Replace `YOUR_GHES_OR_GHEC_HOSTNAME` with your GitHub Enterprise Server hostname (for example, `https://github.example.com`) or GitHub Enterprise Cloud hostname (for example, `https://octocorp.ghe.com`).

## Next steps

* To learn how to use the GitHub MCP server, see [Using the GitHub MCP Server in your IDE](/en/copilot/how-tos/copilot-in-your-ide/copilot-for-common-tasks/use-the-github-mcp-server).
* To learn how to configure toolsets for the GitHub MCP server, see [Configuring toolsets for the GitHub MCP Server](/en/copilot/how-tos/copilot-in-your-ide/customize-copilot/extend-copilot-with-tools-and-context/configure-toolsets).