# /sprint-update

Part of **Proteus** (`~/Projects/proteus`). Triggers `docs/team-flow-check.md`'s Sprint Update capability. Conditional: only relevant if the user manages or leads an engineering team and an issue tracker is connected — if either isn't true, say so and don't run it.

**Install:** save/symlink to `~/.claude/commands/sprint-update.md` on each machine, same as the other commands.

**Config:** generic, no hardcoded paths. Requires `.local/knowledge-index.md`'s Issue tracker slot filled in (`templates/knowledge-index.example.md`). If that slot is empty because the user doesn't manage an engineering team, this command shouldn't be run at all — if it is anyway, say so plainly rather than guessing at data that doesn't exist.

---

## Steps

### 1. Pull the sprint goal
Read it from the issue tracker if the field exists and is filled in. If it's missing (not every team sets one), say so directly — don't infer or invent a goal from the ticket list.

### 2. Pull what's in the sprint
All tickets, grouped by status: done, in progress, not started, blocked. Read-only — don't modify, comment on, or re-prioritize anything.

### 3. Check alignment, not just completion
Does the actual ticket mix serve the stated goal, or has scope drifted since planning? A sprint can look mostly "done" by ticket count while still missing its actual goal. If this looks like drift, name it as the same finding `team-flow-check.md`'s unplanned-work thief would catch — don't treat it as a separate problem.

### 4. Assess risk explicitly
Time remaining in the sprint vs. work remaining. State plainly whether this is on track, at risk, or already missed — don't just report counts and leave the user to infer it.

### 5. Surface blockers and neglected tickets within the sprint
Same definitions `team-flow-check.md`'s five-thieves check uses for "blocked" and "neglected" — don't redefine them here.

### 6. Route anything that needs it
- A genuine win worth capturing → SBI (`templates/sbi.md`), same mechanism `/post-meeting` uses.
- A new action item surfaced while reviewing → the to-do list's Inbox (`delegate-or-decline.md`'s Capture step).
- Something that needs a real conversation (someone's overloaded, the goal was unrealistic from the start) → flagged for `hard-conversations.md` or `one-on-ones.md`, not resolved here.

### 7. Confirm
A short status, usable directly in a standup or a written update — not a full ticket-by-ticket readout.
