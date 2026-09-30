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
  - `wrap-up.md` — richer end-of-day ritual (daily log, TODO checkoff, book-practice check-in, keeper-wins-to-monthly-log)
- `state/` — small state files the commands read/write
  - `pdr-active-practice.md` — whichever book's practice is currently active
- `templates/` — reusable templates
  - `monthly-log.md` — placeholder monthly-log format (swap for Jenn's real work template when she brings it over)

## Why a separate repo

This needs to work from both Jenn's personal machine and her work laptop, unlike `claude_projects` (personal-only content: finances, house decisions, etc. — not going to a work git repo). `commands/wrap-up.md` reads Jenn's actual daily/TODO/work-strategy context from a machine-specific `<CONTEXT_DIR>` (see that file) — only the design docs, commands, state, and templates in *this* repo are meant to be identical on both machines.
