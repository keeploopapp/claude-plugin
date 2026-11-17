---
name: keep-waiting
description: "Mail you sent that nobody has answered yet, oldest first, with a nudge suggestion."
disable-model-invocation: true
---

Use the Keeploop tools from whichever Keeploop connector this chat has: the Keeploop extension in the Claude app on my Mac, or Keeploop Remote on the web and phone. If both are there, use the extension. Their names may carry a prefix; use them by their Keeploop name. If no Keeploop connector is available, tell me to turn on the Keeploop extension or Keeploop Remote, and stop.

Show me what I am waiting on other people for, using the Keeploop tools.

1. Call awaiting_reply with direction="them" (default days=7).
Then list each thread, oldest first: who I wrote to, subject, when I sent it, and whether a nudge makes sense now. Include each mail_id. Do not draft nudges unless I ask.
If a tool is missing, or answers that it needs Keeploop Pro, say so in one line and do what you can with search_mail and get_email instead.
