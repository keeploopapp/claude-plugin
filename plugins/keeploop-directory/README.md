# Keeploop for Claude

[Keeploop](https://keeploop.app) is a Mac menu bar app that lets Claude read your Mail, Calendar,
Messages, Notes, Contacts and Slack, right on your Mac. This plugin adds the Keeploop connector
and the `/keep-` commands to Claude on the web, in the desktop and phone apps, in Cowork and in
Claude Code. Your data stays on your Mac until an AI app you connect asks for it, and you choose
what Claude can see and do.

## What it adds

- **The Keeploop connector** at `https://mcp.keeploop.app/mcp`: search and read mail, threads
  and attachments; your calendar and free time; iMessage conversations; notes; contacts; Slack.
  Drafts and replies follow your rules on the Mac. It is the same server as the Keeploop
  connector in Claude's directory, so if you add both you get one set of tools.
- **The `/keep-` commands**:

| Command | What it does |
|---|---|
| `/keep-today` | Today's schedule, the replies you owe, and today's monitor hits |
| `/keep-free` | Open slots on your calendar, for example `30m this week` |
| `/keep-brief` | Unread mail, what needs a reply, and today's monitor hits |
| `/keep-reply` | Threads where someone is waiting on you, with a suggested next step each |
| `/keep-waiting` | Mail you sent that nobody has answered yet, oldest first |
| `/keep-thread` | Summarize a whole conversation: decisions and open questions |
| `/keep-draft` | Draft a threaded reply that sounds like you. Saves a draft only |
| `/keep-find` | Find a file someone sent you by describing it |
| `/keep-settings` | See what Claude can do |
| `/keep-help` | List the commands |

## Requirements

- An Apple Silicon Mac on macOS 26 or later, on and running the Keeploop app. Get it at
  [keeploop.app](https://keeploop.app).
- Keeploop Pro or its free trial. Every Pro feature is in the trial.

## Set up

1. Install this plugin, then connect Keeploop when Claude asks and sign in to Keeploop.
2. Approve Claude on your Mac when Keeploop asks.
3. Type `/keep-help`.

New apps start Read only. You can allow drafts, replies and more per account, label and contact
in Keeploop on your Mac.

## Claude Code on the same Mac

This plugin reaches your Mac through Keeploop's connection service. If you use Claude Code on
the Mac where Keeploop runs, the local plugin works on Keeploop Free, and with Pro it does more
than this plugin can: monitors that wake your Claude Code session, sending texts and Slack
messages, and writing notes within your permissions. Install it instead:

```
/plugin marketplace add keeploopapp/claude-plugin
/plugin install keeploop@keeploop
```

## Privacy

Your data stays on your Mac. When Claude uses this plugin, Keeploop's connection service passes
requests to your Mac and results back. It never stores them. One-time and MFA codes are
hidden from results. In Keeploop you choose which sources and accounts Claude can see, and for
each app whether an action is blocked, asks you first on your Mac, or goes ahead. The plugin
itself runs nothing on your computer.

The full policy is at <https://keeploop.app/privacy>. Questions: help@keeploop.app.

## Support

- Terms: <https://keeploop.app/terms>
- Support: <https://keeploop.app/support> or help@keeploop.app

## License

The files in this plugin are MIT licensed (see `LICENSE`). The Keeploop app itself is
separate, proprietary software and is not part of this plugin.
