# /wrap-up

Part of **Proteus** (`~/Projects/proteus`). Same command name as before on purpose — Jenn wants one shared workflow across her personal machine and her work laptop, so this stays "wrap-up" rather than getting a new name.

**Install:** save/symlink to `~/.claude/commands/wrap-up.md` on each machine.

**Config:** this command is generic — it carries no hardcoded paths to Jenn's real files. Before first use on a machine, copy `templates/knowledge-index.example.md` to `.local/knowledge-index.md` (gitignored) and fill in the real paths for the to-do list and the daily/monthly log locations. Every reference below to "the to-do list" or "the daily/monthly log" means "wherever `.local/knowledge-index.md` points."

---

## What's new vs. the old `wrap-up`

Steps 1, 2, 3, 5, 6 are unchanged (date/project, daily log, to-do checkoff, confirm, usage push notification). Two new steps inserted before Step 5 (Confirm):

### Step 4a — Book practice check-in
- Read `.local/pdr-active-practice.md` if it exists (gitignored; copy `state/pdr-active-practice.md`, the generic template in this repo, there on first use).
- If there's an active practice: ask what actually happened against its commitments today (specific, not "how'd it go"), what worked, what didn't. Log the answer under that entry.
- **Skipped-twice check** (`docs/habit-formation.md`): if today's the second consecutive day the practice was skipped, say so directly — that's the actual signal, not each individual missed day. If it's genuinely not sticking, run the Rider/Elephant/Path diagnostic (same doc) instead of just asking "why" open-endedly.
- Otherwise, once it's been running long enough to judge (Jenn's call, don't impose a fixed number of days): ask whether to keep it running, adjust it, or retire it. A retired practice moves to the "Retired" section, not deleted.
- If nothing's active: skip silently, don't prompt her to start one — that happens when she hands over a new one-pager (see `docs/pdr-practice-coach.md`), not during wrap-up.

### Step 4b — Monthly log
- From today's "What We Did," ask (or judge, if obviously clear-cut) whether anything qualifies as a keeper win — worth naming, narrating, and sharing later per her strategy/goals context, not just today's routine work.
- If yes: capture it in **SBI** (`templates/sbi.md` — Situation/Behavior/Impact) for a quick win, or **STARR** (`templates/starr.md` — adds Task and a Reflection step) for one substantial enough to want the detail. This is what makes the monthly log doubly useful — not just a record, but material that's already shaped for a self-review or performance conversation when the time comes (see `docs/hard-conversations.md`).
- Append it to **End-of-Month Wins** in this month's log at the path in `.local/knowledge-index.md` (create it from `templates/monthly-log.md` — the real Monthly Log format from `plan-do-reflect-www` — if this month's file doesn't exist yet).
- **Only on the last wrap-up of a calendar month** (or if Jenn asks directly):
  - Ask the Deep Work shallow-work check — did logistics/status meetings/reactive Slack crowd out the protected deep-work block more weeks than not this month? Log it under Ideas & Open Threads (or wherever it best fits that month's entries).
  - Ask The ONE Thing's Focusing Question at month-scope, and check the month's **Core Goals** / **Growth Goals** sections are actually filled in for next month, not just Wins — that's the point of pulling this specific template rather than a generic log.
  - See `docs/daily-work-companion.md` → Longer cadences → Monthly.

## Original steps, unchanged

1. Identify today's date and project (cwd)
2. Write the daily log to the path in `.local/knowledge-index.md` (append if it exists)
3. Update the to-do list (per the knowledge index) if one exists
5. Confirm to Jenn what was written and where, end with one sentence on what's next
6. Send a PushNotification usage reminder
