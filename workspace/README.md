# Workspace

One folder per active mentorship track. A track = one mentor × one goal.
The `/mentor` skill creates and maintains these; this file documents the shape.

```
workspace/<track-slug>/            e.g. freelancing-jamie-brindle/
├── charter.md      # the deal: mentor, goal, where the mentee started, cadence
├── progress.md     # the mentor's memory — running state of the mentorship
└── sessions/
    └── YYYY-MM-DD-NN-<topic>.md   # one log per session
```

## charter.md
Written during the first session. Mentor name + brain path, the mentee's goal for this
track, starting-point assessment, agreed cadence and working style. Rarely changes;
when the goal itself shifts, update it and note the pivot.

## progress.md
The single file a session agent reads to know "where are we?" — current phase, what's
been covered, homework outstanding, wins, struggles, what the mentor planned to do
next. Includes a **calibration line**: the mentee's current stage in this track and
when it was last verified — sessions treat an old verification as a hypothesis to
re-check, not a fact. Updated at the end of **every** session at minimum; mid-session
updates are encouraged when the mentee visibly outgrows what's recorded. Keep it
current-state, not a diary — history lives in the session logs.

## Session logs
Each session ends by writing a log: what was discussed, advice given (marked sourced
vs extrapolated), decisions, homework assigned, and the mentor's private read on how
the mentee is doing. Logs are append-only history; never rewrite old ones.
