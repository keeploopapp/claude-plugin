# Keeploop Remote for Grok Bot

[Keeploop](https://keeploop.app) is the personal context layer for your AI: a Mac menu bar app
that lets the AI apps you use read your Mail, Calendar, Messages, Notes, Contacts and Slack. This
plugin connects Grok Bot to Keeploop through the hosted connector at
`https://mcp.keeploop.app/mcp`. Your data stays on your Mac, and you choose what Grok Bot can see
and do.

Needs Keeploop Pro or its free trial for remote use; local use is free.

## What it adds

- **The Keeploop tools**: search and read mail, threads and attachments; your calendar and free
  time; iMessage conversations; notes; contacts; Slack; drafts in your voice; sending within
  your permissions; and monitors.
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
| `/keep-settings` | See what the AI can do. Changes are proposed from an AI app on your Mac |
| `/keep-help` | List the commands |

## Requirements

- **The Keeploop app** on an Apple Silicon Mac (macOS 26 or later), signed in, with the sources
  you want turned on. Get it at [keeploop.app](https://keeploop.app). The Mac must be on and
  Keeploop running for Grok Bot to reach your data.
- Keeploop Pro or its free trial (see above).

## Connect

In Grok Bot, open Connect apps, find Keeploop, and add it. Sign in to Keeploop in the window that
opens, then approve Grok Bot on your Mac. Remote apps are Read only until you allow more in
Keeploop. Step by step: <https://keeploop.app/your-ai-apps>.

## What the plugin contains

- `mcp.json`: the address of Keeploop's hosted connector, `https://mcp.keeploop.app/mcp`.
- `skills/keep-*`: the commands, as plain Markdown.

The plugin runs nothing on your computer: no launcher, no hooks, no downloaded code.

## Privacy

Your data stays on your Mac. Keeploop's connection service passes Grok Bot's requests to your
Mac and the results back, and never stores them. In Keeploop you choose which sources and
accounts Grok Bot can see, and for each action whether it is blocked, asks you first on your
Mac, or goes ahead. The connection service keeps account, device and approval records until you
delete them, and security event metadata for 30 days.

The full policy is at <https://keeploop.app/privacy>. Questions: help@keeploop.app.

## Support

- Terms: <https://keeploop.app/terms>
- Support: <https://keeploop.app/support> or help@keeploop.app

## License

The files in this plugin are MIT licensed (see `LICENSE`). The Keeploop app itself is
separate, proprietary software and is not part of this plugin.
