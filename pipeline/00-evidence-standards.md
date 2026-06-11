# Evidence Standards

Shared rules for what counts as a mentor's teaching and how claims are graded.
All three pipeline stages apply these. Research briefs must **inline** the relevant
rules (briefs are self-contained and can't reference this file).

## The evidence ladder — taught vs implied

What counts as "the mentor teaches this"? Four rungs; the first three are admissible:

| Marker | Meaning | Rule |
|---|---|---|
| `[stated]` | The mentor explicitly says it as advice, instruction, or position. | Fully in. Sub-mark quote fidelity: `[stated-verbatim]` or `[stated-paraphrased]`. |
| `[demonstrated]` | The mentor shows it through their examples, stories, or visible actions without naming it as advice. | In. Cite the demonstration itself ("in his teardown of X, he does Y"). Never upgrade to `[stated]`. |
| `[reconstructed]` | A pattern the researcher infers across the mentor's material that is never stated or singly demonstrated. | Weakest admissible. Requires ≥2 independent instances, all cited. |
| *(generic)* | True of any competent expert in the domain; can't be tied to this mentor. | **Out.** Spot-check: if the sentence would survive with the mentor's name swapped for anyone else's and no citation breaks, cut it. |

Markers travel with claims through findings into the brain — synthesis preserves them.

## The currency rule — mentors change their minds

Breadth-first search finds *popular* positions, not *current* ones. A superseded tip
elaborated in good faith is the pipeline's most dangerous failure mode. Therefore:

1. **Date everything.** Scans and findings record publication dates wherever recoverable.
2. **Verify before reporting.** Before a research agent reports a major claim, it checks
   whether the mentor has revised, walked back, or contradicted it in later material.
   Search explicitly for retractions ("I was wrong about", "I no longer recommend",
   newer content on the same topic).
3. **Latest position wins.** The brain teaches the current position. Superseded positions
   are recorded as evolution (in `sources.md` and findings' "Evolution & corrections"
   sections), never as live advice.
4. **Findings must include an "Evolution & corrections" section** — even if its content
   is "no position changes found" (that's a checked fact, not a default).

## Teaching-style evidence tiers

Teaching style is *behavioral* evidence, not claim evidence: it can only be researched
by observing instances of the mentor actually mentoring. Claims about it are graded:

| Tier | Evidence | Examples |
|---|---|---|
| **T1 — observed** | Recorded interaction with a real learner. | Coaching calls, live portfolio/profile reviews ("roast my X"), office hours, live Q&A with back-and-forth, student critiques, workshop recordings. |
| **T2 — self-described** | The mentor describing how they mentor or what they'd say to someone. | "What I tell my students...", interviews about their coaching. |
| **T3 — inferred** | Deduced from the structure of their one-to-many content. | Sequencing of a course, how their videos open. |

Rules:
- Every claim in a brain's `teaching-style.md` carries its tier.
- **T1 is the gate.** If Stage 1's source hunt finds no T1 artifacts, the pipeline stops
  after Stage 1 and reports to the user (see `01-broad-scan.md`, checkpoint). The user
  may supply private sources, accept a degraded T2/T3-only style profile (the brain and
  sessions must say so), or skip the style brief.
- Sessions inherit the tier: a T2/T3-only style profile is run as "the mentor describes
  their approach as..." — never presented as observed behavior.
