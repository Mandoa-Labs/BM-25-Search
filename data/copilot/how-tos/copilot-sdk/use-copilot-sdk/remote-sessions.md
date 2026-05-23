# Remote sessions

Let users access their Copilot session from GitHub web and mobile by connecting the session to Mission Control.

> [!NOTE]
> Copilot SDK is currently in public preview. Functionality and availability are subject to change.

Remote sessions let users access their Copilot session from GitHub web and mobile. When enabled, the Copilot SDK connects each session to Mission Control, producing a URL that can be shared as a link or QR code.

## Prerequisites

* The user must be authenticated (GitHub token or logged-in user)
* The session's working directory must be a GitHub repository

## Enabling remote sessions

You can enable remote access at the client level (always-on) or toggle it per session (on-demand).

### Always-on (client-level)

Set `remote: true` when creating the client. Every session in a GitHub repo automatically gets a remote URL.

```typescript
import { CopilotClient } from "@github/copilot-sdk";

const client = new CopilotClient({ remote: true });
const session = await client.createSession({
  workingDirectory: "/path/to/github-repo",
  onPermissionRequest: async () => ({ allowed: true }),
});

session.on("session.info", (event) => {
  if (event.data.infoType === "remote") {
    console.log("Remote URL:", event.data.url);
  }
});
```

For examples in Python, Go, C#, and Rust, see the [`github/copilot-sdk` repository](https://github.com/github/copilot-sdk/blob/main/docs/features/remote-sessions.md#always-on-client-level). For Java, see the [`github/copilot-sdk-java` repository](https://github.com/github/copilot-sdk-java).

### On-demand (per-session toggle)

Use `session.rpc.remote.enable()` to start remote access mid-session, and `session.rpc.remote.disable()` to stop it. This is equivalent to Copilot CLI's `/remote on` and `/remote off` commands.

```typescript
const result = await session.rpc.remote.enable();
console.log("Remote URL:", result.url);

// Later: stop sharing
await session.rpc.remote.disable();
```

For examples in Python, Go, C#, and Rust, see the [`github/copilot-sdk` repository](https://github.com/github/copilot-sdk/blob/main/docs/features/remote-sessions.md#on-demand-per-session-toggle). For Java, see the [`github/copilot-sdk-java` repository](https://github.com/github/copilot-sdk-java).

## QR code generation

The remote URL can be rendered as a QR code for easy mobile access. The Copilot SDK provides the URL—use your preferred QR code library.

## Notes

* The `remote` client option only applies when the Copilot SDK spawns Copilot CLI. It is ignored when connecting to an external server via `cliUrl`.
* If the working directory is not a GitHub repository, remote setup is silently skipped (always-on mode) or returns an error (on-demand mode).
* Remote sessions require authentication. Ensure `gitHubToken` or `useLoggedInUser` is configured.