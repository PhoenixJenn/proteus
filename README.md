# Proteus

An agent that helps Jenn actually run Plan-Do-Reflect on her own workday: staying focused on what matters, protecting her calendar, documenting and reflecting daily, and putting the `plan-do-reflect-www` one-pagers into practice one book at a time.

Named after the shape-shifting Greek sea god — the point of this agent is to change how Jenn works, not just track it.

## Status

Design draft. Not yet built as a Claude Project. See `docs/daily-work-companion.md` for the full design and open questions.

## Layout

- `docs/` — design docs for the agent itself
  - `daily-work-companion.md` — the overall daily-loop design (Plan/Do/Reflect for the workday)
  - `pdr-practice-coach.md` — the book-one-pager-practice component
- `commands/` — Claude Code slash commands that support the agent
  - `wrap-up.md` — richer end-of-day ritual (daily log, to-do checkoff, book-practice check-in, keeper-wins-to-monthly-log)
- `state/` — generic, empty templates for state the commands read/write once running
  - `pdr-active-practice.md` — template for whichever book's practice is currently active
- `templates/` — reusable templates
  - `monthly-log.md` — placeholder monthly-log format (swap for Jenn's real work template when she brings it over)
  - `knowledge-index.example.md` — the shape of the local knowledge index (see below)

## No internal knowledge lives in this repo

Everything above is generic framework — it doesn't know Jenn's actual to-do list, strategy docs, goals, or any other personal/work content. The first time this is used on a machine, it builds a **local knowledge index** (`.local/knowledge-index.md`, copied from `templates/knowledge-index.example.md`) pointing at wherever that machine's real files live, plus real state files like the active book practice. `.local/` is gitignored — nothing in it should ever be committed here.

## Why a separate repo

This needs to work from both Jenn's personal machine and her work laptop, which is exactly what the framework/`.local/` split above is for — the tracked framework is identical on both machines, and each machine's `.local/knowledge-index.md` points at that machine's own context.
