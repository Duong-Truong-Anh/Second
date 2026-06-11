# Stage 3 — Synthesis

**Goal:** curate the research findings into a standardized **mentor brain** — the durable
artifact sessions run on.

**Input:** `mentors/<slug>/scan.md` + all of `mentors/<slug>/research/findings/`
**Output:** `mentors/<slug>/brain/` following `pipeline/templates/mentor-brain/`

**Standards:** apply `pipeline/00-evidence-standards.md` — markers and tiers survive
synthesis; they are not editorial decoration to be cleaned up.

## Procedure

1. **Cross-check and arbitrate by date.** Read all findings. Where two findings touch
   the same claim, verify they agree. Where they conflict, the **latest dated position
   wins** (currency rule); better-sourced beats worse-sourced only when dates can't
   settle it. Every superseded position is recorded in `sources.md` under evolution —
   the brain teaches the current position and may cite the shift when instructive.
2. **Distill, don't dump.** The brain is curated knowledge, not concatenated research.
   Organize by how a mentor would *use* it in a session, not by which agent found it.
3. **Preserve provenance and grading.** Claim-level traceability survives synthesis:
   each section carries source references, and evidence-ladder markers
   (`[stated]`/`[demonstrated]`/`[reconstructed]`) plus T1/T2/T3 tiers in
   `teaching-style.md` carry through — sessions use them to phrase attribution honestly.
4. **Map the gaps from two feeds.** `gaps.md` is seeded by (a) the scan's coverage map —
   every `[absent]` item lands here directly, no research needed to confirm an absence
   the scan documented — and (b) gaps reported in findings (including the style brief's
   "Not observed" section). This file powers labeled blending; a good gaps file is a
   feature, not an admission of failure.
5. **Honor the style profile's tier ceiling.** If the teaching-style findings are
   T2/T3-only (the user proceeded past the Stage 1 gate without T1 evidence),
   `teaching-style.md` must say so at the top, and sessions must present style-derived
   behavior as the mentor's self-description, not observed practice.
6. **Write for the session, not the archive.** The brain's reader is a future agent
   mid-conversation with a mentee. Frameworks should be stated operationally (when to
   invoke, the steps, what good looks like), not historically.

## The brain files (see templates)

| File | Contents |
|---|---|
| `overview.md` | Who the mentor is, domains, why they're credible. The 2-minute read. |
| `philosophy.md` | Core beliefs and principles — the WHYs. What they'd never compromise on. |
| `playbook.md` | Frameworks, methods, tactics, workflows — the HOWs. Operational form. |
| `teaching-style.md` | How they mentor 1-on-1: intake questions, feedback style, sequencing, pushback patterns. |
| `sources.md` | Master provenance ledger; conflicts and evolution noted. |
| `gaps.md` | What we know we don't have. Powers labeled blending. |

## Done when

- A stranger could run a credible first mentorship session from `brain/` alone.
- Every load-bearing claim in `philosophy.md` and `playbook.md` traces to `sources.md`,
  with its evidence-ladder marker intact.
- No superseded position appears as live advice; evolution is recorded in `sources.md`.
- `teaching-style.md` claims carry tiers, and its top states the overall evidence level.
- `gaps.md` contains every `[absent]` item from the scan's coverage map plus all
  research-reported gaps — sessions can tell extrapolation from teaching *before* they
  open their mouth.
