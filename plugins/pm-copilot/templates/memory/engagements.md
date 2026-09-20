# Engagements

The registry of every client and their projects. This is what makes the workflows sweep everything instead of watching one board: every workflow reads this file first and treats each **active project** as its own sweep unit, its own ClickUp list, its own chat tool and channel, its own contacts.

Two tiers, on purpose. A client can run several projects at once, or one project can end while the relationship continues. Client-level facts (who the main contact is, how they like to work) shouldn't have to be repeated per project, and a project's own facts (its ClickUp list, its phase, who's actually on it) shouldn't have to wait for the whole client relationship to change.

A project only leaves the sweep by being moved to Paused or Closed, deliberately, usually during weekly-prep's standing-initiatives review. Nothing drops out from going quiet. Closed projects and closed clients are kept as real short records, not compressed to one line, agency clients re-engage and that history is worth having later. See `consolidate` for how this file avoids growing unbounded without losing that history.

## Active clients

Fill one block per client. Leave a field blank rather than guessing.

```
### <Client name>
- **Client contacts (all projects):** (name, role, Slack handle if reachable via DM, why they're the client-wide contact, e.g. billing or primary relationship)
- **Relationship notes:** (comms preferences, sensitivities, anything durable that isn't project-specific)
- **General chat (if any):** (tool + channel, only if there's a client-wide channel separate from per-project ones)

  #### Active projects

  ##### <Project name>
  - **ClickUp:** (Space / Folder / List, and a link). If it follows the standard four-list shape (Execution Tasks, Bugs & Change Requests, Meeting Notes, Question Tracker), note that; each list feeds a different workflow, see CLAUDE.md.
  - **Project type:** (adhoc / one-time / mixed) - adhoc has no fixed sprint structure, work arrives as individual requests; one-time is a fixed-scope build running sprint work in lists created fresh per sprint; mixed is a one-time build with adhoc requests also running alongside it.
  - **Active sprint list (one-time/mixed only):** (the current sprint's list name; update this as sprints roll, `client-update` reads whichever list is named here, not Execution Tasks)
  - **Weekly client update:** yes / no (you set this per project; nothing gets swept into this report by inference)
  - **Chat:** (tool + channel, e.g. Slack #acme-wrg. External project channels and client/team DMs are both Slack for now; Google Chat is deliberately not swept yet, see CLAUDE.md)
  - **Email domain (if relevant):** (if this project's client contact emails from a different address than your own WRG one and you're forwarding it in, this is still just the domain the mail actually arrives showing, forwarding doesn't change what to match on)
  - **Client contacts (this project):** (only if different from, or in addition to, the client-wide contacts above; include Slack handle)
  - **Internal team:** (WRG dev/DM/QA/AM/PC leads staffed on this specific project; include Slack handle for anyone whose updates come through DM rather than the project's ClickUp folder)
  - **Phase:** (discovery / build / QA / launched / support)
  - **One-line context:** (what this project actually is)
  - **Status notes:** (anything a workflow needs that doesn't have its own field: cadence with this client, a pending dependency, etc.)

  #### Paused projects
  (Same block shape. Workflows skip these unless asked. A project pauses without the client relationship pausing.)

  #### Closed projects
  (A real short record, not a single line: what it was, key outcomes, close date, a link into `memory/decisions.md` if relevant decisions were logged there. Kept for when this client comes back for a related project.)
```

## Paused clients
(Same shape as an active client block, used when nothing for that client is currently active, but the relationship isn't over. No active-projects sweep happens here until something moves back to active.)

## Closed clients
(A real short record per client, not a single line: name, close date, one-line summary of the relationship, a link into `memory/decisions.md`. The individual project detail can be lighter here since the relationship itself ended, but never compressed to nothing.)

## Changelog
- [YYYY-MM-DD] Created at setup.
