# Design Log

Decisions made, with reasoning, plus the open questions we haven't answered yet.
This project lives in "I don't know what I don't know" territory — this file is how
we keep track of what we've figured out and what we're still circling.

## Decided

### D1. The product is the workflow, not the mentors (2026-06-11)
This repo is designed to be public. Anyone should be able to clone it and build their
own mentor from their own guiding voices. Mentor brains are instances; the pipeline,
templates, and session protocol are the product. Everything in `pipeline/` must
therefore be mentor-agnostic and agent-agnostic.

### D2. Three-stage research pipeline (2026-06-11)
1. **Broad scan** — one pass mapping the WHAT: the complete surface of a mentor's
   teachings, plus a brief overview of who they are and why they matter. Breadth only,
   no depth.
2. **Research handoffs** — the scan is partitioned into independent research briefs
   covering the WHYs and HOWs. As many briefs as the material requires. Each brief is
   fully self-contained (an agent reading it cold needs zero outside context), overlaps
   minimally with its siblings, forbids general-knowledge padding, and demands
   source citations.
3. **Synthesis** — findings are curated into a standardized mentor brain with full
   provenance and an explicit gaps list.

Rationale: a single research pass can't go deep and broad at once; independent briefs
parallelize depth and can be run by *any* agent (Claude subagents, other AI tools,
even manually), which keeps the workflow portable.

### D3. Labeled blending for gaps (2026-06-11)
In sessions, the mentor distinguishes sourced advice ("the mentor explicitly teaches X")
from extrapolation ("the mentor hasn't addressed this directly; consistent with their
principles, I'd suggest Y"). Strict sourced-only would dead-end early; unlabeled
extrapolation would corrupt the whole point of having real mentors.

### D4. Knowledge, not persona (2026-06-11)
We capture frameworks, philosophy, tips, workflows, and *how they teach 1-on-1* —
we do not imitate voice or personality.

### D5. Pilot track: Jamie Brindle / freelancing (2026-06-11)
Build the system against one real track first. Abstractions earned from a working
example, not guessed up front.

### D6. Interface: slash-command skill now, portable core always (2026-06-11)
`/mentor` and `/mentor-build` are Claude Code skills, but they are thin: all real
content (brain, session protocol, mentee profile, progress notes) is plain markdown
so any agent harness can run the same workflow later.

## Open questions

- **O1. Mentor instruction format.** Is a markdown brain + session protocol enough, or
  do mature mentors need more structure (per-topic skills, a curriculum graph, retrieval
  over large source sets)? Revisit after the pilot brain exists and we see its size.
- **O2. Mentee assessment.** What does the first-session intake actually measure, and
  how does the mentor detect progress level in later sessions? Current answer: intake
  questions + `progress.md`, but a real assessment rubric per domain may be needed.
- **O3. Multi-mentor.** Can tracks consult multiple mentors? Do mentors ever disagree
  on record, and how is that surfaced? Deferred until ≥2 brains exist.
- **O4. Source ingestion.** Right now research agents work from public web material.
  Do we need an inbox for user-supplied material (transcripts, course notes, books)?
  Likely yes — add when first needed.
- **O5. Session cadence + homework.** Real mentorship includes between-session work.
  How does the mentor assign, track, and review homework? Sketched in the session
  protocol; needs validation in the pilot.
- **O6. Quality gate for research findings.** How do we verify a research agent didn't
  hallucinate? Current answer: citation requirements + synthesis cross-checking.
  May need a dedicated verification pass.
