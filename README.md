# 0xdesigner

Give design work to 0xdesigner from the conversation where you're already building.

This repository contains the **0xdesigner-owned plugin**, distributed directly. It is not an OpenAI- or Anthropic-endorsed marketplace listing.

## Fastest way to connect

- **Claude:** add `https://0xdesigner.com/mcp` as a custom connector at https://claude.ai/customize/connectors, sign in with your email, and it is available in Claude Code (desktop app and terminal) and claude.ai. No plugin needed.
- **Codex:** run `codex mcp add 0xdesigner --url https://0xdesigner.com/mcp` once in a terminal, sign in in the browser tab that opens, then start Codex. The app and the CLI share this setting.

Then say **“Use 0xdesigner and check that it is ready.”** The plugin below is the alternative for people who prefer it.

## Claude Code (terminal)

Not in Claude Code yet? Two commands, then start Claude Code:

```sh
claude mcp add --transport http --scope user 0xdesigner https://0xdesigner.com/mcp
claude mcp login 0xdesigner
```

A browser tab opens; sign in with your email code and choose Connect. Over SSH add `--no-browser`. If `0xdesigner` already exists, run only the login line, or remove an old token entry first with `claude mcp remove 0xdesigner`.

Already in a session? Install the plugin instead (Claude Code 2.1.275 or newer):

```
/plugin install 0xdesigner --marketplace 0xdesign/0xdesigner-mcp
```

Older versions run `/plugin marketplace add 0xdesign/0xdesigner-mcp`, then `/plugin install 0xdesigner@0xdesigner`. Then open `/mcp`, select `plugin:0xdesigner:0xdesigner`, choose **Authenticate** and sign in through your browser. If Claude asks for `/reload-plugins`, run it in the same conversation. Use one of the two setups, not both.

## Claude desktop app (Code tab)

Slash commands are not available to the agent in the desktop app, so paste the connection prompt from https://0xdesigner.com/vending-machine or run these in any shell:

```sh
claude plugin marketplace add 0xdesign/0xdesigner-mcp
claude plugin install 0xdesigner@0xdesigner --scope user
```

The desktop app loads a plugin's tools when a conversation starts. Start a new conversation, type `/mcp`, select `plugin:0xdesigner:0xdesigner`, choose **Authenticate** and sign in through your browser. No app restart is needed.

## Codex app

Add the marketplace, then install from the Plugins tab:

```sh
codex plugin marketplace add https://github.com/0xdesign/0xdesigner-mcp
```

Open [Install 0xdesigner](codex://plugins/install/0xdesigner?marketplace=0xdesigner) after adding the marketplace, then press **Install**. Sign in through your browser when prompted, then return to the same conversation. Codex may ask once or twice to run outside the sandbox; that is normal. If no sign-in was prompted, choose **Authenticate** under Settings → MCP servers.

## Codex CLI

Run this before you start Codex:

```sh
codex mcp add 0xdesigner --url https://0xdesigner.com/mcp
```

A browser tab opens; sign in with your email code and choose Connect. If no browser opens, run `codex mcp login 0xdesigner`. Then start `codex`. Prefer the plugin instead? Add the marketplace as above and install from `/plugins`; Codex CLI 0.154 or newer loads it in the open session, older versions after you run `codex` again. Never use both the plugin and a manual `0xdesigner` entry: one hides the other.

## Check the connection

Ask: **“Use 0xdesigner and check that its tools are ready.”** The agent must discover the native tools and call `browse_menu` with `intent: "connect"`. A configuration entry or endpoint health check alone is not readiness.

Then, while working on a product, say **“Give this to 0xdesigner.”** Your agent drafts a focused design request from the context you approve.

## Your account and privacy

- The plugin contains only a public HTTPS MCP address. No API keys, scripts, hooks or embedded credentials.
- Your MCP host handles browser OAuth sign-in and stores your connection credentials.
- Signing in connects to your existing briefs and credits. It does not purchase credits or share your code.
- Review connections and disconnect agents from [your account](https://0xdesigner.com/vending-machine/account).
- [How the service works](https://0xdesigner.com/vending-machine) · [Privacy](https://0xdesigner.com/privacy)

## Updating

Claude Code: `/plugin marketplace update 0xdesigner`, then `/plugin update 0xdesigner@0xdesigner`. Codex: `codex plugin marketplace upgrade`.

## Upgrading an older test connection

A manually configured server named `0xdesigner` can override the plugin. If you are migrating from the old token setup, remove only that old entry with `codex mcp remove 0xdesigner`, then reinstall the plugin through the native Plugins menu. Keep the same chat open. This does not delete your account, briefs or credits. Do not remove unrelated servers or repeat registration to fix missing tools.

## Shared plugin metadata

Both manifests share the same name, version, description, author, website, repository, keywords and MCP configuration. The Codex `interface` branding is mirrored into Claude Code’s supported `metadata.interface` object, including the bundled X profile picture at `assets/profile.jpg`. Claude Code currently ignores custom metadata and has no documented plugin logo display field, so the shared image is packaged but does not appear in its picker. Keep these fields synchronized when publishing a new version.
