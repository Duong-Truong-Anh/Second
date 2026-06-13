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
│  brain: philosophy, playbook, voice, teaching style,       │
│  sources, known gaps. Every claim traceable to a source.   │
└────────────────────────────────────────────────────────────┘
        │
        ▼
┌─ 4. SESSIONS ──────────────────────────────────────────────┐
│  /mentor <name> starts a 1-on-1 session. The mentor knows  │
│  you (mentee profile), remembers this mentorship (journey   │
│  notes), speaks in the mentor's voice, and teaches the way  │
│  the real mentor teaches.                                   │
└────────────────────────────────────────────────────────────┘
```

## Core principles

1. **Knowledge and voice, not impersonation.** The brain captures what a mentor knows,
   believes, how they teach, *and how they talk* — and sessions speak in that voice
   (their register, phrasings, metaphors, sourced from their own content). What sessions
   never do is claim to *be* the mentor or invent their biography.
2. **Provenance lives in the brain, not the conversation.** Every claim traces to a
   source — that audit trail lives in the brain and the session logs. Sessions don't
   recite it; they speak with internalized authority. (Inline citations would make
   hard-won real-world advice read like a theory paper.)
3. **One spoken honesty signal: sourced vs extrapolated.** When the mentor's material
   covers your situation, you just get taught. When it doesn't — when the mentor extends
   their thinking onto something the real person never addressed — the session says so,
   naturally, so you always know what's sourced and what's inferred.
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
| `mentors/<name>/` | One mentor: definition, scan, research handoffs + findings, and the curated `brain/`. **Gitignored.** |
| `mentees/<name>/` | Who you are (`profile.md`), and per-mentor memory (`<mentor>/journey.md` + `sessions/`). **Gitignored.** |
| `.claude/skills/` | `/mentor` (run a session) and `/mentor-build` (run the pipeline). |
| `DESIGN.md` | Design decisions log and open questions. |

**Privacy boundary:** the repo tracks only the workflow. Your mentors, your profile,
and your session history are personal — they stay on your machine (gitignored). A
mentor brain is also a real person's distilled teachings, which isn't yours to
publish. If you run a private fork and want version history for these, remove the
ignore rules in `.gitignore`; the pipeline's stage boundaries make natural commit
points.

## Quick start

1. Build a mentor: `/mentor-build <mentor name>` — opens with a short definition Q&A
   (who exactly, what for, which era of them), then runs the pipeline above.
2. Start mentorship: `/mentor <mentor name>` — first session is an intake; the mentor
   assesses where you are and sets up the track. Every later session picks up where
   you left off.
