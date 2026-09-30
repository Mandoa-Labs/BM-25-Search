# Configuring toolsets for the GitHub MCP Server

Learn how to configure toolsets and tools for the GitHub MCP server for fine-grained control and optimized performance.

The GitHub MCP server includes default toolsets (`repos`, `issues`, and `pull_requests`) that are enabled automatically. You can customize toolset configuration by:

* **Enabling individual toolsets** such as `actions`, `code_security`, or `secret_protection`. For a step-by-step guide to scanning for secrets using the `secret_protection` toolset, see [Scanning for secrets with the GitHub MCP server](/en/code-security/how-tos/use-ghas-with-ai-coding-agents/scan-for-secrets-with-github-mcp-server).
* **Using special keywords** like `all` to enable every available toolset, or [`default`](https://github.com/github/github-mcp-server?tab=readme-ov-file#default-toolset) to include the standard set alongside others (for example, `default,stargazers`)
* **Accessing remote-only toolsets** such as `copilot` (for Copilot cloud agent) and `github_support_docs_search`, which are only available on the remote MCP server
* **Selecting specific tools** for granular control when you want to exclude specific tools or combine toolsets with individual tools

For a complete list of available toolsets, see [Tools](https://github.com/github/github-mcp-server/blob/main/README.md#tools) in the `github/github-mcp-server` repository. For configuration examples, see [Server configuration](https://github.com/github/github-mcp-server/blob/main/docs/server-configuration.md). For a full introduction to the GitHub MCP server and an overview of MCP, see [About Model Context Protocol (MCP)](/en/copilot/concepts/context/mcp).

## Configuring toolsets for the remote MCP server

You can configure toolsets for the remote GitHub MCP server using:

* **URL path parameters** when enabling a single toolset
* **HTTP headers** when enabling multiple toolsets

For detailed setup instructions, see [Remote GitHub MCP server](https://github.com/github/github-mcp-server?tab=readme-ov-file#remote-github-mcp-server) and [Remote server configuration](https://github.com/github/github-mcp-server/blob/main/docs/remote-server.md) in the `github/github-mcp-server` repository.

## Configuring toolsets for the local MCP server

You can configure toolsets for the local GitHub MCP server using:

* **Command-line flags**
* **Environment variables** (these take precedence over command-line flags)

For detailed setup instructions, see [Local GitHub MCP server](https://github.com/github/github-mcp-server?tab=readme-ov-file#local-github-mcp-server) and [Tool configuration](https://github.com/github/github-mcp-server?tab=readme-ov-file#tool-configuration) in the `github/github-mcp-server` repository.

## Further reading

* [Setting up the GitHub MCP Server](/en/copilot/how-tos/copilot-in-your-ide/customize-copilot/extend-copilot-with-tools-and-context/set-up-the-github-mcp-server)
* [Using the GitHub MCP Server in your IDE](/en/copilot/how-tos/copilot-in-your-ide/copilot-for-common-tasks/use-the-github-mcp-server)