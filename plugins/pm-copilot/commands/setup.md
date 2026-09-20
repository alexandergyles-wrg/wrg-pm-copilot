---
description: Set up PM Co-Pilot for you. Asks a short set of questions about your tools, your rhythm, and who you are (proposing answers from your connected tools where it can), then writes your routing brain and memory. Run this once, first.
---

You are setting up **PM Co-Pilot** for a new user. Your job: create their personal routing brain and memory from the templates, filled in with their answers. This is the moment the system becomes theirs instead of generic.

## Ground rules
- Ask in small batches, not one giant form. Use AskUserQuestion.
- Every question has a sensible default. Make clear they can accept the default and refine later. Nobody should stall.
- **Recommend, don't interrogate.** Wherever a tool is connected, PROPOSE the answer from real signals and ask the user to confirm or adjust, instead of asking them to type from a blank page. Only ask cold when you have nothing to propose.
- Write only to their chosen workspace folder. Never write outside it. Show what you'll write before writing.

## Step 1 - Locate the workspace
Confirm the folder where their `CLAUDE.md` and `memory/` should live (their main Claude working folder). A fresh, empty folder is perfectly fine and avoids tangling with anything else they run. If unclear, ask. Everything below is written there.

**Before writing anything, check for an existing setup.** If the chosen folder already has a `CLAUDE.md` or a `memory/` folder, stop and tell the user plainly. Do not overwrite it. Give them two options and let them pick before you go on:
- Point setup at a fresh, empty folder instead, so PM Co-Pilot stays separate from what they already run.
- Or walk through their existing `CLAUDE.md` together and fold PM Co-Pilot's routing table and memory files into it, so nothing they rely on is lost.
Only proceed once they have chosen. Never replace an existing routing brain on your own.

## Step 2 - Check what's connected
Quickly note which relevant connectors are actually available in this Cowork (ClickUp, Slack, Google Chat, email, calendar, notes/transcripts, docs). You'll use the connected ones both to propose answers below and to tell the user, at the end, which workflows will be live vs skipped. If a tool they rely on isn't connected, note it and tell them how to connect it (Customize → Connectors) or that the related workflow step will simply be skipped until they do.

## Step 3 - Ask the setup questions (batched, propose-first)
Group into a few short AskUserQuestion rounds. Offer defaults in brackets. For any item marked "propose", do the discovery read first and present your suggestion for confirmation.

**You** (propose name, role, company, email domain, timezone from the account/profile/calendar where possible)
- Name?
- Role / title? [Product Manager]
- Company, in one line of what it does?
- Work email domain?
- Location / timezone? [detect]
- **Manager** (propose from recurring 1:1s on the calendar): "Looks like your manager may be [X], from your recurring 1:1. Right?"
- Primary focus or domain right now?
- What you're working toward (a launch, a metric, a promotion)? [optional]

