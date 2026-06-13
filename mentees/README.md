# Mentees

Who you are, and the memory of every mentorship you run. One folder per mentee; inside
it, one folder per mentor you've consulted. The `/mentor` skill creates and maintains
all of this — this file documents the shape.

```
mentees/<mentee-name>/
├── profile.md                       # who I am — shared across ALL mentors
└── <mentor-slug>/                   # one per mentor this mentee consults
    ├── journey.md                   # the mentor's memory of this mentorship
    └── sessions/
        └── YYYY-MM-DD-NN-<topic>.md # append-only session logs
```

**Why nested this way.** Two kinds of memory have different lifetimes, so they live at
different levels:
- **Who you are** (name, situation, durable life facts) is true no matter which mentor
  you're talking to — it lives **once**, at `profile.md`, and every mentorship reads it.
- **Where you are in a mentorship** (stage, open commitments, what's been covered, the
  mentor's read on you) is specific to *that* mentor — it lives in that mentor's
  `journey.md`. Your pricing mentor and your fitness mentor remember different things
  about you.

This also makes the system multi-mentee (a family, a class, a team can each have a
folder) without the files colliding.

## profile.md
Cross-mentor identity. Created from `pipeline/templates/mentee-profile.md` at first
contact — **name first**, then situation and durable facts, captured conversationally
and written *early* in the first session (not saved up for the end). Built from
`pipeline/templates/mentee-profile.md`.

## journey.md
The mentor's live, current-state memory of one mentorship — calibration, open loops,
covered ground, the mentor's private read, and the next move. Read at the start of every
session, updated **incrementally** (sessions don't always reach a clean close). Built
from `pipeline/templates/journey.md`.

## sessions/
Append-only logs, one per session, built from `pipeline/templates/session-log.md`.
History; never rewritten. `journey.md` is the summary you read; these are the record.

---
**Everything in this folder except this README is gitignored** — it's your personal
mentorship history. (Private fork wanting version history? Remove the rule from
`.gitignore`.)
