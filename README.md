# PM Co-Pilot (WRG fork, multi-client, overnight-team edition)

Forked from Daniel Blum's [PM Co-Pilot](https://github.com/IamBlum/pm-copilot), featured on [How I AI with Claire Vo](https://www.youtube.com/watch?v=p2qmX6TM0kw). All credit for the original design (the routing brain, the memory model, the core workflows, the self-improvement loop) goes to that repo. This fork changes what happens when your job isn't one product roadmap worked by one company in one timezone, it's several concurrent client engagements, and an engineering team on the other side of the clock.

## Who this is for

Delivery or PM work at an agency, specifically: several clients running at once, some clients running more than one project at once, and a team (engineering, in this case) that works while you sleep and sleeps while you work. If any of that doesn't apply, most of this fork's additions won't either, upstream's version is the better starting point.

## What's different from upstream, and why

**Clients and projects, not one board.** `memory/engagements.md` is a two-tier registry: a client block (contacts, relationship notes, general channel, all persistent) contains one or more project blocks (its own ClickUp list, its own chat tool and channel, its own phase, its own contacts). Every workflow sweeps every active project, not a rotating top few, a client with three live projects gets all three checked. Closed clients and closed projects are kept as real short records, never compressed to one line, because agency clients come back.

**A personal board that's a real status, not a tag.** The stock system assumes your task tracker's own status field doubles as your personal weekly triage (Inbox/This Week/Backlog/Archive). This fork's ClickUp reality has a real, already-automated delivery workflow per project (ten stages, QA gates, client-review gates), so personal triage lives on its own dedicated private ClickUp list instead, four statuses, Inbox (open type), This week (custom), Backlog (custom), Archive (closed type). Nothing here ever writes to a project's actual delivery status.

**Two chat tools, tracked per project.** Some clients use Slack, some use Google Chat. `memory/engagements.md` records which one each project actually uses, and every sweep checks the right one.

**ClickUp itself is a capture source, not just where the board lives.** Comments, status changes, and mentions on watched or assigned tasks get swept the same way chat and email do.

**A weekly client-facing status draft, per project, opt-in.** `client-update` produces a client-ready draft (work in progress, upcoming work, and hours where billable) plus a completely separate internal-only efficiency note, for exactly one project per run, only when that project's `memory/engagements.md` entry says so. Two corrections came out of building this against the real ClickUp template: sprint work for a one-time (fixed-scope) project lives in a list created fresh per sprint, not in Execution Tasks (that list holds the project's lifecycle bookends: startup, the PM's own logged time, go-live, closure), so each project now records its current `Active sprint list`; and hours have three faces, only one of which a client ever sees. Time Estimate is the team's raw internal guess and never reaches a client draft, under any circumstance. PM Estimated Hours is the padded number actually quoted, and that's what shows up against Actual, for adhoc and change-request work only. A one-time project's fixed-scope sprint work carries no hours line in the client draft at all, there's nothing to show them, but Time Estimate vs. Actual on that same work still gets tracked, for WRG's own profitability and estimating accuracy, in the internal note that never leaves the session.

**Three passes a day, not one, because of the overnight handoff.** The team is offline during the workday and their updates land in a window at its start; anything left unanswered by day's end costs a full day, not a few hours.
- **Morning-brief, pass 1 (light, client-facing):** early, before most team updates land.
- **Morning-brief, pass 2 (team catch-up):** later, once they mostly have. Same skill, same logic, it only reports what's new since pass 1, a quiet second pass correctly says so.
- **End-of-day-check (new skill):** a dedicated sweep before the handoff window closes. Finds anything unanswered, tags it relay-critical or routine as a suggestion, and logs the suggestion next to whatever priority you actually pick. This is a deliberate learning period: the tag never decides anything on its own, `self-improvement` reports weekly on how often it would have been right, and whether to ever trust it outright is a separate, explicit decision, not something the system escalates to.

**Open-loops stays upstream's cadence, twice a week**, for the slower stuff a same-day check isn't for: a client who's back in three weeks, a cold-outreach thread being nursed along. It's not the tool for the handoff problem, end-of-day-check is.

**Consolidate has one exception to its normal instinct.** Its default (fold the takeaway forward, drop the rest) is right for a finished feature at a single-product company. It's wrong for a closed client who might re-engage next year, so this fork carves that case out: closed client and project history is archived, never dropped. The append-only logs (morning-brief's audit trail, end-of-day-check's tag-vs-decision log) get a 90-day rollup instead, that detail has no ongoing use once self-improvement has already reported on it.

Everything else, the routing brain's session protocol, the writing-voice defaults, memory-keeper, sync, and improve, is unchanged from upstream.

## What you need

- Claude Cowork (this fork hasn't been run under Claude Code, though nothing here should block it).
- ClickUp connected, plus Slack and/or Google Chat, plus email and calendar.
- A private ClickUp list for the personal board, created once, by hand, in ClickUp's own settings. The connector can create a bare list, it can't set custom statuses on one, so this one step happens outside Claude before `/setup`.

## Install

> Install by URL, not by downloading a ZIP. Push this folder to your own GitHub repo first (private is fine), then add *that* repo as the marketplace.

1. Push this repo to your own GitHub account, e.g. `github.com/<you>/wrg-pm-copilot`.
2. In ClickUp, create a private list with four statuses: Inbox (open type), This week (custom), Backlog (custom), Archive (closed type). Note its name and space.
3. In Claude Cowork: **Customize > Plugins > Add marketplace**, paste your repo's link.
4. Find **PM Co-Pilot** and click **Install**.
5. Open a new chat and run **`/pm-copilot:setup`**. It'll ask for your personal list from step 2, your active clients and their projects (grouped, not flat), each project's type (adhoc, one-time, or mixed) and current sprint list where relevant, which ones want a weekly client-update draft, which chat tool each project uses, and your three daily times.
6. Run **`/pm-copilot:first-run`** to see all six workflows once and fix anything that's off before you rely on them.

## Running it

Open a new chat and name the workflow: `morning-brief` (run it at both of your daily times), `end-of-day-check` (once, before the handoff window closes), `weekly-prep` (start of week), `client-update` (per project, only where flagged), `open-loops` (twice a week), `self-improvement` (weekly), `sync` then `consolidate` (every couple of weeks). Same limitation as upstream: Claude's scheduled cloud tasks can't reach local memory yet, so these are run by hand for now.

## License

MIT, same as upstream.
