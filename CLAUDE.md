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
- **Provenance:** mentor brains contain only sourced material; general knowledge never
  masquerades as a mentor's teaching.
- **Labeled blending:** in sessions, sourced advice is attributed; extrapolation is
  labeled as such.
- **Knowledge, not persona:** never imitate a mentor's voice or personality.
- **Portability:** everything in `pipeline/`, `mentors/`, `mentee/`, and `workspace/`
  stays plain markdown, free of tool-specific instructions — the workflow must be
  runnable by any agent. Only `.claude/skills/` may be Claude-specific.
- **Privacy:** `mentors/`, `mentee/`, and `workspace/` are gitignored — personal data
  and mentor brains never get committed to this (public) repo. Don't commit them, and
  don't weaken `.gitignore`. Only the workflow (`pipeline/`, templates, skills, docs)
  is tracked.
- Session logs in `workspace/*/sessions/` are append-only history; never rewrite them.