**Your personal board** (this fork's approach: a real status, not a tag, kept off the project lists)
- Do you already have a private ClickUp list for this? If yes, get its name/space and confirm it, or read its statuses if reachable. If no, offer to walk them through creating one: a private list with four statuses, Inbox (open type), This week (custom), Backlog (custom), Archive (closed type). This is a one-time manual step in ClickUp's list settings, the connector can create the list itself but can't set custom statuses on it; say so plainly rather than attempting it silently.
- Confirm this list is separate from any project's own delivery-status workflow, and that these skills will never write to a project's actual status field.

**Your tools** (for each: name the tool, or "none")
- Chat / messaging tools? Slack is the one this fork actually sweeps (external project channels, client DMs, internal-team DMs). If Google Chat is also in use, note it, but say plainly it isn't swept yet, the schema has a place for it, building the sweep is a later addition, not something setup should imply is already live.
- Email? [e.g. Gmail, Outlook]
- Calendar? [e.g. Google Calendar, Outlook]
- Meeting notes / transcripts? [e.g. Otter, Fireflies, tl;dv, none]
- Docs store? [e.g. Google Drive, Confluence, Notion]
- ClickUp notifications: confirm comments, status changes, and mentions on tasks they're watching or assigned should be swept as their own capture source, separate from the personal board.
- Optional: a personal capture channel (a private chat channel where you toss things for the co-pilot to file). If they want one, note its name/ID; morning-brief will read it.
- What is your company OK with you connecting? (so you never suggest a tool they can't use)

**Your clients and projects** (this fork's core addition - propose, don't ask cold)
- If ClickUp is connected, scan its Spaces/Folders for ones that look like active client work (recent activity, not archived). Group folders that clearly belong to the same client (matching names, e.g. multiple folders under one client's umbrella) and propose a client/project structure: which folders are separate projects under the same client, versus genuinely separate clients. Present to confirm/trim/add rather than asking cold, this grouping is a guess and needs a real confirmation.
- For each confirmed client: ask for client-wide contacts (the person who's the same regardless of which project, with their Slack handle if reachable by DM) and any relationship notes worth keeping, only what you couldn't infer.
- For each confirmed project under that client: which chat tool and channel it uses (guess from name-matching if chat is connected), whether its ClickUp folder follows the standard four-list shape (Execution Tasks, Bugs & Change Requests, Meeting Notes, Question Tracker, note it if so, so open-loops knows Question Tracker is available), project-specific contacts if different from the client-wide ones, internal team, phase, and a one-line context. Get a Slack handle for anyone (client-side or internal) whose updates come by DM rather than the project's ClickUp folder or a shared channel, DM attribution depends entirely on having it. Skip anything they wave off; they can fill it in later.
- If the same person turns up on more than one active project's internal team, don't ask anything extra here, that's derived automatically at runtime from the lists you've already given, not a separate thing to configure.
- **Project type:** ask adhoc, one-time, or mixed for each project. For one-time or mixed, also ask for the current **active sprint list** name, sprint work lives in a list created fresh per sprint, not in Execution Tasks, so this has no safe default to infer.
- **Weekly client update:** ask, per project, whether they want the `client-update` skill available for it. Default to not asking cold for every single project if there are many, propose "none yet" and let them turn it on per project as they're ready, rather than assuming every project wants a weekly draft.
- Ask which clients or projects are paused or wrapping up, so those start in the right section of `memory/engagements.md` rather than Active and don't get swept.
- This feeds every workflow's sweep. Make sure it's genuinely complete before moving on: ask directly, "Is that every active client and project, or are there others?"

**Your key channels and people** (propose, don't ask cold)
- **Priority channels:** start from every channel matched to a project above, since the point of this fork is a full sweep, not a top-N. If chat is connected, also scan the last ~30 days for other channels they post in, are mentioned in, or have starred, and offer those as adds. Present the combined list to confirm/trim. If chat isn't connected, ask for a short list.
- **VIPs (people whose messages always surface):** if chat/calendar is connected, propose frequent DM contacts and recurring 1:1 partners with a one-line reason each ("appears in 8 threads this month"), present to confirm/trim/add. Otherwise ask for a few names.

**Your rhythm** (this fork runs three passes a day by default, because of an overnight team handoff)
- When does your week start? [Monday]
- When do you wrap up / review the week? [Friday afternoon]
- Pass 1, morning-brief, light and client-facing: what time, what timezone? [propose from their stated workday start]
- Pass 2, morning-brief, team catch-up: what time, once overnight updates have mostly landed? [propose ~2 to 2.5 hours after pass 1, confirm]
- Pass 3, end-of-day-check: what time, before the handoff window closes? [ask directly, this is specific to their situation]
- If they don't have an overnight-team handoff situation at all, one daily morning-brief pass is enough, skip pass 2 and end-of-day-check, note that plainly rather than forcing three passes on everyone.
- Any non-working days or holidays to respect?

**Your voice** [all optional]
- General tone? [direct and concise]
- Anything you never do in writing? [e.g. no em-dashes, no emoji]
- Paste 1 to 3 real things you've written, if you want it to sound like you.

## Step 4 - Write the files and create the folders
Copy the plugin's templates into the workspace and fill them from the answers. Create the full folder structure up front so nothing ever fails later with "nowhere to save":
- `CLAUDE.md` from `templates/CLAUDE.md` (adjust the tool references to match their stack; keep the routing table).
- `memory/role.md`, `memory/colleagues.md`, `memory/scope.md`, `memory/day-to-day.md`, `memory/voice.md`, `memory/decisions.md`, `memory/engagements.md` from `templates/memory/`, filled with their answers. Record the personal board's list ID and statuses, the chat tools, and all three pass times in `day-to-day.md`. Record every confirmed client (with its contacts) and every project nested under it (Active, Paused, or Closed) in `engagements.md`. Leave blanks where they skipped; do not invent anything.
- Create these empty so every workflow has a home: `memory/topics/`, `memory/state/`, `memory/context-gaps.md`, `memory/context-watchlist.md`, `memory/skill-improvements.md`, `memory/meeting-prep-recurring.md`, and a `memory/_backups/` folder for the sync/consolidate backups.
Show the user exactly what you're about to write (a short summary per file), then write on their confirmation. Never fabricate a fact they didn't give.

## Step 5 - Point them to the next steps
Confirm what was written, and which workflows will be live vs skipped based on their connected tools. Then tell them:
- Their system is live; from now on Claude reads `CLAUDE.md` and loads the right memory automatically.
- Run `/pm-copilot:first-run` to run all the workflows once right now, see the output, and calibrate.
- After that, run any workflow whenever they want by opening a new chat and naming it: `morning-brief` for each of its two daily passes, `end-of-day-check` for the third, `weekly-prep` at the start of the week, `client-update` per project for any flagged for it, `open-loops` for a twice-weekly sweep, `self-improvement` weekly, `sync` then `consolidate` to refresh memory. Tell them to run these in a normal chat so they execute on their machine with access to this memory folder. Claude's scheduled tasks currently run in the cloud and cannot see local files, so do not schedule these for now.
- They can add topic files under `memory/topics/` any time; `sync` and `consolidate` keep memory current.
- A new project goes straight into `memory/engagements.md`, nested under its client, the moment it kicks off, and moves to Paused or Closed the moment it wraps, so the sweep always matches reality. A brand-new client gets its own client block first.
