# Evidence Standards

Shared rules for what counts as a mentor's teaching and how claims are graded.
All pipeline stages apply these. Research briefs must **inline** the relevant
rules (briefs are self-contained and can't reference this file).

## Provenance is an auditing property of the brain, not a speech act in the session

The pipeline's job is to guarantee that every claim in a brain is real and traceable.
That guarantee is enforced **in the artifact** — markers on claims, the `sources.md`
ledger, the gaps list. It is *not* meant to be performed aloud in a session. A session
that recites source IDs or prefixes every sentence with "the mentor teaches…" turns
internalized knowledge back into a database read-out, and (ironically) makes hard-won
real-world advice feel like theory. So:

- **Findings and the brain:** show all the provenance. Mark everything. This is where
  auditability lives.
- **Sessions:** speak with internalized authority. Provenance stays in the brain and the
  session log (the audit trail), not in the conversation. The one honesty signal that
  *does* surface is the **sourced-vs-extrapolated boundary** — and only when it changes
  how much the mentee should trust the advice (i.e. when crossing into territory the
  brain doesn't cover). See DESIGN.md D18.

## Voice vs impersonation

A mentor brain captures two separable things, and they have very different evidence
profiles:
- **Voice** — *how the mentor talks and explains*: register, cadence, metaphors,
  phrasings, explanatory structure. This is **well-sourced** from monologue content
  (videos, posts, talks) and belongs in `voice.md`. Sessions adopt it.
- **Teaching behavior** — *how the mentor mentors a person 1-on-1*. This is **often
  unsourced** (the T1 problem below) and belongs in `teaching-style.md`.

Sessions may speak **in the mentor's voice** — that is adopting how they express ideas,
which is sourced. Sessions may **not impersonate**: never claim to *be* the mentor,
never invent their biography or put words/positions in their mouth they didn't hold. If
the mentee asks something the real person never addressed, the voice stays but the
certainty drops to honest extrapolation. (Knowledge **and voice**, not impersonation —
this refines the older "knowledge, not persona" rule; see DESIGN.md D18.)

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
3. **Corrections always win; drift is arbitrated.** Old positions come in two kinds,
   and they resolve differently:
   - **Correction** — the mentor says (or clearly shows) the old position was wrong.
     The latest position wins unconditionally; the old one is recorded as evolution,
     never taught as live advice. No era preference can resurrect a correction.
   - **Drift** — nothing was retracted; the mentor's audience or stage changed (the
     solo-freelancing advice of 2018 vs the agency-owner advice of 2026). Here newest
     is *not* automatically most relevant: the era preference in the mentor's
     `definition.md` (Stage 0) decides which version the brain centers on. The other
     era is recorded as evolution with its stage context, available when the mentee
     reaches it.
4. **Findings must include an "Evolution & corrections" section** — even if its content
   is "no position changes found" (that's a checked fact, not a default). Where
   possible, findings note whether a change looks like a correction or drift.

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
