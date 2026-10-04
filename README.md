# RankZap assistant plugin

Version 0.1.0. This package contains a workflow skill and remote MCP configuration. It does not contain the RankZap application, customer data, provider keys or a local server binary.

**Release status: integration preview.** The server implementation and automated authorization/billing tests are complete; production activation is being coordinated with a hosting migration. The hosted endpoint must be enabled before sign-in works. Native-client acceptance and public marketplace approval are not yet claimed.

The package includes a portable Agent Plugins manifest for ChatGPT/Codex and compatibility manifests for Claude Code, Cursor and Grok Build. It executes no local hooks or scripts. Public directory submission is a separate process.

## Install the Claude Code plugin

Once the hosted service is enabled:

```text
/plugin marketplace add hasi100/rankzap-mcp
/plugin install rankzap@rankzap
```

The bundled skill teaches the review-and-approval workflow. Authenticate the bundled MCP server through `/mcp`.

## Connect

Remote URL: `https://rankzapseo.com/mcp` (Streamable HTTP with browser authorization).

Claude Code:

```sh
claude mcp add --transport http --scope user rankzap https://rankzapseo.com/mcp
```

Open `/mcp` to finish sign-in. When using this plugin's bundled MCP configuration, avoid adding a duplicate manual server.

Cursor: use the `mcpServers` object from [.mcp.json](.mcp.json) in `.cursor/mcp.json`, then authorize the connection.

ChatGPT: add the remote endpoint through the custom MCP/plugin settings where Developer Mode is available, sign in and enable it in the conversation. Installing a local Codex or Claude Code configuration does not connect ChatGPT.

Codex:

```sh
codex mcp add rankzap --url https://rankzapseo.com/mcp
codex mcp login rankzap
```

## Use

> Audit my website, explain the main issues, help me choose keywords and plan three articles per week. Show me each charge and let me review an article before publishing.

The user selects workspace/project access at sign-in. Each requested mutation or paid action returns a RankZap approval page. The application enforces scoped access, quotes, allowances, supplier budgets and revocation. The skill explains the workflow; it cannot override those controls.

Saved results are free. Paid MCP actions initially require managed launch pricing. Legacy subscriptions retain saved-data access; paid legacy actions use the dashboard until a compatible quote is available. Website connections are completed in RankZap; do not paste credentials into an assistant.

[Setup guide](https://rankzapseo.com/integrations/mcp) · [Manage access](https://rankzapseo.com/settings/assistants) · Support: hello@rankzapseo.com
