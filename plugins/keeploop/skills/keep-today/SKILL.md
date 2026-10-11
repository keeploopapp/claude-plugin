---
name: keep-today
description: "Today's schedule, the replies you owe, and today's monitor hits, in one short view."
disable-model-invocation: true
---

Show me my day, using the Keeploop tools.

1. Call list_events with start and end both set to today's date (YYYY-MM-DD) to get today's events.
2. Call awaiting_reply with direction="me" and days=2 to find threads waiting on me.
3. Call list_monitors, then check_monitor with limit=100 for each active monitor. Hits come oldest first: while a call returns 100 hits, call it again with since_hit_id set to the last_hit_id it returned. Keep the hits from today.
Then write three short sections. Schedule: each event's time, title and location, oldest first; mark events that are over, and flag overlaps or back-to-back meetings. Replies owed: sender, subject and mail_id, most urgent first, at most five. Monitor hits: the monitor's name and what arrived. Leave out a section that is empty and say "Nothing on today" if all three are.
If a tool is missing, is turned off in Keeploop, or answers that it needs Keeploop Pro, say so in one line and do what you can with the rest.
