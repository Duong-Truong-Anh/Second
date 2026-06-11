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
Follow `pipeline/01-broad-scan.md` exactly. Use web search/fetch extensively — the scan
lives or dies on breadth. Write `mentors/<slug>/scan.md` in the prescribed structure.
**Stop and show the user the scan**, especially the "Research needs" section — they may
know channels or material the scan missed. Incorporate their input before Stage 2.

## Stage 2 — Research handoffs
Follow `pipeline/02-research-handoffs.md`. For each research area:
1. Write the brief to `mentors/<slug>/research/handoffs/NN-<topic>.md` using
   `pipeline/templates/research-handoff.md`. Honor all five partitioning rules —
   each brief fully self-contained, scope boundaries explicit.
2. Always include the dedicated **teaching & mentoring style** brief.

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
