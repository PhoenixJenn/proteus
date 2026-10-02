# Team Flow Check

An on-demand (and optionally weekly) mechanism, conditional on two things being true: the user manages or leads an engineering team, and an issue tracker (JIRA, Linear, or similar) is connected. If either isn't true, this mechanism doesn't apply — don't surface it, and don't substitute a generic version for a user without a team. Covers two distinct capabilities on the same gate and connector:

- **The five-thieves flow check** (below) — *why* isn't work flowing, a health diagnostic. Built around the existing "A team's work isn't flowing" nugget (`framework-nuggets.md`, Making Work Visible) run against real data instead of as a mental checklist.
- **Find Your Brent** (below) — *is one specific person the whole team's bottleneck*, a sharper, person-level cut on the same WIP data. Built around the "Find your Brent" nugget (`framework-nuggets.md`, The Phoenix Project / Theory of Constraints).
- **Sprint Update** (`commands/sprint-update.md`) — *is the current sprint on track against what it committed to*, a status check. Different question, same underlying data.

## The five thieves, with what to actually check

(Making Work Visible, Dominica DeGrandis)

1. **Too much work in progress** — the biggest thief, per DeGrandis. Query in-progress ticket counts per person. Flag anyone noticeably over a healthy WIP limit for their role — cross-references the 80% utilization trap already in `delegate-or-decline.md`: the same capacity math, applied to a team instead of to the user's own workload.
2. **Unknown dependencies** — tickets effectively blocked or waiting on another ticket, person, or team, but not visibly flagged as blocked. These are the ones that quietly stall without anyone noticing until someone asks.
3. **Unplanned work** — tickets added to a sprint or board after it started, outside the original plan. A high rate of this is itself the finding — it means the planning process isn't capturing real demand, not that the team is just unlucky this sprint.
4. **Conflicting priorities** — someone assigned across too many different initiatives at once, or multiple tickets simultaneously marked as the top priority. If everything is P1, nothing is.
5. **Neglected work** — tickets with no status change or activity in an extended stretch (the user's own threshold — what counts as "neglected" varies by team and ticket type). Easy to miss because neglected work is, by definition, not making noise.

## What this produces

Not a dashboard dump — a short diagnostic naming which thief (or thieves) is actually active right now, same spirit as `hard-conversations.md`'s diagnosis-before-action principle: know what's actually wrong before prescribing a fix. Each thief implies a different intervention (DeGrandis's own framing) — the fix for too much WIP (cap it) is not the fix for conflicting priorities (force a single ranked list), so naming the right one matters more than a general "things feel busy" read.

## Find Your Brent — a sharper, person-specific cut

(The Phoenix Project, Gene Kim et al. — Theory of Constraints applied to people)

Thief #1 above (too much WIP) is diffuse — it flags when the whole team is overloaded. Find Your Brent is a different, sharper question: has one specific, irreplaceable person quietly become the whole system's single point of failure. A team can clear thief #1's check (everyone's WIP looks reasonable) while still having a Brent, if that one person is the one everyone else's work actually depends on.

1. **Pull per-person activity, not just WIP count** — tickets assigned, but also who's tagged on reviews/approvals, who gets pulled into other people's blocked tickets, who's cited as "ask so-and-so" in ticket comments if that's visible. A high ticket count alone is thief #1; a high *dependency* count — other people's work routing through this one person — is Brent.
2. **Check whether this person is also the unblocker** — the one whose review, sign-off, or specific knowledge is what gets other tickets moving again. This is the qualitative signal the book describes and a raw count won't catch on its own.
3. **Name it plainly if found** — don't soften a real finding into "the team seems busy." If it's one person, say which person and what specifically routes through them. Vague is the failure mode here, same as the rest of this diagnostic.
4. **Don't try to fix it in this check** — protecting or offloading a Brent's load is a real conversation (with the Brent, with whoever's been routing work to them by habit, possibly with the user's own manager about backfill or cross-training), not a ticket re-assignment. Flag it for `one-on-ones.md` or `hard-conversations.md` depending on how direct the fix needs to be.
5. **Check whether the Brent is the user** — the nugget's own closing point (via The 7 Habits of Highly Successful Leaders): sometimes the bottleneck is the user's own approvals, reviews, or decisions gating the team. Different question from the 80% capacity check already in `delegate-or-decline.md` — that one asks "is the user over capacity," this one asks "is the user's own involvement what's gating everyone else," which can be true even at well under 80%.

## Sprint Update — a different question than the five thieves

Triggered as `/sprint-update` (`commands/sprint-update.md`), standalone, any time — not tied to the weekly cadence the way the five-thieves check is, since sprint status is relevant whenever the user wants it, not just once a week.

1. **Pull the sprint goal**, if the tracker has one set (JIRA sprints support a Sprint Goal field; not every tool or team actually fills it in — say so plainly if it's missing rather than inventing one).
2. **Pull what's actually in the sprint** — tickets grouped by status (done / in progress / not started / blocked).
3. **Check alignment**, not just completion: does what's actually in the sprint serve the stated goal, or has scope drifted since planning? A sprint can be 80% "done" by ticket count while missing the goal entirely if the wrong 80% got done. Cross-references the five thieves' unplanned-work check above — scope drift is often the same underlying thing showing up in two places.
4. **Assess risk**, not just status: given time remaining against work remaining, is this sprint actually on track to hit its goal? Flag it plainly if not, rather than reporting ticket counts and letting the user infer risk themselves.
5. **Surface blockers and neglected tickets** inside the sprint specifically, using the same definitions as the five-thieves check above — no need to re-derive what "blocked" or "neglected" means twice.

Produces a short status — usable directly in a standup, a written update, or just the user's own situational awareness before a 1:1 or a conversation with their own manager. If it surfaces something worth capturing as a win, it feeds SBI (`templates/sbi.md`) the same way `/post-meeting` does; if it surfaces a new action item, it goes to the to-do list's Inbox the same way everything else does.

## Read-only, same as calendar/email/messaging

Per `daily-work-companion.md`'s "Takes action" principle: read ticket data directly rather than asking the user to describe their board. Don't comment on, modify, or re-prioritize tickets — this is a diagnostic for the user to act on, not Proteus making changes to a team's tracker on its own initiative. If the connector isn't set up, ask once (same rule as every other capability), don't silently skip or substitute a manual version every time.

## Where this plugs in

- **The five-thieves check and Find Your Brent** — Weekly cadence (`daily-work-companion.md`), conditional alongside the existing "1:1 check, if the user manages people" bullet — same gate, same cadence, run together since all three are reading the same ticket data for different signals. Also runnable on-demand if something feels off mid-week.
- **Sprint Update** — purely on-demand via `/sprint-update`, whenever the user wants a status read, not tied to a cadence.
- Findings that point to a specific conversation (someone's overloaded, priorities are genuinely unclear, a sprint is visibly off track) route into `hard-conversations.md` or `one-on-ones.md` rather than being resolved in this check itself.

## Still open

No issue-tracker connector confirmed available as of this writing (checked alongside email and messaging — neither JIRA nor a generic issue-tracker tool showed up). Whether this ends up as JIRA specifically, a more generic connector, or something the user has to paste summaries of manually is undetermined — see `going-live.md`.
