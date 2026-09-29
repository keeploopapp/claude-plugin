# Keeploop plugin for Claude Code, Cursor and Grok Build

[Keeploop](https://keeploop.app) is the personal context layer for your AI: a Mac menu bar app
that lets the AI apps you already use read your Mail, Messages, Calendar, Notes and Slack, right
on your Mac. Everything stays on your Mac, and you decide what each AI can see and do.

This repository is the plugin marketplace for Keeploop. The plugin adds:

- **The Keeploop tools** (search mail, read threads and attachments, monitors that wake the agent
  when a reply lands, drafts in your voice). They come from the Keeploop app through a small
  launcher; nothing in this repository reads your mail itself.
- **The `/keep-` commands**:

| Command | What it does |
|---|---|
| `/keep-brief [account or category]` | Unread mail, what needs a reply, and today's monitor hits |
| `/keep-reply` | Threads where someone is waiting on you, with a suggested next step each |
| `/keep-thread <subject or mail id>` | Summarize a whole conversation: decisions and open questions |
| `/keep-draft <mail id> <what to say>` | Draft a threaded reply that sounds like you. Saves a draft only |
| `/keep-find <description>` | Find a file someone sent you by describing it |
| `/keep-waiting` | Mail you sent that nobody has answered yet, oldest first |
| `/keep-help` | List the commands |

## Requirements

- An Apple Silicon Mac on macOS 26 or later, with Apple Mail set up.
- **The Keeploop app**, installed in `/Applications` (or `~/Applications`) and opened once.
  Get it at [keeploop.app](https://keeploop.app). Without the app the plugin's server stops with
  "Keeploop is not installed on this Mac. Install Keeploop from https://keeploop.app ...".

If you already have Keeploop, the easiest route is Keeploop > Settings > Connect, which installs
this plugin for you.

## Install

### Claude Code

```
/plugin marketplace add keeploopapp/claude-plugin
/plugin install keeploop@keeploop
```

Or from a terminal:

```
claude plugin marketplace add keeploopapp/claude-plugin
claude plugin install keeploop@keeploop
```

Restart Claude Code, then type `/keep-help`.

### Cursor

Install **Keeploop** from the Cursor Marketplace in Customize, or add this repository as a
plugin source. The plugin reports itself to Keeploop as Cursor, so Keeploop's per-app rules apply.

### Grok Build

Grok Build reads Claude Code marketplaces, so the Claude Code commands above are all it needs.

## What the plugin contains

- `plugins/keeploop/server/mailroom-mcp`: a shell launcher that runs the connector inside
  `Keeploop.app` (its signed `Contents/MacOS/mailroom-mcp`). The Keeploop app checks that
  signature and applies your permissions to every call.
- `plugins/keeploop/skills/keep-*`: the commands, as plain Markdown.
- `plugins/keeploop/hooks/hooks.json`: a Claude Code `SessionStart` hook that tells Keeploop
  which session is running, so a monitor can wake the session that asked for it. It does nothing
  when the app is not installed.
- `.claude-plugin/` and `.cursor-plugin/`: the marketplace manifests.

Nothing in the plugin makes a network connection, downloads code or installs packages. The
launcher only runs the Keeploop app's connector on your Mac, and that talks to the Keeploop app
over a local connection. What the app itself can send, and only when you turn it on, is listed in
the [privacy policy](https://keeploop.app/privacy).

## Privacy and support

- Privacy: <https://keeploop.app/privacy>
- Terms: <https://keeploop.app/terms>
- Support: <https://keeploop.app/support> or help@keeploop.app

## License

The files in this repository are MIT licensed (see `LICENSE`). The Keeploop app itself is
separate, proprietary software and is not part of this repository.

This repository is generated from the Keeploop release build; please send changes as issues
rather than pull requests.
