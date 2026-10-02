# /good-morning

Part of **Proteus** (`~/Projects/proteus`). The morning counterpart to `/wrap-up` — implements `docs/daily-work-companion.md`'s Morning Plan, plus the Weekly cadence items that didn't otherwise have a trigger point.

**Install:** save/symlink to `~/.claude/commands/good-morning.md` on each machine, same as `/wrap-up`.

**Config:** generic, no hardcoded paths. Requires `.local/knowledge-index.md` to exist (see `templates/knowledge-index.example.md` — needs the to-do list with its Inbox section, the Goals list, calendar, email, messaging, and daily/monthly log paths filled in) and `.local/last-checked.md` (copy `state/last-checked.md` on first use — same file `/whats-new` reads and updates). If the knowledge index doesn't exist yet, point Jenn at `start-here.md` instead of guessing at her context.

---

## Steps

### 1. Process the Inbox
Per `docs/delegate-or-decline.md`'s Capture → Clarify → Organize: read the to-do list's Inbox section. For each item captured since the last `/good-morning` (or since yesterday's, if this is the first run):
- If it would take less than two minutes, just do it now (or confirm it's done) rather than triaging it.
- Otherwise run it through the Delegate or Decline flow (ABCDE tag, strength/capacity check, operating-principles check) and move it into the main to-do list with its tag, or resolve it as a decline per that doc.
The Inbox should be empty, or close to it, before moving to Step 2.

### 2. Check the calendar
Per "Takes action" in `docs/daily-work-companion.md`: read real availability directly. Don't ask Jenn to describe her day.

### 3. Run `/whats-new`
Call `commands/whats-new.md`'s Steps 1-4 (email + messaging, since each channel's own last-checked timestamp in `.local/last-checked.md`, not a fuzzy "since the last wrap-up" boundary). Anything that's an action item lands in the Inbox the same way — if that pulls anything new into the Inbox, loop back through Step 1 for just that item before continuing.

### 4. Pull today's open items
From the now-current to-do list (Step 1 already cleared the Inbox into it). Check them against whatever operating principles the strategy/goals context defines — does today's list actually move the needle, or is it busywork that crept in?

### 5. The Focusing Question
With the to-do list, calendar, and today's `/whats-new` results already in view (not before): what's the one thing today that, if it happened, would matter most against her current goals (`.local/knowledge-index.md`'s Goals list)? If there's an active book practice (`.local/pdr-active-practice.md`), surface today's version of it as one of the day's commitments here, not as a separate checklist.

### 6. Protect the block
If the Focusing Question's answer needs a protected block and one isn't already on the calendar, create it directly (per "Takes action") rather than just naming candidate times.

### 7. Weekly cadence — only on the first `/good-morning` of the week, or if Jenn asks directly
See `docs/daily-work-companion.md` → Longer cadences → Weekly for the full detail on each of these:
- **Protect the standing deep-work block** for the week if it's not already on the calendar (distinct from Step 6's daily block).
- **The Focusing Question at week-scope.**
- **The Weekly Review** (GTD system-hygiene pass) + **Delegate or Decline run across the whole to-do list**, not just today's items.
- **1:1 check**, if Jenn manages people: confirm each direct's 1:1 is actually on the calendar for the week.

### 8. Confirm
One line on what's in today's plan and what, if anything, got resolved from the Inbox or the weekly pass. No full recap read back to her.
