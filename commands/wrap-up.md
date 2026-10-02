# /wrap-up

Part of **Proteus** (`~/Projects/proteus`). Meant to be one shared workflow across a personal machine and a work laptop, so it stays "wrap-up" as a name rather than getting a different one per machine.

**Install:** save/symlink to `~/.claude/commands/wrap-up.md` on each machine.

**Config:** this command is generic — it carries no hardcoded paths to the user's real files. Before first use on a machine, copy `templates/knowledge-index.example.md` to `.local/knowledge-index.md` (gitignored) and fill in the real paths for the to-do list and the daily/monthly log locations. Every reference below to "the to-do list" or "the daily/monthly log" means "wherever `.local/knowledge-index.md` points."

---

## What's new vs. the old `wrap-up`

Steps 1, 2, 3, 5, 6 are unchanged (date/project, daily log, to-do checkoff, confirm, usage push notification). Three new steps inserted before Step 5 (Confirm):

### Step 2a — Time-value rollup
- If any meetings happened today, pull their goal-contribution tags from `docs/post-meeting-capture.md`'s Step 3 (did each one actually serve a goal, or none).
- Ask how the day's time actually split — how much served a real goal, how much didn't. Not a guilt exercise; the point is the same one 168 Hours and Christensen's resource-allocation finding make (`docs/framework-nuggets.md`): actual priorities are revealed by where time went, not by what was intended.
- If a specific meeting type keeps tagging "none" more than once, flag it as a candidate for the next Weekly Review (`docs/delegate-or-decline.md`) or the Quarterly trigger audit (`docs/daily-work-companion.md`) — don't just note it and let it repeat.

### Step 4a — Book practice check-in
- Read `.local/pdr-active-practice.md` if it exists (gitignored; copy `state/pdr-active-practice.md`, the generic template in this repo, there on first use).
- If there's an active practice: ask what actually happened against its commitments today (specific, not "how'd it go"), what worked, what didn't. Log the answer under that entry.
- **Skipped-twice check** (`docs/habit-formation.md`): if today's the second consecutive day the practice was skipped, say so directly — that's the actual signal, not each individual missed day. If it's genuinely not sticking, run the Rider/Elephant/Path diagnostic (same doc) instead of just asking "why" open-endedly.
- Otherwise, once it's been running long enough to judge (the user's call, don't impose a fixed number of days): ask whether to keep it running, adjust it, or retire it. A retired practice moves to the "Retired" section, not deleted.
- If nothing's active: skip silently, don't prompt the user to start one — that happens when they hand over a new one-pager (see `docs/pdr-practice-coach.md`), not during wrap-up.

### Step 4b — Monthly log
- From today's "What We Did," ask (or judge, if obviously clear-cut) whether anything qualifies as a keeper win — worth naming, narrating, and sharing later per the user's strategy/goals context, not just today's routine work.
- If yes: capture it in **SBI** (`templates/sbi.md` — Situation/Behavior/Impact) for a quick win, or **STARR** (`templates/starr.md` — adds Task and a Reflection step) for one substantial enough to want the detail. This is what makes the monthly log doubly useful — not just a record, but material that's already shaped for a self-review or performance conversation when the time comes (see `docs/hard-conversations.md`).
- Append it to **End-of-Month Wins** in this month's log at the path in `.local/knowledge-index.md` (create it from `templates/monthly-log.md` — the real Monthly Log format from `plan-do-reflect-www` — if this month's file doesn't exist yet).
- **Only on the last wrap-up of a calendar month** (or if the user asks directly):
  - Ask the Deep Work shallow-work check — did logistics/status meetings/reactive Slack crowd out the protected deep-work block more weeks than not this month? Log it under Ideas & Open Threads (or wherever it best fits that month's entries).
  - Ask The ONE Thing's Focusing Question at month-scope, and check the month's **Core Goals** / **Growth Goals** sections are actually filled in for next month, not just Wins — that's the point of pulling this specific template rather than a generic log.
  - See `docs/daily-work-companion.md` → Longer cadences → Monthly.

## Original steps, unchanged

1. Identify today's date and project (cwd)
2. Write the daily log to the path in `.local/knowledge-index.md` (append if it exists)
3. Update the to-do list (per the knowledge index) if one exists
5. Confirm to the user what was written and where, end with one sentence on what's next
6. Send a PushNotification usage reminder
