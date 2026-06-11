# Second

> A *second* is what you call someone who is not the main act, but makes the main act
> possible. A second voice. A second opinion. A guiding one.

Second is a workflow for turning an AI agent into your personal mentor, built on the
documented wisdom of real people you wish were mentoring you. You are the main act;
this is your second.

**The product is the workflow, not the mentors.** This repo gives you a repeatable pipeline
for researching any mentor's teachings, distilling them into a standardized "mentor brain,"
and running ongoing 1-on-1 mentorship sessions with continuity — memory of who you are,
what you've worked on, and where you're heading. The mentors included here are just
instances; the pipeline is the point.

## How it works

```
┌─ 0. DEFINITION ────────────────────────────────────────────┐
│  Pin down WHO exactly, WHAT the mentorship is for, WHICH   │
│  era of the mentor matters, and WHERE you're starting.     │
└────────────────────────────────────────────────────────────┘
        │
        ▼
┌─ 1. BROAD SCAN ────────────────────────────────────────────┐
│  Map the full surface of the mentor's teachings: the WHAT. │
│  Topics, frameworks, junctions between topics, and a       │
│  source hunt for recorded 1-on-1 mentoring behavior.       │
└────────────────────────────────────────────────────────────┘
        │
        ▼
┌─ 2. RESEARCH HANDOFFS ─────────────────────────────────────┐
│  Partition the scan into independent research briefs — the │
│  WHYs and HOWs. Each brief is self-contained and runnable  │
│  by any engine: Claude subagents, Gemini Deep Research,    │
│  Perplexity, or a human. The findings format is the        │
│  contract; the engine is interchangeable.                  │
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
| `mentors/<name>/` | One mentor: definition, scan, research handoffs + findings, and the curated `brain/`. |
| `mentee/` | Who you are — shared across all mentorship tracks. |
| `workspace/<track>/` | One active mentorship: charter, progress notes, session logs. |
| `.claude/skills/` | `/mentor` (run a session) and `/mentor-build` (run the pipeline). |
| `DESIGN.md` | Design decisions log and open questions. |

## Quick start

1. Build a mentor: `/mentor-build <mentor name>` — opens with a short definition Q&A
   (who exactly, what for, which era of them), then runs the pipeline above.
2. Start mentorship: `/mentor <mentor name>` — first session is an intake; the mentor
   assesses where you are and sets up the track. Every later session picks up where
   you left off.
