---
description: Run all the PM Co-Pilot workflows once, right now, as a calibration pass. Lets you see real output and fix anything that's off (wrong channels, people, tone) before you rely on them. Run this after /setup.
---

You are running **PM Co-Pilot's first-run calibration**. The point: the user just finished `/setup`, but nothing has run yet, and they have no confidence yet that the system is calibrated to their world. So run the workflows once now, show the output, and let them adjust before they start relying on them.

Read `memory/role.md` and `memory/day-to-day.md` first. Use only connected tools; note any that are skipped.

## What to do
Run the six workflows once each, in this order, presenting each result for review and treating it as a calibration checkpoint (not a live action):

1. **Morning brief** - run it once. Show what it captured, closed, and flagged. Note for the user that this fork runs it twice a day, so a second same-day run correctly showing "nothing new" isn't a bug.
2. **End-of-day check** - run it once. Show what's unanswered and its suggested tags. Remind them the tag is a suggestion only, they set the actual priority every time, this is calibrating, not deciding.
3. **Weekly prep** - run the guided review as if it were the start of the week.
4. **Client update** - if any project is flagged for it, run it once for one such project. Show both the client draft and the internal efficiency note, and make the split between them obvious: one is reviewable-and-sendable, the other never leaves this session. If no project is flagged yet, skip this and say so.
5. **Open loops** - show what's waiting on them and what they're waiting on, twice-a-week cadence, the slower stuff.
6. **Self-improvement** - run the light version: surface any obvious memory gaps or first improvement candidates. The end-of-day-check calibration report will say "no data yet", that's expected on a first run.

## Calibration, not autopilot
For each workflow, after showing the output, ask the calibration question:
- "Do these look like the right channels and people?" (if wrong, update `memory/day-to-day.md` now, with their confirmation)
- "Is this the right level of detail and tone?" (if off, note it to `memory/voice.md`)
- "Anything here that isn't actually yours, or missing a client/project it should have caught?" (fix `memory/engagements.md` or the relevant memory file)

Apply only the corrections they confirm, to memory files only. Do NOT send anything, close anything, or write to their personal board or any project's task tracker during first-run beyond what they explicitly approve; this is a preview to build trust, not a live run.

## Close
Summarize what looked right and what you adjusted. Then tell them: the system is calibrated. Run any workflow whenever you want by opening a new chat and naming it (`morning-brief` for each of its two daily passes, `end-of-day-check` for the third, `weekly-prep`, `client-update` per project, `open-loops`, `self-improvement`, or `sync` then `consolidate`). Run them in a normal chat so they execute on the user's machine with access to their memory folder; Claude's scheduled tasks currently run in the cloud and cannot reach these local files.
