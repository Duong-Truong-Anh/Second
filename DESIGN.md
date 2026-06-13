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
out. Defined once in `pipeline/evidence-standards.md`; briefs inline it (briefs are
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

### D12. Research engines are interchangeable; the findings format is the contract (2026-06-11)
Stage 2 assumed agents can search the whole web — false, and Claude's native fetch is
the most restricted of the realistic options (sandboxed cite-then-fetch, robots-bound,
no paywalls). Stage 2 now ends with an engine choice the user makes per build:
**Gemini Deep Research** (widest sweep; verbose academic output tamed by an adapter
block appended to each brief), **Perplexity Search Pro** (best practical reach;
~3 free Pro searches/day/account, so spreading self-contained briefs across multiple
accounts is a supported pattern), or **Claude subagents** (fully automated, weakest
reach). External paths get a guided copy-paste flow: one brief per fresh instance,
reports pasted into pre-created findings files — never back into prompts. Mixing
engines across briefs is fine. Caveat recorded: no engine watches video; transcripts
in `research/user-sources/` are the highest-leverage manual step for the style brief.

### D13. Junction insights: exclusive centers, shared edges (2026-06-11)
Mentors' insights often live only at the intersection of two topics (what they say
about pricing only when discussing client relationships). A hard-boundary partition
guarantees those fall between briefs — neither claims them, neither finds them.
Three-part fix: (a) the scan inventories **cross-topic junctions** as first-class
items (the coverage map can't catch what was never named); (b) the partition rule
"minimal overlap" is replaced by **exclusive centers, shared edges** — briefs may not
research a neighbor's core for its own sake but must report cross-topic material under
a mandatory "Junctions" findings section, and every scanned junction is assigned to
exactly one brief in `00-partition.md` (an unassigned junction is a partition bug);
(c) synthesis dedupes edge duplication and cross-references each junction insight from
both of its topics in the brain.

### D14. Stage 0 — Definition; corrections vs drift (2026-06-11; refines D9)
"Latest position wins" hid an assumption: that the mentor's newest teaching is the
most relevant. True for **corrections** (the mentor says the old position was wrong —
latest wins unconditionally), false for **drift** (nothing retracted; the mentor's
audience/stage moved — e.g. solo-freelancer advice → agency-owner advice). A new
Stage 0 (`pipeline/00-definition.md`) settles, in a short Q&A before any research:
identity anchor (disambiguation), domain & goal (bounds scan and partition), **era
preference** (current / earlier phase / stage-matched — arbitrates drift only), and
the mentee's starting point. Output: `mentors/<slug>/definition.md`. Evidence
standards renamed to `pipeline/evidence-standards.md` (cross-cutting standards, not a
numbered stage).

### D15. The mentee profile is a hypothesis, not a fact (2026-06-11)
Three static documents (brain, profile, progress) simulate a dynamic relationship, so
calibration goes stale: a session reading a three-month-old profile teaches who the
mentee *was*. Mitigations now: sessions open by re-verifying load-bearing facts;
in-session evidence overrides the documents; profile/progress may be updated
mid-session (session close is the minimum checkpoint, not the only one); stage
assessments carry a "last verified" date, and a stale verification is explicitly a
hypothesis to re-check. The deeper dynamic-mentee-model problem stays open (O8).

### D16. Project name: Second (2026-06-11)
A second voice, a second opinion, a guiding one — the one who is not the main act but
makes the main act possible. The mentee is the main act.

### D17. Privacy boundary: instances are gitignored, only the workflow is tracked (2026-06-11)
The pilot build committed `mentors/jamie-brindle/` — wrong for two reasons: the
definition/profile/session files contain the *user's* personal context, and a mentor
brain is a real person's distilled teachings, which isn't ours to publish in a public
repo. Now `.gitignore` excludes `mentors/`, `mentee/`, and `workspace/` (their READMEs
stay tracked as structure docs); the blank mentee template moved to
`pipeline/templates/mentee-profile.md` so sessions can create `mentee/profile.md`
locally. The skills no longer commit stage boundaries or session artifacts — boundaries
are verification checkpoints, and the files themselves are the record. Escape hatch:
private forks can delete the ignore rules to get version history back. The pilot's four
local commits were dropped before ever being pushed; nothing personal reached the
public repo.

### D18. Provenance in the artifact, voice in the session (2026-06-13; refines D3, D4)
Running the pilot first session exposed that we put provenance *in the conversation*:
inline source IDs (`[S19]`) and "Jamie teaches…" on every claim made the mentor feel
like a database read-out — and, ironically, made real-world advice read like theory,
violating the mentor's own ethos. Two coupled fixes:
- **Provenance is an auditing property of the brain, not a speech act.** The brain and
  session logs carry the full trail (markers, ledger, gaps); sessions speak with
  internalized authority. The only spoken honesty signal is sourced-vs-extrapolated,
  voiced naturally and only when crossing into what the brain doesn't cover. (Refines
  D3's labeled blending — the integrity guarantee is unchanged, only the delivery.)
- **Knowledge AND voice, not impersonation** (refines/partly reverses D4). The old
  "knowledge, not persona" rule conflated *voice* (how they talk — well-sourced from
  monologue content) with *impersonation* (claiming to be them — forbidden). We threw
  away sourced signal out of fear of the unsourced kind. Now: a new `voice.md` brain
  file (+ a mandatory voice research brief, a scan voice section, and a synthesis step)
  captures register/phrasings/metaphors verbatim; sessions speak in it but never claim
  the mentor's identity or biography. User chose this stance ("Jamie's voice, not his
  identity") over full first-person and over keeping the neutral third-person. The
  voice/teaching-style distinction is sharp: voice = how they sound (sourced);
  teaching-style = how they mentor 1-on-1 (often unsourced, the T1 problem).

### D19. Memory architecture: nested mentees/<name>/<mentor>/ (2026-06-13; supersedes D-era workspace/)
The single shared `mentee/profile.md` + `workspace/<track>/` split wasn't future-proof:
no multi-mentee support, and identity (cross-mentor) was tangled with relationship state
(per-mentor). New structure: `mentees/<mentee>/profile.md` (who I am, shared across all
mentors) + `mentees/<mentee>/<mentor-slug>/journey.md` + `sessions/` (the memory of one
mentorship). Two kinds of memory, two lifetimes, two levels. `mentee/` and `workspace/`
removed; `.gitignore` now covers `mentors/` + `mentees/`.

### D20. journey.md models what a mentor actually remembers (2026-06-13; answers part of O2/O8)
The pilot session tracked nothing — not even the user's name. `journey.md` is built on
six axes a real mentor holds about a person: **calibration** (dated stage hypothesis),
**open loops** (commitments with honest status), **covered ground** (build, don't
repeat), **the read** (private working model of how they tick — the axis that makes
continuity feel like a relationship), and **next move**; identity (#0) lives up at
`profile.md`. Plus an execution rule the failure exposed: **write memory incrementally
at natural beats** (identity right after intake, a commitment when struck), not batched
at session close — the pilot died to a rate limit and saved nothing.

### D21. Commitments are negotiated, not manufactured (2026-06-13; refines O5)
The session skill *required* a next-action output, so homework got minted whether or not
the mentee would do it — and the pilot assigned proof-capture *before* learning "I'm bad
at these things." Fix: continuity comes from recording *state*, not from minting a task;
when a next step is genuinely right, propose then calibrate to the smallest version the
mentee will actually do, and record the negotiated form. Sometimes the right next step is
none. Kept as a principle, not a "always ask for the smallest version" script (which
would become its own tic). The external critique that surfaced this was adopted at its
core but not its claim that homework is *only* a continuity artifact — capturing proof
was genuinely the right step; the flaw was assigning it un-negotiated.

## Open questions

- **O1. Mentor instruction format.** Is a markdown brain + session protocol enough, or
  do mature mentors need more structure (per-topic skills, a curriculum graph, retrieval
  over large source sets)? Revisit after the pilot brain exists and we see its size.
- **O2. Mentee assessment.** Partly answered by D20 (the calibration + read axes of
  journey.md). Still open: a real per-domain assessment *rubric* — the intake still
  measures stage impressionistically, not against a yardstick the mentor brain defines.
- **O3. Multi-mentor.** D19's `mentees/<name>/<mentor>/` makes multiple mentors per
  mentee structural. Still open: can a *session* consult more than one brain at once,
  do mentors ever disagree on record, and how is that surfaced? Deferred until ≥2 brains
  are in real use.
- **O4. Source ingestion.** Partially answered by D8: `mentors/<slug>/research/user-sources/`
  exists for user-supplied teaching-style evidence. Still open: a general inbox for
  user-supplied material on *topic* briefs (transcripts, course notes, books), and how
  research agents should weigh private material against public material.
- **O5. Session cadence + homework.** Largely answered by D21 (negotiated, calibrated,
  tracked as journey.md open loops with status) — but the *cadence* half is open: nothing
  yet handles time between sessions (a commitment agreed "this week" has no notion of how
  long it's actually been, no nudge, no decay). Revisit once multiple real sessions exist.
- **O6. Quality gate for research findings.** How do we verify a research agent didn't
  hallucinate? Current answer: citation + dating requirements, evidence-ladder markers,
  the currency rule, and synthesis cross-checking. May still need a dedicated
  verification pass (an agent that samples citations and confirms they say what the
  findings claim).
- **O7. Partition quality.** D10 gives Stage 2 explicit partitioning criteria, but
  whether they produce good partitions is unproven. Revisit after the Jamie Brindle
  build — compare the partition `00-partition.md` records against what synthesis
  actually needed, including whether junction assignment (D13) caught the real
  intersections or only the ones the scan happened to name.
- **O8. Dynamic mentee modeling.** D15 + D20 give detectable staleness (dated
  calibration, the "read" axis, incremental writes), but the model is still prose files
  updated by hand each session. Candidate future shape: calibration decay tied to elapsed
  time/sessions (overlaps O5's cadence gap). Needs data from multiple real sessions on
  how fast calibration actually drifts before designing more.
- **O9. Voice without 1-on-1 behavior.** For Jamie, `voice.md` is well-sourced but
  `teaching-style.md` is degraded (T2/T3). A session now has a strong sense of how he
  *sounds* but a weak sense of how he *runs a session*. Untested whether good voice
  papers over thin teaching-behavior convincingly, or whether the gap shows. Watch in
  the re-run of the pilot session.
