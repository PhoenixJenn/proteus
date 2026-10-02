# Post-Meeting Capture

A fifth cross-cutting mechanism, on-demand right after any meeting — not a cadence check. Triggered as `/post-meeting` (`commands/post-meeting.md`), the counterpart to `/good-morning` and `/wrap-up` for the moment in between. Identified as a gap during a live role-play test: none of the other four flows (`delegate-or-decline.md`, `habit-formation.md`, `hard-conversations.md`, `one-on-ones.md`) actually cover "I just left a meeting, help me capture what matters before it fades." This one composes pieces from all of them rather than inventing new mechanics — its job is routing, not new content.

## Which meeting this is actually for

This never runs anonymously — every capture is attached to a named meeting. Per `daily-work-companion.md`'s "Takes action" principle: if the calendar is connected, read that day's meetings directly rather than asking the user to remember and name each one.

- **Calendar connected:** pull the day's meetings (today by default, or a different day if the user names one — this isn't limited to running right after the meeting that just happened), check that day's daily log for which already have a capture or a SKIP logged, and walk through only what's left, one meeting at a time, in order.
- **Calendar not connected:** ask which meeting this is for, by name, before anything else.

**SKIP is a complete, acceptable answer** for any meeting in the walk-through — no justification required. It still gets logged (as skipped, not as unprocessed) so it isn't re-asked next time.

**Catching up on prior meetings:** since this is anchored to a day's calendar rather than only "the meeting that just ended," it also covers getting busy and falling behind — name an earlier day and it walks through whatever that day's calendar shows that hasn't already been captured or skipped. The daily log is what makes this safe to re-run without duplicating anything.

## The prompt

Once a specific meeting is identified, delivered as a short numbered list the user can answer quickly, not an open-ended narrative ask — speed matters more than completeness right after a meeting:

1. **Outcomes** — what was actually decided, and what happened?
2. **Action items** — what's now on someone's plate, and whose? (Anything not the user's own runs through `delegate-or-decline.md`'s full flow since it's already a named decision, not a fresh capture; anything that is theirs goes into the to-do list's **Inbox** — captured now, clarified and prioritized at the next Morning Plan, not decided on the spot.)
3. **Goal contribution** — did this meeting actually serve one of the named goals in `.local/knowledge-index.md`'s Goals list — which one, or none? A direct tag against a real name, not a vibe-check, and it's allowed to be "none."
4. **Priorities** — does anything here change or confirm what matters most right now?
5. **How do you feel** — any reaction worth naming (frustrated, energized, uneasy, relieved)?
6. **People observations** — anything notable about how people showed up: engaged, checked out, pushback, something unspoken? (Baseline-then-deviation and SCARF, both in `framework-nuggets.md`, are the lenses for this one.)
7. **Your own presence** — how did you come across? Gravitas, communication, read of the room (Executive Presence nugget, `framework-nuggets.md`) — anything you'd adjust next time?
8. **A keeper win here?** — captured in SBI (`templates/sbi.md`) if yes, not just noted in passing.
9. **Does anything here point toward a harder conversation later?** — flagged for `hard-conversations.md`, not addressed in the moment the notes are being taken.

## Where each answer actually goes

- **Outcomes** → the daily log (done-list, per `daily-work-companion.md`'s Evening Reflect) — this is raw material for that, not a separate record.
- **Action items** → the to-do list's Inbox if it's the user's own (captured, not yet triaged — `delegate-or-decline.md`'s Capture/Clarify/Organize note); `delegate-or-decline.md`'s full flow right now if there's a live question about whether it's theirs at all.
- **Goal contribution** → logged against the daily log entry for this meeting, specifically so Evening Reflect's time-value rollup (`daily-work-companion.md`) has real tags to aggregate instead of reconstructing the day from memory at night.
- **Priorities** → cross-check against the day's Focusing Question (`daily-work-companion.md`, Morning Plan) — if it's changed, that's worth knowing before the day's plan goes stale.
- **Feelings** → no separate record unless it's substantial; the point is naming it, not journaling it, unless the three-EQ-journals habit (`framework-nuggets.md`) is already running.
- **People observations** → informs how the user handles any 1:1 or follow-up with that person (`one-on-ones.md`), not filed away as a one-off.
- **Their own presence** → the quarterly personal-narrative/brand check (`daily-work-companion.md`, Quarterly) is where a pattern across several of these would actually get acted on — a single meeting's answer here is just a data point, not a verdict.
- **Keeper win** → `templates/sbi.md`, same as `/wrap-up`'s existing keeper-wins step — this is actually the same mechanism, just triggered by a meeting instead of end-of-day.
- **Harder conversation flag** → `hard-conversations.md`, run separately and later, not in the heat of capturing notes.

Every routed item carries which meeting it came from — necessary once a single run can walk through several meetings in one pass. Separately, whichever meeting was just handled (captured or skipped) gets one line in the daily log recording that — this is the only state the catch-up logic above reads, so it has to be written for a SKIP just as much as for real notes.

## What this isn't

Not a transcript or a full meeting-minutes system — it's a fast sort, done once right after the meeting while it's still fresh, that routes each piece to wherever it was always going to need to go.
