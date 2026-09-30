# /wrap-up

Part of **Proteus** (`~/Projects/proteus`). Same command name as before on purpose — Jenn wants one shared workflow across her personal machine and her work laptop, so this stays "wrap-up" rather than getting a new name.

**Install:** save/symlink to `~/.claude/commands/wrap-up.md` on each machine.

**Config (machine-specific — set this before installing):** this command reads/writes `<CONTEXT_DIR>/daily/`, `<CONTEXT_DIR>/monthly/`, and `<CONTEXT_DIR>/TODO.md`. On the personal machine `<CONTEXT_DIR>` = `~/Projects/claude_projects/context`. On the work laptop it needs its own value (probably not the same folder, since that one holds personal-only content like finances/house-decision notes) — set it there when this gets installed. Everything else this command needs (`state/`, `templates/`) lives inside this Proteus repo itself, so it's identical on both machines.

---

## What's new vs. the old `wrap-up`

Steps 1, 2, 3, 5, 6 are unchanged (date/project, daily log, TODO.md checkoff, confirm, usage push notification). Two new steps inserted before Step 5 (Confirm):

### Step 4a — Book practice check-in
- Read `state/pdr-active-practice.md` (this repo).
- If there's an active practice: ask what actually happened against its commitments today (specific, not "how'd it go"), what worked, what didn't. Log the answer under that entry.
- If it's been running long enough to judge (Jenn's call, don't impose a fixed number of days): ask whether to keep it running, adjust it, or retire it. A retired practice moves to the "Retired" section, not deleted.
- If nothing's active: skip silently, don't prompt her to start one — that happens when she hands over a new one-pager (see `docs/pdr-practice-coach.md`), not during wrap-up.

### Step 4b — Monthly log: keeper wins
- From today's "What We Did," ask (or judge, if obviously clear-cut) whether anything qualifies as a keeper win — the Rules of Engagement bar from her work-strategy context: worth naming, narrating, and sharing later, not just today's routine work.
- If yes: append to `<CONTEXT_DIR>/monthly/YYYY-MM.md` (create it from `templates/monthly-log.md`, in this repo, if this month's file doesn't exist yet).
- `templates/monthly-log.md` is a placeholder — Jenn has a real template at work she hasn't brought over yet. Use the placeholder as-is until she swaps it in; don't invent structure beyond what it has.

## Original steps, unchanged

1. Identify today's date and project (cwd)
2. Write the daily log to `<CONTEXT_DIR>/daily/YYYY-MM-DD.md` (append if it exists)
3. Update `TODO.md` in the current project if one exists
5. Confirm to Jenn what was written and where, end with one sentence on what's next
6. Send a PushNotification usage reminder
