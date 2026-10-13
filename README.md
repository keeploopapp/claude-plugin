# Keeploop plugins for Claude Code, Cursor, Gemini CLI, Grok Build and Grok Bot

[Keeploop](https://keeploop.app) is the personal context layer for your AI: a Mac menu bar app
that lets the AI apps you already use read your Mail, Messages, Calendar, Notes and Slack, right
on your Mac. Your data stays on your Mac until an AI app you connect asks for it, and you decide what each AI can see and do.

This repository is the plugin marketplace for Keeploop. It has two plugins:

- `keeploop` runs on your Mac, for Claude Code, Cursor, Gemini CLI and Grok Build. Local use is free.
- `keeploop-remote` is for Grok Bot. It connects through Keeploop's hosted connector at
  `https://mcp.keeploop.app/mcp` and is hidden in the Cursor editor. Needs Keeploop Pro or its
  free trial for remote use; local use is free.

The local plugin adds:

- **The Keeploop tools** (mail, threads and attachments, calendar and free time, messages, notes,
  contacts and Slack, monitors that wake the agent when a reply lands, drafts in your voice).
  They come from the Keeploop app through a small launcher; nothing in this repository reads
  your data itself.
- **The `/keep-` commands**:

| Command | What it does |
|---|---|
| `/keep-today` | Today's schedule, the replies you owe, and today's monitor hits |
| `/keep-free [length and range]` | Open slots on your calendar, for example `/keep-free 30m this week` |
| `/keep-brief [account or category]` | Unread mail, what needs a reply, and today's monitor hits |
| `/keep-reply` | Threads where someone is waiting on you, with a suggested next step each |
| `/keep-thread <subject or mail id>` | Summarize a whole conversation: decisions and open questions |
| `/keep-draft <mail id> <what to say>` | Draft a threaded reply that sounds like you. Saves a draft only |
| `/keep-find <description>` | Find a file someone sent you by describing it |
| `/keep-waiting` | Mail you sent that nobody has answered yet, oldest first |
| `/keep-settings [what to change]` | See what the AI can do, or propose a change for approval on your Mac |
| `/keep-help` | List the commands |

## Requirements

- An Apple Silicon Mac on macOS 26 or later.
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

### Gemini CLI

```
gemini extensions install https://github.com/keeploopapp/claude-plugin
```

The extension runs the same local launcher as the plugin (`gemini-extension.json` and
`GEMINI.md` at the repository root). Restart Gemini CLI, then ask "what needs my reply today?".

### Grok Bot

In Grok Bot, open Connect apps, find Keeploop, and add it (this is the `keeploop-remote`
plugin). Sign in to Keeploop in the window that opens, then approve Grok Bot on your Mac.

### Web and phone AI apps (Claude, ChatGPT, Grok, Poke and others)

The plugin is for AI apps on your Mac. To use Keeploop from claude.ai, ChatGPT (including dots),
grok.com, Poke or any app that can add a custom MCP connector, add this one URL:

```
https://mcp.keeploop.app/mcp
```

Sign in to Keeploop in the window the app opens, then approve the app on your Mac. The same URL
works for every user; it reaches your Mac only after you approve it there. Remote apps are Read
only until you allow more in Keeploop. Web and phone AI apps need Keeploop Pro or its free trial;
the plugin on your Mac works on Free. Step by step for each app:
<https://keeploop.app/your-ai-apps>.

## What the plugin contains

- `plugins/keeploop/server/keeploop-mcp`: a shell launcher that runs the connector inside
  `Keeploop.app` (its signed `Contents/MacOS/keeploop-mcp`). The Keeploop app checks that
  signature and applies your permissions to every call.
- `plugins/keeploop/skills/keep-*`: the commands, as plain Markdown.
- `plugins/keeploop/hooks/hooks.json`: a Claude Code `SessionStart` hook that tells Keeploop
  which session is running, so a monitor can wake the session that asked for it. It does nothing
  when the app is not installed.
- `plugins/keeploop-remote/`: the Grok Bot plugin. Its `mcp.json` holds only the address
  `https://mcp.keeploop.app/mcp`, and it has the same `skills/keep-*`. It runs nothing on your
  computer.
- `.claude-plugin/` and `.cursor-plugin/`: the marketplace manifests.

Nothing in the local plugin makes a network connection, downloads code or installs packages. The
launcher only runs the Keeploop app's connector on your Mac, and that talks to the Keeploop app
over a local connection, so there is no Keeploop server in the path. If you also use Keeploop from
a web or phone AI app, that is a separate connection: your data stays on your Mac, and Keeploop's
connection service passes requests to your Mac and results back. It never stores them. What the
app itself can send, and only when you turn it on, is listed in the
[privacy policy](https://keeploop.app/privacy).

## Privacy Policy

The full policy is at <https://keeploop.app/privacy>. In short:

- **Collection:** this plugin collects nothing. It starts the Keeploop app's connector, which
  reads the Apple Mail data (and any other source you turn on) already on your Mac, only when
  your AI app calls a tool.
- **Use and storage:** results go to the AI app that asked, on your Mac. Keeploop keeps its
  settings and monitors on your Mac only.
- **Sharing:** none. With the plugin there is no Keeploop server in the path. If you also use
  the web and phone URL above, our connection service passes requests to your Mac and results
  back and never stores them.
- **Retention:** the plugin keeps no data. The connection service keeps account, device and
  approval records until you delete them, and security event metadata for 30 days.
- **Contact:** help@keeploop.app

## Support

- Terms: <https://keeploop.app/terms>
- Support: <https://keeploop.app/support> or help@keeploop.app

## License

The files in this repository are MIT licensed (see `LICENSE`). The Keeploop app itself is
separate, proprietary software and is not part of this repository.

This repository is generated from the Keeploop release build; please send changes as issues
rather than pull requests.
