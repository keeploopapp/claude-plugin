---
name: keep-draft
description: "Draft a threaded reply that sounds like you. Saves a draft only; never sends."
argument-hint: "<mail id> <what to say>"
disable-model-invocation: true
---

Draft a reply in my voice, using the Keeploop tools.
Message: mail_id $0
What the reply should say: everything after the mail_id in: $ARGUMENTS
(If the mail_id or what to say is missing, ask me for it before calling any tool.)

1. Call get_email with that mail_id and read the whole message.
2. Call get_voice_profile with sender set to the address I received it on (my account's address) and to set to the person I am replying to. Follow its greeting, sign-off, length and tone.
3. Write the reply body, then call save_reply_draft with mail_id and body. Leave allow_paste at its default so Mail keeps the quoted original. Use reply_all=true only if the other recipients need to see it.
4. Show me the draft text and say it is saved in Mail's Drafts for me to review.
Do not send mail unless the user asked you to send it. Nothing is sent unless they allow it: Keeploop checks their permissions and may ask them on their Mac first. If a tool is missing, or answers that it needs Keeploop Pro, say so in one line and do what you can with search_mail and get_email instead.
