# Keeploop for Claude Code and Cowork

[Keeploop](https://keeploop.app) is a Mac menu bar app that lets Claude read your Mail, Calendar,
Messages, Notes, Contacts and Slack, right on your Mac. This plugin connects Claude Code and
Cowork to it. Your data stays on your Mac until an AI app you connect asks for it, and you choose what Claude can see and do.

## What it adds

- **The Keeploop tools**: search and read mail, threads and attachments; your calendar and free
  time; iMessage conversations; notes; contacts; Slack. With Pro, also drafts in your voice,
  sending within your permissions, and monitors that wake Claude when a reply lands. The tools
  come from the Keeploop app through a small launcher; nothing in this plugin reads your data
  itself.
- **The `/keep-` commands**:

| Command | What it does |
|---|---|
| `/keep-today` | Today's schedule, the replies you owe, and today's monitor hits |
| `/keep-free [length and range]` | Open slots on your calendar, for example `/keep-free 30m this week` |
| `/keep-brief [account or category]` | Unread mail, what needs a reply, and today's monitor hits |
| `/keep-reply` | Threads where someone is waiting on you, with a suggested next step each |
| `/keep-waiting` | Mail you sent that nobody has answered yet, oldest first |
| `/keep-thread <subject or mail id>` | Summarize a whole conversation: decisions and open questions |
| `/keep-draft <mail id> <what to say>` | Draft a threaded reply that sounds like you. Saves a draft only |
| `/keep-find <description>` | Find a file someone sent you by describing it |
| `/keep-settings [what to change]` | See what Claude can do, or propose a change for approval on your Mac |
| `/keep-help` | List the commands |

If another plugin already uses one of these names, type it as `/keeploop:<name>`, for example
`/keeploop:keep-today`.

## Requirements

- An Apple Silicon Mac on macOS 26 or later.
- **The Keeploop app**, installed in `/Applications` (or `~/Applications`) and opened once.
  Get it at [keeploop.app](https://keeploop.app). In the app, turn on the sources you want
  Claude to use. Without the app the plugin's server stops with "Keeploop is not installed on
  this Mac. Install Keeploop from https://keeploop.app ...".

## Install

If you already have Keeploop, the easiest route is Keeploop > Settings > Connect, which installs
this plugin for you.

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

### Cowork

In the Claude desktop app, open Customize > Plugins and add Keeploop from the directory, or
choose Add > Add marketplace and enter `keeploopapp/claude-plugin`. The Keeploop tools load
when the Cowork session runs on the Mac where Keeploop is installed.

## Free and Pro

Keeploop Free searches and reads every source, finds free time on your calendar, and keeps
your permissions per app. Keeploop Pro, a one-time purchase, adds drafts and threaded replies,
sending email, texts and Slack messages within your permissions, creating notes, monitors,
reply tracking (used by `/keep-today`, `/keep-reply` and `/keep-waiting`), your voice profile, and web and
phone AI apps. Every Pro feature is in the free trial. Details:
<https://keeploop.app/pricing#compare>.

## Privacy

Your data stays on your Mac. The plugin's launcher runs the Keeploop app's connector, which
talks to the app over a local connection, so there is no Keeploop server in the path. In
Keeploop you choose which sources and accounts Claude can see, and for each app whether an
action is blocked, asks you first on your Mac, or goes ahead. The plugin itself makes no
network connection, downloads no code and collects nothing.

The full policy is at <https://keeploop.app/privacy>. Questions: help@keeploop.app.

## Claude on the web and phone

This plugin is for Claude on your Mac. To use Keeploop from claude.ai or the Claude phone app,
add the Keeploop connector with this URL: `https://mcp.keeploop.app/mcp`. Web and phone use
needs Pro or a trial. Step by step: <https://keeploop.app/your-ai-apps>.

## Support

- Terms: <https://keeploop.app/terms>
- Support: <https://keeploop.app/support> or help@keeploop.app

## License

The files in this plugin are MIT licensed (see `LICENSE`). The Keeploop app itself is
separate, proprietary software and is not part of this plugin.
