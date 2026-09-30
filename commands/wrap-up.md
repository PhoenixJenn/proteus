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
- If it's been running long enough to judge (Jenn's call, don't impose a fixed number of days): ask whether to keep it running, adjust it, or retire it. A retired practice moves to the "Retired" section, not deleted.
- If nothing's active: skip silently, don't prompt her to start one — that happens when she hands over a new one-pager (see `docs/pdr-practice-coach.md`), not during wrap-up.

### Step 4b — Monthly log: keeper wins
- From today's "What We Did," ask (or judge, if obviously clear-cut) whether anything qualifies as a keeper win — worth naming, narrating, and sharing later per her strategy/goals context, not just today's routine work.
- If yes: append to this month's log at the path in `.local/knowledge-index.md` (create it from `templates/monthly-log.md`, in this repo, if this month's file doesn't exist yet).
- `templates/monthly-log.md` is a generic placeholder — Jenn has a real template at work she hasn't brought over yet. Use the placeholder as-is until she swaps it in; don't invent structure beyond what it has.
- **Only on the last wrap-up of a calendar month** (or if Jenn asks directly): ask the Deep Work shallow-work check — did logistics/status meetings/reactive Slack crowd out the protected deep-work block more weeks than not this month? Log the answer under that month's file. See `docs/daily-work-companion.md` → Longer cadences → Monthly.

## Original steps, unchanged

1. Identify today's date and project (cwd)
2. Write the daily log to the path in `.local/knowledge-index.md` (append if it exists)
3. Update the to-do list (per the knowledge index) if one exists
5. Confirm to Jenn what was written and where, end with one sentence on what's next
6. Send a PushNotification usage reminder
