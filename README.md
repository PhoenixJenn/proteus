# Proteus

An agent that helps you actually run Plan-Do-Reflect on your own workday: staying focused on what matters, protecting your calendar, documenting and reflecting daily, and putting the `plan-do-reflect-www` one-pagers into practice one book at a time.

Named after the shape-shifting Greek sea god — the point of this agent is to change how you work, not just track it.

## Status

Design draft. Not yet built as a Claude Project. See `docs/daily-work-companion.md` for the full design and open questions.

## Setup

New to this repo (your own clone, or someone else's)? Start with **`start-here.md`** — it walks through the questions Proteus needs answered (calendar, email, messaging, to-do list with an Inbox section, a "second brain" if you don't have one yet, a named goals list, operating principles, review format, first book practice) and builds your machine's `.local/knowledge-index.md` and `.local/last-checked.md` from the answers. Written to work for anyone, not just the original author.

## Layout

- `docs/` — design docs for the agent itself
  - `daily-work-companion.md` — the overall daily-loop design (Plan/Do/Reflect for the workday)
  - `pdr-practice-coach.md` — the book-one-pager-practice component
  - `framework-nuggets.md` — pre-curated "best of" situational frameworks from the one-pagers, for live conversation — curated once per book, not searched live (keeps token cost off every conversation)
  - `delegate-or-decline.md` — a decision flow spanning several one-pagers (core-competency filter, ABCDE tagging, capacity check, actual no-tactics), run both on-demand and proactively during the Weekly Review
  - `habit-formation.md` — how any new habit gets set up (habit stacking, the Four Laws) and diagnosed if it's slipping (Rider/Elephant/Path, Drive's Autonomy/Mastery/Purpose) — wired into the book-practice coach and `/wrap-up`, not a standalone cadence
  - `hard-conversations.md` — a flow for feedback, accountability, and conflict that's already hard (or might become so) — STATE/CRIB, a three-books-deep listening technique, and a difficult-behavior playbook
  - `one-on-ones.md` — the routine, scheduled counterpart: 1:1 structure (another independent three-book convergence), lightweight frequent feedback, task-relevant-maturity delegation, and "no surprises" performance reviews built from material already captured, not written cold
  - `post-meeting-capture.md` — a fast, numbered post-meeting check (outcomes, action items, priorities, feelings, people observations, your own presence, a keeper win, a harder-conversation flag) that routes each answer to wherever it belongs rather than being its own record. Found as a gap during a live role-play test, not sourced from a book.
  - `team-flow-check.md` — conditional on managing an engineering team with an issue tracker connected: the five-thieves-of-time health diagnostic (Making Work Visible), Find Your Brent's person-specific bottleneck check (The Phoenix Project), and Sprint Update's goal-alignment/risk check — three questions on the same data, not the same question three times
  - `going-live.md` — what actually building this as a Claude Project involves: the custom-instructions/knowledge-file split, the `.local/knowledge-index.md` problem on a filesystem-less Project, which connectors are confirmed working vs. need checking, and the day-to-day usage scenarios
- `commands/` — Claude Code slash commands that support the agent
  - `good-morning.md` — Morning Plan: processes the Inbox, checks calendar, runs `/whats-new`, asks the Focusing Question, protects a block — plus the Weekly cadence (Weekly Review, Delegate or Decline across the whole list, 1:1 calendar check, Team Flow Check) on the week's first run
  - `whats-new.md` — checks email and messaging since each channel's own last-checked timestamp (`state/last-checked.md`), not a fuzzy boundary; standalone, runnable any time, and the actual implementation `/good-morning` calls rather than duplicating
  - `post-meeting.md` — walks today's calendar meeting by meeting (or a named prior day, to catch up if time got away) asking the nine-question check, SKIP always acceptable, routed to the Inbox, the daily log, SBI, or `hard-conversations.md` depending on the answer — the on-demand trigger in between `/good-morning` and `/wrap-up`
  - `sprint-update.md` — conditional, same gate as Team Flow Check: sprint goal alignment, what's actually in the sprint, and an explicit on-track/at-risk call, standalone any time rather than tied to a cadence
  - `wrap-up.md` — richer end-of-day ritual (daily log, time-value rollup, book-practice check-in, keeper-wins-to-monthly-log, captured in SBI/STARR)
- `state/` — generic, empty templates for state the commands read/write once running
  - `pdr-active-practice.md` — template for whichever book's practice is currently active
  - `last-checked.md` — template for the per-channel last-checked timestamps `/whats-new` and `/good-morning` read and update
- `templates/` — reusable templates, sourced from `plan-do-reflect-www`'s own published framework where one exists — public content, not placeholders
  - `monthly-log.md` — the Monthly Log format from Reflection Practice (Core Goals, Growth Goals, Ideas & Open Threads, End-of-Month Wins)
  - `quarterly-review.md` — the Quarterly Review format, explicitly reusable for a quarter/half/full year — also the base shape for mid-year/EOY reviews (your own extra prompts for those go in `.local/reviews/`, gitignored, once you have them)
  - `sbi.md` / `starr.md` — the site's own accomplishment-capture formats (quick vs. detailed), used to shape keeper wins into material a real performance review can draw from
  - `knowledge-index.example.md` — the shape of the local knowledge index (see below)

## No internal knowledge lives in this repo

Everything above is generic framework — it doesn't know your actual to-do list, strategy docs, goals, or any other personal/work content. The first time this is used on a machine, it builds a **local knowledge index** (`.local/knowledge-index.md`, copied from `templates/knowledge-index.example.md`) pointing at wherever that machine's real files live, plus real state files like the active book practice and any personal mid-year/EOY review prompts. `.local/` is gitignored — nothing in it should ever be committed here.

## Why a separate repo

This is meant to work from more than one machine (a personal laptop and a work laptop, for instance), which is exactly what the framework/`.local/` split above is for — the tracked framework is identical on every machine, and each machine's `.local/knowledge-index.md` points at that machine's own context.
