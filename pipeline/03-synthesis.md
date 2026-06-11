# Stage 3 — Synthesis

**Goal:** curate the research findings into a standardized **mentor brain** — the durable
artifact sessions run on.

**Input:** `mentors/<slug>/scan.md` + all of `mentors/<slug>/research/findings/`
**Output:** `mentors/<slug>/brain/` following `pipeline/templates/mentor-brain/`

## Procedure

1. **Cross-check.** Read all findings. Where two findings touch the same claim, verify
   they agree. Where they conflict, prefer the better-sourced one and record the conflict
   in `sources.md` (mentors evolve — a 2019 position and a 2025 position can both be true).
2. **Distill, don't dump.** The brain is curated knowledge, not concatenated research.
   Organize by how a mentor would *use* it in a session, not by which agent found it.
3. **Preserve provenance.** Claim-level traceability survives synthesis: each section of
   the brain carries source references; `sources.md` is the master ledger.
4. **Map the gaps.** Everything a session might need that research did not find goes in
   `gaps.md` — this file is what powers honest labeled blending ("the mentor hasn't
   addressed this directly..."). A good gaps file is a feature, not an admission of failure.
5. **Write for the session, not the archive.** The brain's reader is a future agent
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
- Every load-bearing claim in `philosophy.md` and `playbook.md` traces to `sources.md`.
- `gaps.md` honestly lists what sessions will need to extrapolate on.
