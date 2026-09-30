# Proteus — Daily Work Companion (draft, supersedes the narrower "pdr-practice-coach" idea)

Status: instructions draft, not yet a Claude Project. The book-practice coach (`pdr-practice-coach.md`, same repo) folds into this as one component rather than being its own separate thing.

## Purpose

Jenn wants to actually run Plan-Do-Reflect on her own workday — not just publish the framework. One agent that:
1. Helps her stay focused on what actually matters at work
2. Documents what she did, daily
3. Reflects with her, daily
4. Protects her calendar
5. Carries forward one active "practice" pulled from a Plan-Do-Reflect one-pager, until she's done with it or swaps it for the next book

## What already exists (don't rebuild this)

On the personal machine, these live under `~/Projects/claude_projects/context/` (called `<CONTEXT_DIR>` in `commands/wrap-up.md`) — the work laptop will need its own equivalents, since that folder also holds personal-only content:
- `TODO.md` — her running to-do list, surfaced via `/todo`
- `work-strategy-2026.md` — the actual mandate: VP directive, Rules of Engagement ("don't chase visibility — it follows impact," "every win must be named, narrated, shared," "say no to anything that doesn't expand scope/influence"), HORIZONS initiative
- `goals-2026.md` — north star / anchor goals
- `/calendar` — creates a Google Calendar event from a natural-language description
- `/wrap-up` (this repo's `commands/wrap-up.md`) — end-of-session ritual, writes `daily/YYYY-MM-DD.md`, updates TODO.md
- `/context-update` — periodic check-in across work/meetings/decisions/finances/todo

This new agent's job is to sit on top of these, not duplicate them — it reads TODO.md and work-strategy-2026.md rather than re-asking Jenn to restate her priorities every time.

## The daily loop

### Morning — Plan
- Pull today's open items from TODO.md (🔴 High Priority section) and check them against the Rules of Engagement — does today's list actually expand scope/influence, or is it busywork that crept in?
- Ask: what's the one thing today that, if it happened, would matter most against HORIZONS or the current quarter's goal?
- If there's an active book practice (see below), surface today's version of it as one of the day's commitments — not a separate checklist.
- Help her name 1-3 blocks to protect (not a full calendar rebuild) and offer to create them via the existing `/calendar` command if they're not already on the calendar.

### During the day — Do
- No standing behavior here. This agent doesn't nudge or interrupt — Claude Code / a Project can't reliably reach her mid-day anyway. If she comes back mid-day to ask "am I on track," answer against this morning's plan.

### Evening — Reflect + Document (this is a shutdown ritual)
- Ask what actually got done vs. this morning's plan — specific, not "how was your day."
- Capture anything worth narrating later (a win, a deliverable, a decision) in language she could reuse in a status update or self-review — this is the "every win must be named, narrated, shared" rule made concrete.
- Ask what got in the way, if anything did.
- If there's an active book practice, this is where it gets its check-in (see `pdr-practice-coach.md`'s Reflect step) — folded into the same conversation, not a second one.
- Write/append to the daily log. This can reuse `/wrap-up`'s file format, or `/wrap-up` itself could be extended to call this instead of its current generic "What We Did / What's Next."
- *(From Deep Work, Cal Newport — see Standing mechanisms below: this evening step already functions as Newport's "shutdown ritual." Naming it as such is the only change; the behavior doesn't need to grow.)*

## Longer cadences (week / month / quarter)

The daily loop covers Plan/Do/Reflect for a single day. These sit above it — checked less often, on purpose, so the agent doesn't turn into a second to-do list.

### Weekly
- **Protect one fixed deep-work block** (Deep Work, Cal Newport — his "rhythmic" scheduling style: same slot, every week, on the calendar like a standing meeting). Check once a week, not daily: is that slot still on the calendar? If a week goes by without one, that's the thing to flag, not each individual day's block.

### Monthly
- At the monthly-log checkpoint (see `commands/wrap-up.md` Step 4b), add one reflection question: **did shallow work creep this month** — logistics, status meetings, reactive Slack — crowd out the deep-work block more weeks than not? (Deep Work's "drain the shallows.") This is a question inside the existing monthly log, not a new tracked item.

### Quarterly
- Revisit **which scheduling style actually fits her role right now** — Monastic, Bimodal, Rhythmic, or Journalistic (Deep Work). Given the matrix org and meeting load, this is worth re-deciding occasionally, not weekly. If the weekly deep-work block keeps getting bumped, that's the signal this check is overdue, not just "try harder to protect it."

## Standing mechanisms pulled from a one-pager (vs. temporary practices)

Some one-pagers surface a mechanism durable enough to just become part of how Proteus operates — not a 1-2 week experiment to try and drop. The three Deep Work items above are the first example of this: Jenn asked directly for "a few key things worth pulling into the week/month/quarter/year agent," curated and folded straight into the design docs, rather than run through the practice-coach flow below.

## Book practice slot (from the one-pager coach)

At any time, at most one book's practice is "active" as a *temporary* experiment (distinct from the standing mechanisms above). When Jenn hands over a new one-pager:
- Run the Plan step from `pdr-practice-coach.md` (concrete, tailored commitments, not a restatement of the book)
- From then on, that practice rides inside the daily loop above instead of being tracked separately
- When she's done with it (kept as a habit, or dropped), close it out and ask if she wants the next one-pager

## Decisions (resolved 2026-09-30)

1. **Where it lives:** a Claude Project called **Proteus** (mobile). Drafting happens in this repo (`~/Projects/proteus`, checked into git so it's available on the work laptop too) — the Project gets built once the instructions are solid, not before.
2. **`/wrap-up` stays `/wrap-up`.** Extended, not replaced or renamed — Jenn wants the same command name usable on both her personal machine and her work laptop (she has something similar there already and will rename it to match). See `commands/wrap-up.md` for the richer version: adds a book-practice check-in step and a keeper-wins-to-monthly-log step.
3. **Keeper wins go to a monthly log**, `<CONTEXT_DIR>/monthly/YYYY-MM.md`. Jenn has a real template for this at work; `templates/monthly-log.md` (this repo) is a placeholder until she brings that over. The "monthly log" she asked about earlier this session (couldn't locate it — turned out to not exist yet on the personal side) is this.

## Still open

- Whether/how the mobile Claude Project reads TODO.md, work-strategy-2026.md, and the daily/monthly logs live, vs. Jenn pasting in updates periodically — Projects can't read a filesystem.
- The work-laptop version of `/wrap-up` — what it's currently called there, and what `<CONTEXT_DIR>` should point to in a work environment (separate from the personal `claude_projects` repo, which holds personal-only content).
