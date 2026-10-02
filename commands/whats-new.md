# /whats-new

Part of **Proteus** (`~/Projects/proteus`). Standalone, run any time during the day — not tied to the morning/evening rhythm. The actual implementation of the email/messaging check; `/good-morning` calls this rather than duplicating it.

Built because staying on top of several communication channels throughout the day is genuinely hard, and a fuzzy boundary like "since the last wrap-up" isn't precise enough — this command tracks a real last-checked timestamp per channel so nothing gets missed and nothing gets re-scanned.

**Install:** save/symlink to `~/.claude/commands/whats-new.md` on each machine, same as the other three.

**Config:** generic, no hardcoded paths. Requires `.local/knowledge-index.md`'s Email tool and Messaging tool slots, and `.local/last-checked.md` (gitignored; copy `state/last-checked.md`, the template in this repo, there on first use).

---

## Steps

### 1. Read the last-checked timestamps
From `.local/last-checked.md` — one per channel (Email, Messaging). If a channel shows `_never_`, use the start of today as the boundary instead of scanning back indefinitely; say so, don't silently guess.

### 2. Check each connected channel since its timestamp
- **Email** — read-only scan for anything new since Email's last-checked time. Surface what's actually notable or time-sensitive, not a full unread count or a line-by-line list.
- **Messaging (Teams/Slack/etc.)** — same, since Messaging's last-checked time.
- If a channel isn't connected on this machine, say so and ask for permission/setup once — don't silently skip it every time (same rule as calendar and email already in `docs/daily-work-companion.md`'s "Takes action" section).

### 3. Summarize, don't transcribe
One short section per connected channel: what's actually worth knowing, not everything that arrived. Anything that's clearly an action item goes into the to-do list's Inbox per `docs/delegate-or-decline.md`'s Capture step, same as `/post-meeting` does — don't just read it aloud and leave it to be forgotten.

### 4. Update the timestamps
Write the current time to `.local/last-checked.md` for each channel actually checked. A channel that wasn't connected (and so wasn't checked) keeps its old timestamp — don't mark it checked if it wasn't.

### 5. Confirm
One line: what's new, what got routed to the Inbox, which channels (if any) still aren't connected.

## Relationship to `/good-morning`

`/good-morning`'s Step 3 (email check) should call this command's Steps 1-4 rather than re-implementing them — one source of truth for "what's new since last checked," whether it's triggered standalone mid-day or as part of the morning routine. If `/good-morning` already ran `/whats-new` today, a later standalone run just picks up from whatever the timestamp now is — no double-counting, no gaps.
