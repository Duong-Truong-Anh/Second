# Mentors

One folder per mentor, produced by the pipeline (`/mentor-build <name>`):

```
mentors/<slug>/
├── definition.md      # Stage 0 — who exactly, what for, which era, your starting point
├── scan.md            # Stage 1 — broad scan + teaching-style source hunt + coverage map
├── research/
│   ├── handoffs/      # Stage 2 — 00-partition.md + self-contained research briefs
│   ├── findings/      # research reports, one per brief
│   └── user-sources/  # material you supply (transcripts, recordings, notes)
└── brain/             # Stage 3 — the curated mentor brain sessions run on
```

**Everything in this folder except this README is gitignored.** Mentor brains contain
your personal context (the definition records who you are and where you're starting)
and distilled material from a real person's teachings — neither belongs in a public
repo. The workflow that builds them is the product; the brains are yours.

If you run a private fork and want version history for your mentor builds, remove the
`/mentors/*` lines from `.gitignore` — the pipeline's stage boundaries (definition →
scan → handoffs+findings → brain) make natural commit points.
