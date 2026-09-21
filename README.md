# 0xdesigner

Give design work to 0xdesigner from the conversation where you're already building.

This repository contains the **0xdesigner-owned plugin**, distributed directly. It is not an OpenAI- or Anthropic-endorsed marketplace listing.

## Codex

Add this marketplace:

```sh
codex plugin marketplace add https://github.com/0xdesign/0xdesigner-mcp
```

Open **Plugins → 0xdesigner → Install** (or `/plugins` in Codex CLI). Sign in and approve the connection in your browser, then return to the same conversation.

## Claude Code

In your interactive Claude Code conversation:

```
/plugin install 0xdesigner --marketplace 0xdesign/0xdesigner-mcp
```

Sign in through your browser. If Claude requests activation, run `/reload-plugins` in the same conversation.

## Check the connection

Ask: **“Use 0xdesigner and check that its tools are ready.”** The agent must discover the native tools and call `browse_menu` with `intent: "connect"`. A configuration entry or endpoint health check alone is not readiness.

Then, while working on a product, say **“Give this to 0xdesigner.”** Your agent drafts a focused design request from the context you approve.

## Your account and privacy

- The plugin contains only a public HTTPS MCP address. No API keys, scripts, hooks or embedded credentials.
- Your MCP host handles browser OAuth sign-in and stores your connection credentials.
- Signing in connects to your existing briefs and credits. It does not purchase credits or share your code.
- Review connections and disconnect agents from [your account](https://0xdesigner.com/vending-machine/account).
- [How the service works](https://0xdesigner.com/vending-machine) · [Privacy](https://0xdesigner.com/privacy)
