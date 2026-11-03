# Odin for AI agents

[Odin](https://borghq.io) is Borg's security platform. This plugin connects your agent to Odin's MCP server so it can read your organisation's security findings, fix them in your repository, link the pull request and follow the retest.

It contains:

- The remote Odin MCP server at `https://odin.borghq.io/api/mcp`. You sign in with your Odin account; no API key is needed.
- Two skills: `set-up-odin` recommends the Odin setup that fits your repository, and `fix-odin-finding` fixes one finding from start to finish.

You need an Odin account in an organisation. Linking pull requests needs the organisation's GitHub integration, and changing findings needs the Member role or above.

## Install

### Claude Code

```sh
/plugin marketplace add BorgDevelopment/odin-plugin
/plugin install odin@borg
```

### GitHub Copilot

In VS Code, run **Chat: Install Plugin from Source** and enter `https://github.com/BorgDevelopment/odin-plugin`.

In Copilot CLI:

```sh
copilot plugin install BorgDevelopment/odin-plugin
```

### Cursor

Add the server from **Settings > MCP** with the URL `https://odin.borghq.io/api/mcp`. Marketplace availability will be linked here once the listing is published.

### Gemini CLI

```sh
gemini extensions install https://github.com/BorgDevelopment/odin-plugin
```

### Any other MCP client

Add a Streamable HTTP server with the URL `https://odin.borghq.io/api/mcp`. Clients that support MCP sign-in open Odin in your browser. For clients without sign-in, create an API key in Odin under **Workspace > API Keys** and send it as `Authorization: Bearer <key>`. Never paste the key into a chat.

For agents installing this server: add the remote URL above to the client's MCP configuration, restart the client, and let the user complete the Odin sign-in in their browser. Do not ask the user for an API key unless the client cannot sign in.

## What the agent can do

List and filter findings, pentests and assets; read a finding's remediation, suggested branch, linked pull requests and retest history; link an existing GitHub pull request; change a finding's status or assignee; follow findings; and read or post in its discussion. With your confirmation and write access, the agent can request a manual retest, which spends credits. These tools never create commits, push branches, or open or merge pull requests. Tools that change data are marked for confirmation by your client.

## Updating the plugin

When the skills or server configuration change, bump `version` in `plugin.json`, `.claude-plugin/plugin.json`, `.cursor-plugin/plugin.json` and `gemini-extension.json` together. Claude Code keeps users on the version they installed until it changes.

`plugin.json` and `mcp.json` follow the [Agent Plugins 1.0](https://agent-plugins.org) standard that GitHub Copilot reads. Keep client-specific fields, such as the logo, in the client manifests. Cursor reads its server from `.cursor-plugin/mcp.json`.

## Links

- Documentation: https://docs.borghq.io/platform/odin-mcp
- Guide for AI agents: https://docs.borghq.io/platform/agent-guide
- Privacy policy: https://odin.borghq.io/legal/privacy
- Support: mail@borghq.io or https://www.borghq.io/contact

## Licence

MIT
