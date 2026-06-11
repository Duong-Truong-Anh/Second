# My Mentor

A workflow for turning an AI coding agent into a personal mentor, built on the documented
wisdom of real people you wish were mentoring you.

**The product is the workflow, not the mentors.** This repo gives you a repeatable pipeline
for researching any mentor's teachings, distilling them into a standardized "mentor brain,"
and running ongoing 1-on-1 mentorship sessions with continuity — memory of who you are,
what you've worked on, and where you're heading. The mentors included here are just
instances; the pipeline is the point.

## How it works

```
You name a mentor
        │
        ▼
┌─ 1. BROAD SCAN ────────────────────────────────────────────┐
│  Map the full surface of the mentor's teachings: the WHAT. │
│  Topics, frameworks, recurring themes, where they teach.   │
└────────────────────────────────────────────────────────────┘
        │
        ▼
┌─ 2. RESEARCH HANDOFFS ─────────────────────────────────────┐
│  Partition the scan into independent research briefs — the │
│  WHYs and HOWs. Each brief is self-contained and can be    │
│  run by any AI agent (subagent, another tool, a friend).   │
└────────────────────────────────────────────────────────────┘
        │
        ▼
┌─ 3. SYNTHESIS ─────────────────────────────────────────────┐
│  Findings come back → curated into a standardized mentor   │
│  brain: philosophy, playbook, teaching style, sources,     │
│  known gaps. Every claim traceable to a source.            │
└────────────────────────────────────────────────────────────┘
        │
        ▼
┌─ 4. SESSIONS ──────────────────────────────────────────────┐
│  /mentor <name> starts a 1-on-1 session. The mentor knows  │
│  you (mentee profile), remembers past sessions (progress   │
│  notes), and teaches the way the real mentor teaches.      │
└────────────────────────────────────────────────────────────┘
```

## Core principles

1. **Knowledge, not persona.** The mentor brain captures what a mentor knows, believes,
   and how they teach — it does not impersonate them. Sessions don't mimic voice or
   personality; they apply the mentor's actual frameworks and methods to your situation.
2. **Labeled blending.** When the documented material covers your situation, the mentor
   says so ("Jamie explicitly teaches X here"). When it doesn't, the mentor extrapolates
   from the mentor's principles and *labels it as extrapolation*. You always know what's
   sourced and what's inferred.
3. **Provenance everywhere.** Every claim in a mentor brain traces back to a source.
   No general-knowledge filler dressed up as the mentor's wisdom.
4. **Agent-agnostic by design.** The mentor brain and session protocol are plain markdown.
   The `/mentor` skill is just a thin adapter for Claude Code — any agent harness that can
   read and write files can run a session.

## Who this works for (prerequisite)

The workflow builds mentors from **publicly documented teaching**. Pick guiding voices
who show up online with substantial material — videos, courses, podcasts, books, talks.
A private coach, or someone known mainly by reputation with little documented teaching,
won't yield a usable brain; the pipeline's first stage checks for this and tells you
early. The hardest material — how they actually mentor 1-on-1 — needs *recorded
interactions* (coaching calls, live reviews, office hours); the pipeline treats this as
its strictest evidence requirement and will warn you when it can't find any.

## Repo layout

| Path | What it is |
|---|---|
| `pipeline/` | The workflow itself — stage instructions and templates. The product. |
| `mentors/<name>/` | One mentor: scan, research handoffs + findings, and the curated `brain/`. |
| `mentee/` | Who you are — shared across all mentorship tracks. |
| `workspace/<track>/` | One active mentorship: charter, progress notes, session logs. |
| `.claude/skills/` | `/mentor` (run a session) and `/mentor-build` (run the pipeline). |
| `DESIGN.md` | Design decisions log and open questions. |

## Quick start

1. Build a mentor: `/mentor-build <mentor name>` — runs the pipeline above.
2. Start mentorship: `/mentor <mentor name>` — first session is an intake; the mentor
   assesses where you are and sets up the track. Every later session picks up where
   you left off.
