# Going Live — From Design Docs to a Running Claude Project

Everything else in `docs/` is the framework. This is the one doc about actually standing it up as something Jenn talks to day to day, and what that's like to use once it exists.

## What goes where in a Claude Project

A Project has two inputs: **custom instructions** (always in context, short) and **project knowledge** (files Claude reads as needed, can be larger). Proteus maps onto that split naturally:

- **Custom instructions** — a condensed pointer, not the full framework restated: "You are Proteus, Jenn's daily work companion. Read the attached docs for the full framework (daily loop, cadences, Delegate or Decline, Habit Formation, Hard Conversations, One-on-Ones, Post-Meeting Capture, the nuggets library). Read `.local-equivalent` knowledge content from [wherever it ends up, see below] before answering anything that needs her real context." Short because it's always-loaded; everything else is retrieval.
- **Project knowledge** — every file currently in `docs/` and `templates/`, uploaded as-is. This repo was written to be read directly, not rewritten for this purpose.

## The knowledge-index problem, actually solved

`.local/knowledge-index.md` assumes a filesystem Proteus can read on demand. A Claude Project has no filesystem — project knowledge files are static uploads, not live reads. Two real options, not mutually exclusive:

1. **Paste at the start of a session.** Jenn pastes her current to-do list / whatever's relevant into the conversation when she opens it. Zero setup, goes stale the moment the conversation ends, has to be redone every time. Fine for occasional use (Delegate or Decline, Hard Conversations — on-demand flows that only need the one thing she brings), bad for anything that's supposed to run as a standing rhythm (Morning Plan, Weekly Review).
2. **A live document Claude can actually read, not a static upload.** If Jenn's to-do list and goals context live somewhere Claude has standing read access to (a connected Google Doc, a connected Drive folder), the Project can pull current state instead of a stale snapshot. This is the real fix for Morning Plan et al. to work as designed — worth setting up before relying on the daily/weekly cadences, not after.

Calendar and email don't have this problem the same way — they're reached through a live connector, not a project-knowledge upload (see below).

## Connectors — what's actually confirmed vs. what needs checking

- **Google Calendar: confirmed working.** This environment has it connected right now; read and write both tested earlier (checked a real week, found it was the wrong calendar — personal, not work — which is itself the thing to get right when this moves to wherever the real work calendar lives).
- **Email: not available in this environment.** No Gmail/email tool showed up when checked just now. The Morning Plan step that scans email since the last wrap-up is written into the framework, but whether it actually runs depends on what connector gets enabled on the account the real Claude Project uses — check claude.ai's own connector settings when building it, don't assume it'll just work because Calendar does.
- **To-do list / strategy context:** depends entirely on option 2 above (a connected live document) vs. option 1 (paste it each time). Decide this before leaning on the daily cadence.

## Usage scenarios — what this actually looks like day to day

Short version of each. Morning Plan and Post-Meeting Capture (#1 and #8) have both already been role-played live in a real session to test the framework before it's a Project — the rest are designed but not yet tested the same way.

1. **Morning Plan**, daily — to-do list + calendar + urgent email since last wrap-up, then the Focusing Question, then a protected block if the day's answer needs one. *(Role-played live — worked as designed.)*
2. **A live Delegate or Decline call** — a new ask lands, Jenn brings it mid-day, gets a decision and (if declining) the actual phrasing to use.
3. **Prepping for a 1:1** — pull up `one-on-ones.md`'s structure, check task-relevant maturity for what's on that person's plate, decide which feedback tool fits what came up this week.
4. **A hard conversation she's dreading** — bring the situation, get the diagnosis (what-happened / feelings / identity), the right voicing tool (STATE, or just the everyday script if it's not that heavy), and the listening technique.
5. **Evening wrap-up** — currently a Claude Code slash command (desktop-only, see `commands/wrap-up.md`). On mobile via the Project, this would need to be a conversational equivalent — worth deciding whether that's a second, lighter version or just "have this conversation with the Project before bed."
6. **Handing over a new book one-pager** — `pdr-practice-coach.md`'s Plan step runs, a practice gets set up through Habit Formation's setup checks, and it rides inside the daily loop from then on.
7. **Weekly Review** — GTD-style system check + Delegate or Decline run across the whole list + the deep-work block confirmed or re-created.
8. **Post-Meeting Capture** — right after a meeting, a fast numbered check (see `post-meeting-capture.md`) that routes outcomes, action items, priorities, feelings, people observations, her own presence, a keeper win, and any harder-conversation flag to wherever each actually belongs. *(Role-played live — this is how the mechanism got identified as a gap and built in the first place.)*

## Still open

- Whether wrap-up becomes a Project-native conversational flow or stays Code-only and the Project just reads what it produced.
- Where the live to-do-list/goals document actually lives, and whether Drive (or equivalent) gets connected to the Project before or after the first real week of use.
