---
name: mentor-build
description: Build a mentor brain by running the research pipeline (broad scan → independent research handoffs → synthesis). Use when the user wants to add a new mentor, says "/mentor-build <name>", "build a mentor", "research <person> as a mentor", or wants to refresh/extend an existing mentor brain.
---

# Build a Mentor Brain

Run the three-stage pipeline defined in `pipeline/`. The argument is the mentor's name;
if the mentorship domain isn't obvious or given, ask for it before starting.

## Stage 0 — Setup
1. Slugify the name (e.g. `jamie-brindle`) and create `mentors/<slug>/`.
2. If the mentor already exists, ask: refresh the scan, add research areas, or rebuild?

## Stage 1 — Broad scan
Follow `pipeline/01-broad-scan.md` exactly (standards: `pipeline/00-evidence-standards.md`).
Use web search/fetch extensively — the scan lives or dies on breadth. Write
`mentors/<slug>/scan.md` in the prescribed structure, including the viability
assessment, coverage map, and the teaching-style **source hunt** (artifacts, not
summaries).

**Mandatory checkpoint — stop and report to the user:**
- Viability verdict (thin public footprint → recommend stopping).
- Teaching-style source verdict. **If no T1 artifacts (recorded real interactions)
  were found, warn explicitly:** continuing means a self-described/inferred style
  profile only. Offer: (a) user supplies private sources into
  `mentors/<slug>/research/user-sources/`, (b) proceed degraded, (c) skip the style
  brief. Do not proceed to Stage 2 without their answer.
- Coverage map + research candidates — they may know channels or topics the scan missed.

## Stage 2 — Research handoffs
Follow `pipeline/02-research-handoffs.md`:
1. **Partition first** (Stage 2 owns it; the scan only proposed). Apply the criteria,
   record the mapping in `research/handoffs/00-partition.md`.
2. Write topic briefs to `mentors/<slug>/research/handoffs/NN-<topic>.md` using
   `pipeline/templates/research-handoff.md` — self-contained, scope-bounded, currency
   rule and evidence ladder inlined.
3. Write the **teaching-style brief** using
   `pipeline/templates/research-handoff-observational.md`, pasting in the scan's
   source-hunt table plus any user-supplied sources (mandatory unless the user skipped
   it at the checkpoint).

Then ask the user how to run them:
- **Subagents (default):** spawn one research agent per brief, prompt = the brief file
  verbatim plus one line: "Write your findings to
  `mentors/<slug>/research/findings/NN-<topic>.md`." Run them in parallel.
- **External:** the user copies briefs into other AI tools and pastes results back into
  `research/findings/` — wait for them to say findings are in.

Apply the acceptance check from `pipeline/02-research-handoffs.md` to each finding.
Findings that fail (uncited claims, generic filler) get re-run or flagged, not synthesized.

## Stage 3 — Synthesis
Follow `pipeline/03-synthesis.md`. Build `mentors/<slug>/brain/` from the templates in
`pipeline/templates/mentor-brain/`. Verify the "done when" criteria, then summarize for
the user: what the brain covers, what's in `gaps.md`, and suggest starting with
`/mentor <slug>`.

## Throughout
- Commit at each stage boundary (scan / handoffs+findings / brain).
- Never let general knowledge masquerade as the mentor's teaching — the pipeline's
  value is provenance.
