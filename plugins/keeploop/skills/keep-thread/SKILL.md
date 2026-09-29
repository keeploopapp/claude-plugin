---
name: keep-thread
description: "Summarize a whole email conversation: what happened, decisions, open questions."
argument-hint: "<subject or mail id>"
disable-model-invocation: true
---

Summarize an email thread for me, using the Keeploop tools.
Thread: $ARGUMENTS
(If that is empty, ask me for it before calling any tool.)

1. If the thread above is a number, it is a mail_id: call get_thread with that mail_id. Otherwise call search_mail with subject set to it, pick the most recent match, and call get_thread with its mail_id. If several different threads match, list them and ask which one.
2. Call get_email on any message whose snippet is not enough.
Then write: a three-sentence summary; Decisions (bullets, who decided); Open questions (bullets, who owes the answer); and the last message's date and sender.
If a tool is missing, or answers that it needs Keeploop Pro, say so in one line and do what you can with search_mail and get_email instead.
