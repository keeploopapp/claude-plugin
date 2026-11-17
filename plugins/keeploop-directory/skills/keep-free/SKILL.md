---
name: keep-free
description: "Open slots on your calendar for a length and a range, for example 30m this week."
disable-model-invocation: true
---

Use the Keeploop tools from whichever Keeploop connector this chat has: the Keeploop extension in the Claude app on my Mac, or Keeploop Remote on the web and phone. If both are there, use the extension. Their names may carry a prefix; use them by their Keeploop name. If no Keeploop connector is available, tell me to turn on the Keeploop extension or Keeploop Remote, and stop.

Find open time on my calendar, using the Keeploop tools.
What I need: (the text I typed after the command)
(If that is empty: 30 minutes in the next five days.)

1. Read the length as duration_minutes (30m is 30, 1h is 60, 90 min is 90; 30 if none is given). Turn the range into ISO dates (YYYY-MM-DD) for start and end, using today's date: today, tomorrow, this week (today through the coming Friday), next week (Monday through Friday), and so on. With no range, leave start and end out. If I name hours or days (mornings, after 2pm, weekends), pass working_hours (for example "09:00-12:00") and days (for example "mon-fri" or "sat,sun"); otherwise leave them out.
2. Call find_free_time with duration_minutes, start, end, limit=10, and working_hours and days when step 1 set them.
Then list the slots grouped by day (day, then start to end time), and say the range searched. If there are none, say so and suggest a wider range or other hours. Do not add or propose events unless I ask.
If a tool is missing, is turned off in Keeploop, or answers that it needs Keeploop Pro, say so in one line and do what you can with the rest.
