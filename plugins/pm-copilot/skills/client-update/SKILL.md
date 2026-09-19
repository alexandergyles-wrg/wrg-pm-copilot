---
name: client-update
description: Your weekly client-facing project status draft, hours (where billable), risks and blockers, work in progress, upcoming work, plus a separate internal-only efficiency note. Runs per project, only for projects flagged for it in memory/engagements.md. Drafts only, never sends. Run it in a new chat whenever you want.
---

## GUIDED DELIVERY - one part at a time (always)
Present the client draft first, as its own turn, and wait for edits or approval. Only after that, present the internal efficiency note as a second, clearly separate turn. Never merge the two into one message, the whole point of the split is that one of them must never reach a client.

## FORMATTING - lists, never paragraphs (always)
Whenever you present more than one item, render them as a bulleted or numbered list, one item per line.

---

You are running **client-update** for one project. Read `memory/role.md`, `memory/day-to-day.md`, `memory/voice.md`, and `memory/engagements.md` first. This skill runs per project, never bundled across a client's other projects, and only for a project whose entry has `Weekly client update: yes`. If asked to run it for a project set to `no`, say so and stop rather than draft it anyway.

If the project has no `Active sprint list` set and its type is one-time or mixed, stop and flag that gap. Guessing which list is the current sprint is exactly the kind of silent assumption this system doesn't make.

## Hard guardrails
- **The client draft never contains a Time Estimate figure, ever, for any task, adhoc or sprint.** That field is WRG's internal number. The only hours figure a client ever sees is PM Estimated Hours vs. Actual, and only for adhoc/change-request work.
- **A one-time project's sprint work carries no hours line in the client draft**, fixed-scope means there's nothing to show. The internal efficiency note is where sprint hours live, and it is a separate output, not a section of the same message.
- **Risks and blockers are proposed, never asserted as settled fact.** You infer candidates from stale or blocked items; the user confirms, edits, or drops each one before anything is client-ready.
- **Nothing is sent.** This produces a draft and an internal note, both reviewed in this session. Sending is the user's action, on their own account, always.
- Use the external, partnership-framed voice from `memory/voice.md` for the client draft. No absorbed-hours or liability language; if a risk exists because of an internal miss, the client draft frames it as a plan going forward, and the internal note is where the real cause goes.

## STEP 1 - Work in progress and upcoming work
Source: the project's `Active sprint list` for a one-time or mixed project (never Execution Tasks, that list holds project lifecycle tasks, not sprint work). For an adhoc project, source Bugs & Change Requests instead, there's no sprint list to read.
- **Work in progress:** items past "to do" and short of "complete" (in progress, QA, client review, ready to ship).
- **Upcoming work:** items in "to do / planning" on the same list.
Keep both lists to what a client would recognize as a deliverable, not internal ticket-level detail.

## STEP 2 - Hours (client-facing section, adhoc only)
For adhoc or change-request items closed or active since the last report: pull PM Estimated Hours and Actual per item, and the running total against whatever budget has been quoted. Never pull Time Estimate into this step. If the project is one-time with no adhoc work active, omit this section from the client draft entirely, don't show a zero.

## STEP 3 - Risks and blockers (proposed)
Candidates, gathered, not asserted:
- Bugs & Change Requests items waiting on a client decision or estimate approval.
- Unanswered Question Tracker items.
- Anything stuck in one status unusually long, on the active sprint list or Bugs & Change Requests.
Present each with its evidence. The user confirms, edits the framing, or drops it before Step 5.

## STEP 4 - Internal efficiency note (separate, never sent)
For a one-time or mixed project: sum Time Estimate vs. Actual across the active sprint list, same comparison already used for adhoc, applied here to see if the team is tracking to their own estimates and whether the project is running efficiently. If sprint tasks have no Time Estimate filled in, say that plainly rather than showing a false zero, this only works when the team is actually estimating at the task level. For an adhoc-only project, this step is the same comparison already covered in Step 2's internal working numbers; don't duplicate it as a second note.

## STEP 5 - Present, in order
1. The client draft (Work in Progress, Upcoming Work, Hours if adhoc is active, Risks and Blockers as proposed items). Wait for edits or approval.
2. Once the client draft is settled, the internal efficiency note, headed plainly as internal, never to be sent to the client.

```
[Client] / [Project] - Weekly Update, [date]
(client-facing draft, your voice)

Work in progress
- ...

Upcoming
- ...

Hours (adhoc only, omit if none active)
- [item]: [PM Estimated Hours] quoted, [Actual] logged

Risks and blockers (proposed, confirm or edit)
- [item] - [evidence]
```
```
INTERNAL ONLY - not for the client
[Project] - Efficiency, [date]
Sprint Time Estimate vs. Actual: [total estimated] vs. [total logged] ([% variance])
[note if Time Estimate data is missing or thin]
```

Nothing here is written to memory or sent anywhere; both outputs exist only in this session for the user to copy, edit, or send themselves. Because this drafts client-facing messages, `self-improvement`'s Phase 1 draft-not-sent scan picks these up the same as any other client draft, so voice corrections here feed back into `memory/voice.md` over time the same way.
