---
name: end-of-day-check
description: A daily sweep run once, near the end of your workday, for anything unanswered before an overnight team handoff window closes. Tags each item relay-critical or routine as a suggestion; you decide the actual priority. Distinct from open-loops, which runs twice a week for slower stuff. Run it in a new chat whenever you want.
---

## GUIDED DELIVERY - one part at a time (always)
Present the tagged list as one part, wait for the user to set priorities, then close. Do not fold this into morning-brief's output or run it back to back with a morning-brief pass without a pause.

## FORMATTING - lists, never paragraphs (always)
Whenever you present more than one item, render them as a bulleted or numbered list, one item per line. Never pack multiple items into a run-on paragraph.

---

You are running the user's **end-of-day check**. This exists for one specific risk: the user's workday ends, an overnight team's day begins, and anything left unanswered at that boundary costs the team a full day rather than a few hours. Read `memory/role.md`, `memory/day-to-day.md`, and `memory/engagements.md` first, for the handoff window's timing, both chat tools, and every active project. Never message anyone externally; this is a review the user acts on themselves.

This is not a lighter morning-brief. It has its own high-water mark (`memory/state/end-of-day-check-hwm.json`), separate from morning-brief's, and its own question (what needs a reply before the window closes), not morning-brief's (what happened, what's done, what's today).

## STEP 1 - Capture what's unanswered since the last run
Across both chat tools (whichever each active project actually uses, per `memory/engagements.md`) and email: messages sent to the user, from a team member or a partner/client, where the user hasn't replied. Same underlying signal as morning-brief's "DMs where the other person sent last", but read fresh from this skill's own high-water mark, and framed around the handoff rather than the day.

Tag which client and project each item belongs to, same as morning-brief.

## STEP 2 - Tag each item, learning period (propose only, never decide)
For each unanswered item, suggest one tag:
- **Relay-critical:** answering it (or not) determines whether the overnight team can proceed, e.g. the team asked a question that blocks their next task, or a client gave an answer the team is waiting on.
- **Routine:** no handoff-timing pressure either way.

State the one-line reason for the guess. This tag is always a suggestion. The user sets the actual priority themselves, every time, this skill never assigns priority on its own. This is deliberate: the tag is being calibrated, not trusted yet.

## STEP 3 - Log the suggestion against the decision
Append one line per item to `memory/state/end-of-day-check-log.md`: `[YYYY-MM-DD] item · suggested: <relay-critical|routine> · decided: <what the user actually picked>`. This is silent housekeeping, never shown in the output. `self-improvement` reads this weekly to report how often the suggestion matched the decision; that report is informational only, changing the tagging behavior itself is a separate, explicit decision the user makes later, not something this skill escalates to on its own.

## OUTPUT
```
End-of-day check - [date]

[N] unanswered since last check
1. [<client> / <project>] <item> - <source> · <link> - suggested: relay-critical (<why>)
2. [<client> / <project>] <item> - <source> · <link> - suggested: routine (<why>)
...

Set priority for each (or "same for all"):
```
If nothing's unanswered: `End-of-day check - [date]: nothing outstanding.` Empty runs still log nothing, there's nothing to compare.

## STEP 4 - Apply
Whatever priority the user sets, either add the item to the personal board (Inbox or This week, per their choice) with a "done when" and "check by" of tomorrow morning, or leave it untracked if the user says it's already handled. Never send anything on the user's behalf; if they want a reply drafted, offer that as a follow-up, not part of this skill's default output.
