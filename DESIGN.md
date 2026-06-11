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

### D7. Evidence ladder: stated / demonstrated / reconstructed (2026-06-11)
Resolves "taught vs implied." A mentor's teaching includes what they explicitly state,
what they demonstrate through examples and stories without naming, and patterns
reconstructible from ≥2 independent instances — each marked as such, with markers
surviving into the brain and into session attribution. Generic domain knowledge stays
out. Defined once in `pipeline/00-evidence-standards.md`; briefs inline it (briefs are
self-contained). Rationale: without an explicit boundary, different scan agents draw
it differently and mentors get inconsistent brains.

### D8. Teaching style is source-hunted, not scanned (2026-06-11)
Mentoring behavior is *behavioral* evidence — it can only be researched by observing
instances, not by summarizing claims. Stage 1 therefore hunts for artifacts (recorded
coaching calls, live reviews, office hours) instead of describing the style; this is a
dedicated section of the scan format, not an emphasis. Evidence tiers: T1 observed
interaction / T2 self-described / T3 inferred from content structure. **T1 is a hard
gate:** if none found, the pipeline stops after Stage 1 and the user chooses — supply
private sources (`research/user-sources/`), proceed with a labeled T2/T3-only profile,
or skip. The Stage 2 style brief is observational (template:
`research-handoff-observational.md`): it mines the listed artifacts, expands
collections (a playlist → every session in it), and extracts behavior as
situation → move → outcome instances before generalizing.

### D9. Currency rule: latest position wins (2026-06-11)
Breadth-first search finds popular positions, not current ones — Stage 1 can't fix
that, so Stage 2 must: every brief requires dating claims and checking for later
revisions/retractions before reporting; findings carry a mandatory "Evolution &
corrections" section; synthesis arbitrates conflicts by latest dated position and
records superseded ones as evolution in `sources.md`. The scan helps by inventorying
"self-corrections & changed positions" as a category breadth search *can* find.

### D10. Scan proposes, Stage 2 partitions; coverage is a three-state map (2026-06-11)
Partition ownership was ambiguous. Now: the scan only *nominates* research candidates;
Stage 2 owns the final partition under explicit criteria (one brief ≈ one mentee-facing
decision domain, prefer the mentor's own framework boundaries, size limits), recorded
in `research/handoffs/00-partition.md` for auditability. Every scan inventory item is
tagged `[covered]`/`[thin]`/`[absent]`: thin items ride along on neighboring briefs,
absent items get no brief and seed `gaps.md` directly — giving sessions an explicit
before-the-fact map of when they're extrapolating.

### D11. Mentor viability prerequisite (2026-06-11)
The workflow only works for publicly documented teachers. Stated in the README; the
scan's first step includes a viability verdict so an unsuitable mentor fails fast,
before research is spent.

## Open questions

- **O1. Mentor instruction format.** Is a markdown brain + session protocol enough, or
  do mature mentors need more structure (per-topic skills, a curriculum graph, retrieval
  over large source sets)? Revisit after the pilot brain exists and we see its size.
- **O2. Mentee assessment.** What does the first-session intake actually measure, and
  how does the mentor detect progress level in later sessions? Current answer: intake
  questions + `progress.md`, but a real assessment rubric per domain may be needed.
- **O3. Multi-mentor.** Can tracks consult multiple mentors? Do mentors ever disagree
  on record, and how is that surfaced? Deferred until ≥2 brains exist.
- **O4. Source ingestion.** Partially answered by D8: `mentors/<slug>/research/user-sources/`
  exists for user-supplied teaching-style evidence. Still open: a general inbox for
  user-supplied material on *topic* briefs (transcripts, course notes, books), and how
  research agents should weigh private material against public material.
- **O5. Session cadence + homework.** Real mentorship includes between-session work.
  How does the mentor assign, track, and review homework? Sketched in the session
  protocol; needs validation in the pilot.
- **O6. Quality gate for research findings.** How do we verify a research agent didn't
  hallucinate? Current answer: citation + dating requirements, evidence-ladder markers,
  the currency rule, and synthesis cross-checking. May still need a dedicated
  verification pass (an agent that samples citations and confirms they say what the
  findings claim).
- **O7. Partition quality.** D10 gives Stage 2 explicit partitioning criteria, but
  whether they produce good partitions is unproven. Revisit after the Jamie Brindle
  build — compare the partition `00-partition.md` records against what synthesis
  actually needed.
