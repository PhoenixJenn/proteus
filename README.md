# Proteus

An agent that helps Jenn actually run Plan-Do-Reflect on her own workday: staying focused on what matters, protecting her calendar, documenting and reflecting daily, and putting the `plan-do-reflect-www` one-pagers into practice one book at a time.

Named after the shape-shifting Greek sea god — the point of this agent is to change how Jenn works, not just track it.

## Status

Design draft. Not yet built as a Claude Project. See `docs/daily-work-companion.md` for the full design and open questions.

## Setup

New to this repo (your own clone, or someone else's)? Start with **`start-here.md`** — it walks through the questions Proteus needs answered (calendar, to-do list, a "second brain" if you don't have one yet, goals/operating principles, review format, interruption sources, first book practice) and builds your machine's `.local/knowledge-index.md` from the answers. Written to work for anyone, not just the original author.

## Layout

- `docs/` — design docs for the agent itself
  - `daily-work-companion.md` — the overall daily-loop design (Plan/Do/Reflect for the workday)
  - `pdr-practice-coach.md` — the book-one-pager-practice component
  - `framework-nuggets.md` — pre-curated "best of" situational frameworks from the one-pagers, for live conversation — curated once per book, not searched live (keeps token cost off every conversation)
  - `delegate-or-decline.md` — a decision flow spanning several one-pagers (core-competency filter, ABCDE tagging, capacity check, actual no-tactics), run both on-demand and proactively during the Weekly Review
  - `habit-formation.md` — how any new habit gets set up (habit stacking, the Four Laws) and diagnosed if it's slipping (Rider/Elephant/Path, Drive's Autonomy/Mastery/Purpose) — wired into the book-practice coach and `/wrap-up`, not a standalone cadence
  - `hard-conversations.md` — a flow for feedback, accountability, and conflict that's already hard (or might become so) — STATE/CRIB, a three-books-deep listening technique, and a difficult-behavior playbook
  - `one-on-ones.md` — the routine, scheduled counterpart: 1:1 structure (another independent three-book convergence), lightweight frequent feedback, task-relevant-maturity delegation, and "no surprises" performance reviews built from material already captured, not written cold
  - `going-live.md` — what actually building this as a Claude Project involves: the custom-instructions/knowledge-file split, the `.local/knowledge-index.md` problem on a filesystem-less Project, which connectors are confirmed working vs. need checking, and the day-to-day usage scenarios
- `commands/` — Claude Code slash commands that support the agent
  - `wrap-up.md` — richer end-of-day ritual (daily log, to-do checkoff, book-practice check-in, keeper-wins-to-monthly-log, captured in SBI/STARR)
- `state/` — generic, empty templates for state the commands read/write once running
  - `pdr-active-practice.md` — template for whichever book's practice is currently active
- `templates/` — reusable templates, sourced from `plan-do-reflect-www`'s own published framework where one exists — public content, not placeholders
  - `monthly-log.md` — the Monthly Log format from Reflection Practice (Core Goals, Growth Goals, Ideas & Open Threads, End-of-Month Wins)
  - `quarterly-review.md` — the Quarterly Review format, explicitly reusable for a quarter/half/full year — also the base shape for mid-year/EOY reviews (Jenn's own extra prompts for those go in `.local/reviews/`, gitignored, once she has them)
  - `sbi.md` / `starr.md` — the site's own accomplishment-capture formats (quick vs. detailed), used to shape keeper wins into material a real performance review can draw from
  - `knowledge-index.example.md` — the shape of the local knowledge index (see below)

## No internal knowledge lives in this repo

Everything above is generic framework — it doesn't know Jenn's actual to-do list, strategy docs, goals, or any other personal/work content. The first time this is used on a machine, it builds a **local knowledge index** (`.local/knowledge-index.md`, copied from `templates/knowledge-index.example.md`) pointing at wherever that machine's real files live, plus real state files like the active book practice and any personal mid-year/EOY review prompts. `.local/` is gitignored — nothing in it should ever be committed here.

## Why a separate repo

This needs to work from both Jenn's personal machine and her work laptop, which is exactly what the framework/`.local/` split above is for — the tracked framework is identical on both machines, and each machine's `.local/knowledge-index.md` points at that machine's own context.
