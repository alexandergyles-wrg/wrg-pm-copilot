---
name: open-loops
description: Your open-loops digest, for the slower stuff, not same-day handoffs (see end-of-day-check for that). Finds threads waiting on someone else (you sent the last message and got no reply), unanswered Question Tracker items, and unfinished work from your recent sessions, ranks them, and surfaces them for triage. Run it in a new chat whenever you want.
---

## GUIDED DELIVERY - one part at a time (always)
Do not present both sections in one dump. Show Section A (Waiting on others) as its own turn led by a one-line intro and let the user triage it, then Section B (Waiting on you) as its own turn. Keep each ranked list bulleted.

## FORMATTING - lists, never paragraphs (always)
Whenever you present more than one item, render them as a bulleted or numbered list, one item per line. Never pack multiple items into a run-on paragraph. A single item may be a sentence; two or more are always a list.

---

You are running the user's **Open Loops** digest. Read `memory/role.md`, `memory/day-to-day.md`, and `memory/engagements.md` first for their chat tools, priority channels, VIPs, work week, timezone, and every active project across every active client. Find the two kinds of open loop and surface them as one ranked digest in this session for triage. Never message the user externally, never post on their behalf. Concise, no em-dashes.

This is the slow-cadence digest, twice a week is the intent, a client who's back in three weeks or a cold outreach thread being nursed along, not a same-day answer. If the user needs a daily check for time-critical handoffs, that's `end-of-day-check`, a different skill.

## SECTION A - Waiting on others (chat + Question Tracker)
Two sources feed this section; run both, across every active project.

**ClickUp Question Tracker (structured, primary).** For every active project in `memory/engagements.md` that has a Question Tracker list, pull every item not in a `complete`-type status. This is a direct signal, not an inference: rank HIGH if it's blocking a deliverable or has sat since before the last run, MEDIUM otherwise. No verification step needed, the list itself is the source of truth.

**Chat, Slack for now (inferred).** Find threads where the user sent the last message with a question, request, or mention and no one has responded. Google Chat isn't swept yet, deliberately, see CLAUDE.md.
- What counts as waiting: the user's message is most recent; it contained a question/request/mention; 24+ hours passed and it isn't clearly resolved; when in doubt, flag it.
- Search a ~21-day window across every active project's channel(s), the user's other priority channels and key DMs (from `memory/day-to-day.md`), plus any currently active channels. Use Slack's search for "messages from the user that end a thread with a question." Tag each result with its client and project: a channel thread by the channel, a DM thread by the counterpart's handle per CLAUDE.md's attribution rule, ask rather than guess when a shared team member matches more than one active project and the thread itself doesn't say which.
- Verify: read each candidate thread. Discard only if someone replied after the user, or the user explicitly closed it.
- Rank: HIGH (senior leadership, explicit deadline, 5+ days, or blocking a deliverable); MEDIUM (cross-functional, 2 to 5 days); LOW (exploratory, under 2 days, no blocker).

Merge both into one ranked list per project; do not double-count a chat thread that's clearly the same question as a Question Tracker row.

## SECTION B - Waiting on you (recent sessions)
Find sessions from the past 7 days with unfinished work. List recent sessions, filter to activity within 7 days, exclude the current one. For each, read the transcript and look for: open todos (a task left pending or in-progress is the strongest signal); uncommitted next steps ("I'll do X next", "want me to also", "ready when you are" with no follow-up); mid-flight stops. Exclude sessions that ended clean, trivial Q&A, or where the user said done. Capture: session ID, one-line topic, last activity (relative), up to 3 open todos or the last proposed step.

## OUTPUT - one part at a time (Section A, then Section B)
```
Open Loops - [date]

Waiting on others ([N])
🔴 [<client> / <project>] #channel - X days · your ask: "[snippet]" · waiting on @person
🟡 ...
🟢 ...

Waiting on you ([N])
1. [topic] - [last activity] · open: [todos, max 3]
2. ...
```
Show top 5 per section if many. Empty section: "nothing waiting". Both empty: "No open loops. You're clear."

Then offer triage:
- Section A per thread: `nudge` (draft a follow-up in the user's voice for them to review and send), `track` (create a personal-board task with a "done when" and "check by" so the loop persists), `snooze`, or `drop`.
- Section B per thread: `continue` (pull it back, surface the todos, be ready to do the work), `track` (create a personal-board task capturing the unfinished work), `done`, `snooze`, or `archive`.

`track` is the bridge from an ephemeral loop to a tracked task: for a Question Tracker item it's already tracked, just confirm it stays open; for a chat-sourced loop, it becomes an item on the personal board (per `memory/day-to-day.md`), set to Inbox or This week per the user's choice, with a "done when" and "check by" so morning-brief's close-check picks it up. Never auto-create these; only on a `track` instruction.

Wait for the user's reply, then act on each. Do not pre-summarize or editorialize before they triage. Nothing sent or closed on their behalf.
