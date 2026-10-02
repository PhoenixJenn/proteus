<!-- TEMPLATE — copy this to .local/knowledge-index.md (gitignored) on each machine
     and fill in the real paths. Proteus's framework docs and commands reference
     these slots generically; this file is where the actual pointers live, once
     per machine, never committed. -->

# Knowledge Index (local — not tracked in git)

## To-do list
Path: <absolute path to your to-do list on this machine>
Format: should have an **Inbox** section (newly captured, not yet clarified or prioritized) separate from the main prioritized list — see `docs/delegate-or-decline.md`'s Capture step. If your to-do list doesn't already have this split, add one; it's what keeps new items from either getting lost or dumped into the real list untriaged.

## Goals list
A short, named list — not a vague mission statement. This is what `docs/post-meeting-capture.md`'s goal-contribution tag and the daily Focusing Question (`docs/daily-work-companion.md`) actually tag against, so it needs real names, not a paragraph of context.
Path: <...>
e.g.:
- Goal A: <name>
- Goal B: <name>
- Goal C: <name>

## Strategy / goals context
What it covers: <mandate, operating principles, current initiatives, north-star goals>
Path(s): <...>
(This is the broader context the Goals list above sits inside — operating principles and mandate, not the goals themselves.)

## Calendar tool
Read (checking real availability): <e.g. a connected Google/Outlook calendar tool, or "not connected — ask before proceeding">
Write (creating/moving events): <e.g. a connected calendar tool, or "not connected — ask before proceeding">
Notes: <anything Proteus should know about how to use it here — which calendar(s), any tool name/command>

If either isn't connected on this machine, Proteus should ask Jenn for permission/setup once — not silently fall back to just suggesting times in chat forever.

## Email tool
Read (scanning for anything urgent): <e.g. a connected email tool, or "not connected — ask before proceeding">
Notes: <which account/inbox, any tool name/command>

Read-only by design — `/whats-new` and `/good-morning` use this to surface anything new or urgent since the last check (`state/last-checked.md` / `.local/last-checked.md`), not to triage the whole inbox or take any action (reply, archive, flag) on Proteus's own initiative. If not connected, ask once rather than silently skipping the check every time.

## Messaging tool
Read (scanning for anything new): <e.g. a connected Teams/Slack tool, or "not connected — ask before proceeding">
Notes: <which workspace/channels matter most, any tool name/command>

Same read-only rule as email — `/whats-new` and `/good-morning` surface what's new since the last check, nothing gets replied to or marked read on Proteus's own initiative. If not connected, ask once.

## Daily log
Path: <CONTEXT_DIR>/daily/YYYY-MM-DD.md

## Monthly log
Path: <CONTEXT_DIR>/monthly/YYYY-MM.md
Template: ../templates/monthly-log.md (generic placeholder) or a real one if you have it

## Any other standing context worth the agent knowing about
<...>
