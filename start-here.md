# Start Here

Proteus is a framework for a Claude-based daily work companion — Plan/Do/Reflect for your actual workday, not just a productivity philosophy site. This repo (`docs/`, `commands/`, `templates/`, `state/`) is generic on purpose: it doesn't know anything about you yet. This file is how you fix that.

Read `README.md` first if you haven't — it explains the framework/`.local/` split this setup process builds on.

## How setup works

Everything Proteus needs to know about *you* — your calendar, your to-do list, your goals, where your notes live — goes in `.local/knowledge-index.md`, a file that's gitignored so it never leaves your machine. You build it once per machine (personal laptop, work laptop, etc. each get their own) by answering the questions below, either by hand or by having Claude walk you through them.

## Starter prompt

Paste this into a fresh conversation with Claude, in this repo:

> I'm setting up Proteus for the first time on this machine. Walk me through the setup questions in `start-here.md` one at a time, wait for my answer before moving to the next, and at the end write my answers into `.local/knowledge-index.md` (copying the shape from `templates/knowledge-index.example.md`). If I don't have something a question asks about, help me set up a minimal version of it instead of skipping it.

## Setup questions

Claude should ask these one at a time, in order — later questions build on earlier answers.

**1. Calendar.** What calendar do you use (Google, Outlook, other)? Is there a way for Claude to actually read/write to it in this environment (a connected calendar tool), or does that need setting up? If it can't be connected right now, say so plainly — Proteus should ask permission before assuming it has calendar access, not silently fall back to just suggesting times.

**2. To-do list.** Where do you keep your to-do list today? If you don't have one, this is the point to start one — a plain `TODO.md` somewhere is enough; Proteus doesn't need anything fancier.

**3. Do you have a "second brain" already?** A notes system, journal, personal wiki, or context repo — anywhere you already keep running notes about your goals, decisions, and what you're working on. If yes, where. If no: this is worth building even a minimal version of before going further — Proteus works by reading what's already written down, not by replacing your judgment with its own memory. A minimal version is just a folder with a `daily/` subfolder for day-by-day notes and one file for your goals/priorities — doesn't need to be more than that to start.

**4. Strategy / goals context.** Do you have anything written down about your priorities, goals, or operating principles (a mission statement, OKRs, a set of rules you hold yourself to)? If not, sketch a short one now — a few sentences on what you're actually trying to accomplish and one or two principles you want decisions checked against (Proteus's Delegate-or-Decline flow and daily Plan step both lean on this).

**5. Monthly / quarterly review format.** Proteus ships with generic Monthly Log and Quarterly Review templates (`templates/monthly-log.md`, `templates/quarterly-review.md`) sourced from the Plan-Do-Reflect framework. Use those as-is, or do you already have your own format? If your own: keep the real one wherever it lives, and note its path/shape in the knowledge index rather than copying it into this repo (it's likely specific enough to count as personal/work content, not generic framework).

**6. Messaging and email — interruption sources.** What do you use for chat (Slack, Teams, etc.) and email? Proteus doesn't have a live tool connection to these yet, but naming them now means the quarterly external-trigger audit (see `docs/daily-work-companion.md`) has something concrete to actually audit instead of a vague "notifications."

**7. First book practice (optional).** Is there a specific Plan-Do-Reflect one-pager you want to start applying right away (see `docs/pdr-practice-coach.md`), or do you want to hold off until the rest of the setup is in place?

## After setup

Once `.local/knowledge-index.md` exists, Proteus's daily/weekly/monthly/quarterly behavior in `docs/daily-work-companion.md` should work end to end — it reads everything through that file rather than needing to be told your context again each time.

If you're setting this up on a second machine, repeat this whole process there — the tracked framework is identical, but `.local/` is per-machine on purpose.
