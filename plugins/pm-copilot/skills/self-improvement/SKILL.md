---
name: self-improvement
description: The weekly loop where the system learns from its own use. Scans your recent activity for drafts that got reworded (voice signals) and for repeatable workflows worth turning into skills or fixes, then applies the changes you approve. Walked through part by part, writes held to the end. Run it in a new chat whenever you want.
---

## GUIDED DELIVERY - one part at a time (always)
Do not output a single combined digest. Walk the user through the run part by part as separate turns in the OUTPUT order (Voice corrections, New skill candidates, Improvement candidates, Ready-to-apply diffs), each led by one plain intro line and ending with its question, then stop and wait. Hold all writes to the end and apply only what the user approves.

## FORMATTING - lists, never paragraphs (always)
Whenever you present more than one item, render them as a bulleted or numbered list, one item per line. Never pack multiple items into a run-on paragraph.

---

You are running the user's **self-improvement** pass, the weekly loop where the system learns from its own use. Read `memory/role.md`, `memory/day-to-day.md`, and `memory/engagements.md` first for tools, timezone, work week, and which clients and projects are actually active (so friction on a since-closed project doesn't get proposed as a fix). Surface everything in this session; never message the user externally. No em-dashes. Each phase is fault-isolated: if one errors, note it and continue. Signal-gathering (Phases 1 and 2) runs before applying (Phase 3) so the applier sees this week's new entries.

Friction log: `memory/skill-improvements.md`. Entry format: `- YYYY-MM-DD | "<quote or diff summary>" | proposed change in one line | open`.

## PHASE 1 - Draft-not-sent scan (voice-correction signals)
Window: last 7 days. Scan in parallel, using the connected tools: recent session transcripts, chat sent by the user, email sent by the user, recent doc edits. For each draft the co-pilot produced (a message, email, doc section, ticket comment; ignore code and scaffolds), find what actually landed and classify: NEVER SENT (no match); SENT MATCHING (high overlap, skip); SENT DIVERGED (partial overlap, same intent, different wording, a voice-correction signal). For each diverged draft, propose a friction-log entry under the relevant skill heading (or under a voice/routing heading for the routing brain). Propose the diff; do not auto-write. If transcripts are unavailable, degrade to sent-only mode and say so.

## PHASE 2 - Skill-spotter scan (new and improved skill candidates)
Scan the last 7 days across the connected tools for: (A) new skill candidates, repeatable workflows the user did 2+ times, asked for repeatedly, or that took multiple manual steps; (B) improvement candidates, friction with existing skills or tasks (corrections, redos, "why does it keep" moments). For each: name, where spotted, what it does today, the opportunity. Write (B) as proposed friction-log entries (propose-only). Frame as opportunity. Three sharp candidates beat seven vague ones.

## PHASE 2.5 - Memory gap sweep + triage
Invoke `memory-keeper` in weekly-sweep mode: read `memory/context-watchlist.md`, check each source for material change since it was last swept, and append genuine, routing-mapped gaps to the pending queue in `memory/context-gaps.md` (with dedup and relevance rules). Advance the "last swept" marker only for sources that succeeded. Then present the pending queue for triage, one line per item, drift first, with actions Ingest / Skip / Mute / Link. On Ingest, propose the memory diff (target file, target section, a short before/after) and write only on approval, then move the item to the ingested log. Skip increments a surface count and ages out to Muted after a few passes. Mute means never surface again. Propose-only.

## PHASE 3 - Apply approved diffs
Read every `open` entry in `memory/skill-improvements.md`, including any just proposed and approved this run and any deferred here by the reactive `improve` skill (the two share this friction log). For each, propose a concrete diff. Surface all diffs for bulk approve/reject. What "apply" means depends on the target:
- **A memory file** (`role.md`, `voice.md`, `day-to-day.md`, `engagements.md`, the routing table in `CLAUDE.md`, or similar): apply directly on approval, with a dated changelog line in the affected file. These live in your workspace; writing here is safe and permanent.
- **A skill or command file** (anything under a plugin's `skills/` or `commands/`): these are installed from your GitHub-hosted plugin repo, not your workspace. Editing the locally cached copy directly doesn't stick, the next auto-sync overwrites it with whatever GitHub still has. On approval, write the finished diff into `memory/skill-improvements.md` marked `ready-to-commit` instead of touching the cached file, so it's ready to bring to a session with GitHub access to actually commit and version-bump.
Flip each entry to `applied` (memory files) or `ready-to-commit` (skill/command files) or `wontfix`.

Also run the **weekly memory consolidation** step here if it is not scheduled separately: a reflective pass over the memory files to merge duplicates, retire stale entries, and fix the index. Propose the changes; write only on approval. (If the user set up the biweekly memory-refresh task, consolidation lives there instead; skip it here.)

## PHASE 2.6 - End-of-day-check calibration (report only, no changes proposed)
Read `memory/state/end-of-day-check-log.md`. Compute how often the suggested tag (relay-critical / routine) matched what the user actually decided, over the entries logged since the last time this phase ran. Report the rate plus a count (e.g. "matched 11 of 14 this week"). This is informational only, this phase never proposes changing the tagging behavior itself; that stays the user's call, made explicitly, not something this loop escalates to. If the log is empty or doesn't exist yet, omit this section rather than reporting a zero.

## OUTPUT - walked through one part at a time
```
Self-Improvement - [date]
Draft-not-sent [ok/failed] · Skill-spotter [ok/failed] · Memory sweep [ok/failed] · Applier [ok/failed]

End-of-day-check calibration: matched N of M this week [omit if log is empty]

Voice corrections (drafts that diverged / never sent)
- [item] - [the divergence] - propose logging?

New skill candidates
- [name] - [what it'd automate] - build?

Improvement candidates (existing skills)
- [skill] - [the friction] - propose fix?

Ready-to-apply diffs (from open friction-log entries)
- [skill] - [one-line diff] - apply?
```
Wait for approval on each part, then apply approvals and update statuses. Nothing written or applied without explicit confirmation this run. If the morning brief keeps an auto-close audit log, read its reopen records and report the auto-close false-positive rate so the accepted fuzzy-match risk stays measured.
