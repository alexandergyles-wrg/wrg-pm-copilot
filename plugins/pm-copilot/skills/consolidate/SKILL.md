---
name: consolidate
description: A reflective cleanup pass over your memory files (no external fetch). Merges duplicates, retires stale entries, sharpens durable facts, and fixes the index so a future session orients fast. Backs up first, proposes changes, writes only on your yes. Triggers on "consolidate my memory", "clean up my memory". Run it right after sync, or whenever your memory needs a cleanup.
---

# Consolidate - Memory Hygiene (safe mode)

A reflective pass over what the co-pilot has learned about the user and their work. Goal: a future session should orient quickly (who they work with, what they're focused on, how they like things done) without re-asking. This reads and restructures the memory folder only; it does not fetch from external tools (that's `sync`, which normally runs just before this).

Memory lives in the `memory/` folder next to CLAUDE.md.

## Step 0 - Back up first (non-negotiable)
Snapshot the memory folder before any edit, same pattern as `sync`. If the backup fails, STOP.

## Phase 1 - Take stock
- List the memory folder and read the index in CLAUDE.md's routing table.
- Skim each file. Note which overlap, which look stale, which are thin.

## Phase 2 - Plan the consolidation (propose-only)
Separate the durable from the dated:
- **Durable** (preferences, working style, key relationships, recurring workflows, standing initiatives): keep and sharpen.
- **Dated** (a passed deadline, a one-off, a completed internal task): retire the file, or fold the lasting takeaway (for example "prefers X format for launch docs") into a durable file, then drop the rest.

**Exception: closed client and project history in `memory/engagements.md` is never dropped, only archived.** This fork is agency work, closed clients and past projects re-engage, sometimes years later, and their context needs to survive that gap. Never apply the fold-forward-and-drop treatment to a closed client or project block. If `memory/engagements.md` is getting large, propose moving the oldest closed records, verbatim, into a dated `memory/engagements-archive.md` rather than compressing them, and leave a one-line pointer behind ("<client> - see engagements-archive.md"). This is the one place in this skill where the default instinct (retire and drop) is wrong.

**Log rollup, 90 days.** For the append-only logs (`memory/state/morning-brief-audit.md`, `memory/state/end-of-day-check-log.md`), entries older than 90 days can be rolled into a short dated summary (counts and rates, e.g. "Jan-Mar: 42 auto-closes, 2 reopened") instead of kept as individual rows. This is the one place summarizing instead of preserving is correct, the detail has no ongoing use once self-improvement has already reported on it. Propose this rollup the same as any other change; never do it silently.

Prepare specific proposed changes:
- Merge duplicate facts into one canonical location.
- Fix anything stale or contradicted (prefer the newest confirmed fact; flag genuine conflicts for the user rather than guessing).
- Tighten wording so each file is scannable.
- Update the routing table in CLAUDE.md if files were added, merged, or retired.

Present the plan as a short list: merge / retire / rewrite / reindex, one line each.

## Phase 3 - Apply only what's confirmed
Apply the approved changes. Add a dated changelog line to each affected file. Keep the backup. Confirm what changed in this session.

## Guardrails
- Propose-only. No write without the user's yes.
- Never delete a file outright; retire by folding forward the durable takeaway first.
- Never fold-and-drop a closed client or project in `memory/engagements.md`; archive it verbatim instead, see Phase 2.
- When two facts conflict and you can't tell which is current, ask; do not silently pick one.
