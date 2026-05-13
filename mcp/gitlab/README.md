# GitLab MCP + Copilot CLI

![Docs](https://img.shields.io/badge/docs-setup-blue)
![GitLab](https://img.shields.io/badge/platform-GitLab-FC6D26)
![MCP](https://img.shields.io/badge/integration-MCP-7C3AED)

This folder documents what the GitLab MCP server provides and how to connect it to GitHub Copilot CLI.

- **Official GitLab guide:** <https://docs.gitlab.com/user/gitlab_duo/model_context_protocol/mcp_server/>
- **GitLab MCP tools reference:** <https://docs.gitlab.com/user/gitlab_duo/model_context_protocol/mcp_server_tools/>
- **Copilot CLI MCP guide:** <https://docs.github.com/en/copilot/how-tos/copilot-cli/customize-copilot/add-mcp-servers>

## Summary

The GitLab MCP server lets MCP-compatible assistants connect to GitLab securely and use GitLab-aware tools instead of relying only on pasted context.

From the GitLab documentation, the main points are:

- the feature is currently **Beta**
- it is available for **Premium** and **Ultimate**
- it works with **GitLab.com**, **GitLab Self-Managed**, and **GitLab Dedicated**
- it supports **HTTP transport** (recommended) and **stdio transport via `mcp-remote`**
- it uses **OAuth 2.0 Dynamic Client Registration**, so the first connection opens a browser-based authorization flow
- it can optionally prefix tool names with the `X-Gitlab-Mcp-Server-Tool-Name-Prefix` header to avoid collisions

Typical GitLab MCP tools cover workflows such as:

- reading project and repository information
- working with issues and merge requests
- calling GitLab-backed operations from an AI assistant with GitLab-authenticated access

## Prerequisites

Before connecting GitLab to Copilot CLI, make sure you have:

- GitHub Copilot CLI installed and authenticated
- a reachable GitLab instance URL
- on GitLab Self-Managed, GitLab Duo enabled for the instance
- on GitLab Self-Managed, beta and experimental features enabled
- Node.js 20 or later only if you plan to use the `mcp-remote` stdio fallback

When you see `<gitlab.example.com>` below:

- use your own hostname for GitLab Self-Managed or GitLab Dedicated
- use `gitlab.com` for GitLab.com

## Recommended setup: HTTP transport

GitLab recommends HTTP transport, and Copilot CLI supports adding HTTP MCP servers directly.

1. Start Copilot CLI:

```bash
copilot
```

2. In interactive mode, open the MCP add form:

```text
/mcp add
```

3. Fill the form with values like these:

| Field | Value |
| --- | --- |
| Server Name | `GitLab` |
| Server Type | `HTTP` |
| URL | `https://<gitlab.example.com>/api/v4/mcp` |
| HTTP Headers | optional: `{"X-Gitlab-Mcp-Server-Tool-Name-Prefix":"gitlab_"}` |
| Tools | `*` |

4. Press `Ctrl+S` to save.

5. When the browser opens, review and approve the GitLab OAuth authorization request.

6. Confirm the server is available:

```text
/mcp show GitLab
```

After saving, the server is available immediately in Copilot CLI.

## File-based Copilot CLI configuration

If you prefer to configure MCP servers in a file, Copilot CLI supports `~/.copilot/mcp-config.json`.

Use this JSON shape for GitLab over HTTP:

```json
{
  "mcpServers": {
    "GitLab": {
      "type": "http",
      "url": "https://<gitlab.example.com>/api/v4/mcp",
      "headers": {
        "X-Gitlab-Mcp-Server-Tool-Name-Prefix": "gitlab_"
      },
      "tools": ["*"]
    }
  }
}
```

Then start or restart `copilot`, approve the OAuth flow in your browser, and inspect the configured server with:

```text
/mcp show GitLab
```

## Fallback setup: stdio with `mcp-remote`

If direct HTTP is not the right fit for your environment, GitLab also documents a stdio option that proxies the remote MCP endpoint through `mcp-remote`.

In Copilot CLI, add it with `/mcp add` and use:

| Field | Value |
| --- | --- |
| Server Name | `GitLab` |
| Server Type | `STDIO` |
| Command | `npx mcp-remote https://<gitlab.example.com>/api/v4/mcp` |
| Environment Variables | `{}` |
| Tools | `*` |

This option requires Node.js 20 or later.

## Suggested Copilot CLI prompts

Once the server is connected, prompts like these work well:

```text
Use the GitLab MCP server to summarize my open merge requests.
```

```text
Use GitLab tools to list open issues in this project and group them by label.
```

```text
Use the connected GitLab MCP server to inspect the latest pipeline status for this repository.
```

## Notes and limitations

- The GitLab MCP server is a GitLab Beta feature, so setup and tool coverage may change.
- GitHub Copilot CLI already includes the GitHub MCP server by default; the steps in this README are for adding GitLab as an extra MCP server.
- If you connect multiple GitLab instances, use the tool-name prefix header to reduce tool-name clashes.
- GitLab explicitly warns about prompt injection risk. Use MCP tools only against GitLab content and instances you trust.
- If the OAuth page does not open, inspect the server with `/mcp show` and retry after restarting Copilot CLI.

## Related links

- [Repository root README](../../README.md)
- <https://docs.gitlab.com/user/gitlab_duo/model_context_protocol/mcp_server/>
- <https://docs.gitlab.com/user/gitlab_duo/model_context_protocol/mcp_server_tools/>
- <https://docs.github.com/en/copilot/how-tos/copilot-cli/customize-copilot/add-mcp-servers>
