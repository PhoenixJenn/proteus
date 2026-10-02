# /post-meeting

Part of **Proteus** (`~/Projects/proteus`). Triggers `docs/post-meeting-capture.md` — the fast, numbered check right after any meeting, between `/good-morning` and `/wrap-up` in the daily rhythm rather than tied to either.

**Install:** save/symlink to `~/.claude/commands/post-meeting.md` on each machine, same as the other two.

**Config:** generic, no hardcoded paths. Requires `.local/knowledge-index.md` to exist (needs the to-do list with its Inbox section, the Goals list, and the daily log path). If it doesn't exist yet, point the user at `start-here.md` first.

---

## Steps

### 1. Ask the nine questions, as a numbered list, not a narrative prompt
Speed matters more than completeness right after a meeting — the user answers in order, briefly:

1. **Outcomes** — what was actually decided, and what happened?
2. **Action items** — what's now on someone's plate, and whose?
3. **Goal contribution** — did this meeting actually serve one of the named goals in the Goals list — which one, or none?
4. **Priorities** — does anything here change or confirm what matters most right now?
5. **How do you feel** — any reaction worth naming?
6. **People observations** — anything notable about how people showed up?
7. **Your own presence** — how did you come across; anything to adjust?
8. **A keeper win here?**
9. **Does anything here point toward a harder conversation later?**

### 2. Route each answer — don't just log the list verbatim
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

### 3. Confirm
One line: what got logged, what got routed where, nothing read back in full.
