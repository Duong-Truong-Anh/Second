# Second — repo guide

This repo is **Second**: a workflow for building AI mentors from real people's
documented teachings and running ongoing 1-on-1 mentorship sessions. Read `README.md`
for the concept, `DESIGN.md` for decisions and open questions.

## Two modes — keep them separate
1. **Sessions IN the system:** the user invokes `/mentor <name>` (run a session) or
   `/mentor-build <name>` (research + build a mentor brain). Follow those skills.
2. **Work ON the system:** anything else — improving the pipeline, templates, skills,
   or design. Treat `DESIGN.md` as the decision log: record significant decisions there,
   and check its open questions before re-debating something.

## Hard rules (apply in both modes)
- **Provenance lives in the artifact, not the conversation:** mentor brains contain only
  sourced material (general knowledge never masquerades as a mentor's teaching), and the
  brain carries the audit trail — markers, the sources ledger, gaps. Sessions do *not*
  recite it: they speak with internalized authority. See DESIGN.md D18.
- **The one spoken honesty signal is sourced-vs-extrapolated**, voiced naturally and only
  when crossing into what the brain doesn't cover. Never present extrapolation as the
  mentor's documented position.
- **Knowledge and voice, not impersonation:** sessions speak in the mentor's voice (their
  register/phrasings — well-sourced from monologue content, captured in `voice.md`). They
  never claim to *be* the mentor or invent their biography. (Refines the older
  "knowledge, not persona" rule — see DESIGN.md D18.)
- **Portability:** everything in `pipeline/`, `mentors/`, and `mentees/` stays plain
  markdown, free of tool-specific instructions — the workflow must be runnable by any
  agent. Only `.claude/skills/` may be Claude-specific.
- **Privacy:** `mentors/` and `mentees/` are gitignored — personal data and mentor brains
  never get committed to this (public) repo. Don't commit them, and don't weaken
  `.gitignore`. Only the workflow (`pipeline/`, templates, skills, docs) is tracked.
- Session logs in `mentees/*/*/sessions/` are append-only history; never rewrite them.
