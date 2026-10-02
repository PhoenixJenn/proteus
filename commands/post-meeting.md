# /post-meeting

Part of **Proteus** (`~/Projects/proteus`). Triggers `docs/post-meeting-capture.md` — the fast, numbered check right after any meeting, between `/good-morning` and `/wrap-up` in the daily rhythm rather than tied to either.

**Install:** save/symlink to `~/.claude/commands/post-meeting.md` on each machine, same as the other two.

**Config:** generic, no hardcoded paths. Requires `.local/knowledge-index.md` to exist (needs the to-do list with its Inbox section, the Goals list, and the daily log path). If it doesn't exist yet, point the user at `start-here.md` first.

---

## Steps

### 1. Identify which day, then which meeting(s)
Default to today. If the user names a different day instead ("catch up on Monday," "I never did Tuesday's standup"), use that day's calendar and daily log instead — this command isn't limited to "right after the meeting that just happened."

- **If the calendar is connected:** pull that day's meetings. Check that day's daily log for which ones already have a capture or a SKIP recorded (see Step 4) and drop those from the list — don't re-ask a meeting that's already been handled. Walk through what's left in chronological order, one meeting at a time, naming each one before asking about it ("Next: the 2pm with Design — outcomes?").
- **If the calendar isn't connected:** ask directly which meeting this capture is for, by name, before asking anything else. Every capture gets attached to a named meeting either way — none of this is left anonymous.

### 2. For each meeting, ask the nine questions — or take SKIP
Speed matters more than completeness right after a meeting. For the meeting currently being walked through, ask in order, briefly — and treat **SKIP** as a complete, acceptable answer for that entire meeting, no justification needed. On SKIP, log it as skipped (Step 4) and move straight to the next meeting.

1. **Outcomes** — what was actually decided, and what happened?
2. **Action items** — what's now on someone's plate, and whose?
3. **Goal contribution** — did this meeting actually serve one of the named goals in the Goals list — which one, or none?
4. **Priorities** — does anything here change or confirm what matters most right now?
5. **How do you feel** — any reaction worth naming?
6. **People observations** — anything notable about how people showed up?
7. **Your own presence** — how did you come across; anything to adjust?
8. **A keeper win here?**
9. **Does anything here point toward a harder conversation later?**

If there's more than one meeting left to walk through, move to the next one after routing (Step 3) and logging (Step 4) the current one — don't batch all the questions for every meeting together.

### 3. Route each answer — don't just log the list verbatim
Per `docs/post-meeting-capture.md`'s routing table:
- **Outcomes** → append to today's daily log (raw material for tonight's `/wrap-up`, not a separate record).
- **Action items** → the user's own go into the to-do list's Inbox (captured, not triaged — `/good-morning` clarifies it next); anything with a live question about whose it is runs through `docs/delegate-or-decline.md`'s full flow right now instead of waiting.
- **Goal contribution** → logged against today's daily log entry for this meeting, so `/wrap-up`'s time-value rollup has a real tag to aggregate tonight instead of reconstructing the day from memory.
- **Priorities** → cross-check against today's Focusing Question (set by this morning's `/good-morning`) — flag if it's changed.
- **Feelings** → named, not journaled, unless the three-EQ-journals habit (`docs/framework-nuggets.md`) is already running.
- **People observations** → carried into how the user handles the next `/one-on-ones`-style conversation or follow-up with that person, not filed away as a one-off.
- **Presence** → a single data point, not acted on here — patterns across several of these get picked up at the Quarterly personal-narrative check (`docs/daily-work-companion.md`).
- **Keeper win** → capture in SBI (`templates/sbi.md`) now, same mechanism `/wrap-up` uses, just triggered by the meeting instead of end-of-day — don't make the user repeat it tonight.
- **Harder conversation flag** → noted for `docs/hard-conversations.md`, run separately and later, not addressed in this capture.

Tag every routed item with which meeting it came from — with more than one meeting walked through in a single run, "an action item" isn't enough context on its own later.

### 4. Log the meeting as handled, then move on
Whether captured or skipped, add one line to that day's daily log so this meeting doesn't get re-asked on a later run: `Meeting: <name> — captured` or `Meeting: <name> — skipped`. This is the only state Step 1's catch-up logic reads, so it has to happen for every meeting walked through, not just the ones with real notes.

### 5. Confirm
One line per meeting walked through this run: captured or skipped. Nothing read back in full.
