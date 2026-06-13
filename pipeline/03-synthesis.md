# Stage 3 — Synthesis

**Goal:** curate the research findings into a standardized **mentor brain** — the durable
artifact sessions run on.

**Input:** `mentors/<slug>/scan.md` + all of `mentors/<slug>/research/findings/`
**Output:** `mentors/<slug>/brain/` following `pipeline/templates/mentor-brain/`

**Standards:** apply `pipeline/evidence-standards.md` — markers and tiers survive
synthesis; they are not editorial decoration to be cleaned up.

## Procedure

1. **Cross-check and arbitrate.** Read all findings. Where two findings touch the same
   claim, verify they agree. Where they conflict: **corrections always resolve to the
   latest position; drift resolves to the era preference in `definition.md`** (see the
   currency rule in the standards). Better-sourced beats worse-sourced only when
   neither rule settles it. Every position not adopted is recorded in `sources.md`
   under evolution with its stage context — the brain teaches the adopted position and
   may cite the shift when instructive.
2. **Reassemble junctions.** Findings report cross-topic material under their
   "Junctions" sections, and edge duplication between briefs is expected — dedupe it
   here, keeping the best-sourced version. Every junction insight must be reachable
   from *both* of its topics in the brain: house it where it does its work, and
   cross-reference it from the other topic's section ("on pricing within ongoing
   client relationships, see ‹entry›").
3. **Distill, don't dump.** The brain is curated knowledge, not concatenated research.
   Organize by how a mentor would *use* it in a session, not by which agent found it.
4. **Preserve provenance and grading.** Claim-level traceability survives synthesis:
   each section carries source references, and evidence-ladder markers
   (`[stated]`/`[demonstrated]`/`[reconstructed]`) plus T1/T2/T3 tiers in
   `teaching-style.md` carry through — sessions use them to phrase attribution honestly.
5. **Map the gaps from two feeds.** `gaps.md` is seeded by (a) the scan's coverage map —
   every `[absent]` item lands here directly, no research needed to confirm an absence
   the scan documented — and (b) gaps reported in findings (including the style brief's
   "Not observed" section). This file powers labeled blending; a good gaps file is a
   feature, not an admission of failure.
6. **Honor the style profile's tier ceiling.** If the teaching-style findings are
   T2/T3-only (the user proceeded past the Stage 1 gate without T1 evidence),
   `teaching-style.md` must say so at the top, and sessions must present style-derived
   behavior as the mentor's self-description, not observed practice.
7. **Build the voice profile.** From the voice findings, synthesize `voice.md`:
   register, explanatory structure, signature metaphors/phrasings (kept *verbatim* —
   voice is in the exact words), vocabulary, and where they're blunt vs soft. This is
   the file that lets a session *sound* like the mentor instead of reading their notes.
   Keep the voice-vs-impersonation boundary explicit (see evidence-standards): it
   captures how they express, never their biography or unsourced positions.
8. **Write for the session, not the archive.** The brain's reader is a future agent
   mid-conversation with a mentee. Frameworks should be stated operationally (when to
   invoke, the steps, what good looks like), not historically.

## The brain files (see templates)

| File | Contents |
|---|---|
| `overview.md` | Who the mentor is, domains, why they're credible. The 2-minute read. |
| `philosophy.md` | Core beliefs and principles — the WHYs. What they'd never compromise on. |
| `playbook.md` | Frameworks, methods, tactics, workflows — the HOWs. Operational form. |
| `voice.md` | How they talk and explain — register, metaphors, phrasings. Sessions speak in it. |
| `teaching-style.md` | How they mentor 1-on-1: intake questions, feedback style, sequencing, pushback patterns. |
| `sources.md` | Master provenance ledger; conflicts and evolution noted. |
| `gaps.md` | What we know we don't have. Powers labeled blending. |

## Done when

- A stranger could run a credible first mentorship session from `brain/` alone.
- Every load-bearing claim in `philosophy.md` and `playbook.md` traces to `sources.md`,
  with its evidence-ladder marker intact.
- No superseded position appears as live advice; evolution is recorded in `sources.md`.
- `teaching-style.md` claims carry tiers, and its top states the overall evidence level.
- `voice.md` exists and quotes the mentor verbatim — enough for a session to speak in
  their register without impersonating them.
- `gaps.md` contains every `[absent]` item from the scan's coverage map plus all
  research-reported gaps — sessions can tell extrapolation from teaching *before* they
  open their mouth.
