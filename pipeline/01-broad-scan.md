# Stage 1 — Broad Scan

**Goal:** map the complete surface of a mentor's teachings — the **WHAT** — plus a brief
overview of who they are and why they matter. Breadth is everything here; depth comes in
Stage 2. A topic missed in the scan is a topic the mentor brain will never have.

**Input:** mentor name + the domain you want mentorship in.
**Output:** `mentors/<slug>/scan.md`

## Procedure

1. **Identify the person.** Disambiguate (same-name collisions are common). Record who
   they are, their track record, and why they're worth treating as a mentor in this domain.
2. **Map where they teach.** Every channel: YouTube, courses, books, podcasts (own and
   guest appearances), newsletters, blogs, talks, communities, social threads. For each,
   note roughly how much material exists and how teaching-dense it is.
3. **Inventory the teachings.** Sweep the material for:
   - Named frameworks, methods, and systems they've created or champion
   - Recurring themes and core beliefs they return to again and again
   - Tactical topic areas (e.g., for a freelancing mentor: pricing, client acquisition,
     contracts, scope creep, raising rates, firing clients...)
   - **How they teach** — their 1-on-1 style: questions they ask, how they give feedback,
     how they sequence a beginner vs an intermediate, what they push back on
   - Their own story arc (failures and turning points they teach from)
   - Common audience questions they answer and the shape of their answers
4. **Mark depth-vs-surface.** For each inventory item, note: do we already understand it,
   or does it need dedicated Stage 2 research? Be honest — the scan should *name* things
   accurately, not explain them.

## Quality bar

- Breadth over depth. A one-line accurate naming of a framework beats a paragraph
  guessing its content.
- No general knowledge. If the scan can't tie a topic to this specific mentor, it
  doesn't belong.
- Future-proof: write the scan so a stranger (or another agent) could read it cold and
  understand the mentor's teaching landscape.

## Output structure (`scan.md`)

```markdown
# Broad Scan: <Mentor Name>
Scanned: <date>

## Who they are and why they matter
<brief — credibility, track record, what makes them worth learning from>

## Where they teach
<channel inventory with volume/density notes>

## Teaching inventory
### Named frameworks & systems
### Recurring themes & core beliefs
### Tactical topic areas
### Teaching & mentoring style (observed)
### Their story arc
### Common audience questions

## Research needs
<the items above that need Stage 2 depth, grouped into candidate research areas>
```
