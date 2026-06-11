# Stage 1 — Broad Scan

**Goal:** map the complete surface of a mentor's teachings — the **WHAT** — plus a brief
overview of who they are and why they matter. Breadth is everything here; depth comes in
Stage 2. A topic missed in the scan is a topic the mentor brain will never have.

One exception to "breadth only": **teaching style is not scanned, it is source-hunted**
(step 4). Summarizing mentoring behavior from a distance produces surface observations
("they ask diagnostic questions") that poison Stage 2; what Stage 2 needs is a list of
artifacts where the behavior is actually visible.

**Input:** `mentors/<slug>/definition.md` (Stage 0 — identity anchor, domain & goal,
era preference, mentee starting point).
**Output:** `mentors/<slug>/scan.md`
**Standards:** apply `pipeline/evidence-standards.md` throughout.

## Procedure

1. **Identify the person and check viability.** Confirm the identity anchor from
   `definition.md` (same-name collisions are common — verify against the user's
   confirmable markers). Record who they are, their track record, and why they're
   worth treating as a mentor in this domain. Then assess the public footprint: this workflow only works
   for people whose teaching is publicly documented. If the footprint is thin (a private
   coach, an author of one book, someone known mostly by reputation), say so *now* —
   recommend against proceeding rather than letting twelve research briefs fail slowly.
2. **Map where they teach.** Every channel: YouTube, courses, books, podcasts (own and
   guest appearances), newsletters, blogs, talks, communities, social threads. For each:
   rough volume, teaching density, and **date range** (the currency rule starts here —
   undated material is hard to arbitrate later).
3. **Inventory the teachings.** Sweep the material for:
   - Named frameworks, methods, and systems they've created or champion
   - Recurring themes and core beliefs they return to again and again
   - Tactical topic areas (e.g., for a freelancing mentor: pricing, client acquisition,
     contracts, scope creep, raising rates, firing clients...)
   - **Self-corrections & changed positions** — "I was wrong about", "I no longer
     recommend", older advice they've publicly revised. Breadth search *can* find these
     when it looks for them, and Stage 2's currency checks depend on this head start.
   - Their own story arc (failures and turning points they teach from)
   - Common audience questions they answer and the shape of their answers
   - **Cross-topic junctions** — insights that exist only where two topics meet: the
     thing they say about pricing only when discussing client relationships, the thing
     about creative process that only surfaces when they talk about failure. Record the
     topic pair, the insight in one line, and where it was observed. These are
     first-class inventory items, not footnotes to either topic — a partition that
     never sees them will lose them (Stage 2 assigns each junction to a brief
     explicitly).

   Tag every inventory item twice:
   - **Evidence type** from the ladder: `[stated]`, `[demonstrated]`, or `[reconstructed]`
   - **Coverage state:** `[covered]` (real material exists), `[thin]` (mentioned but
     shallow), or `[absent]` (a topic a mentee will plausibly need that this mentor
     demonstrably does not cover — yes, inventory the absences; they seed `gaps.md`
     and tell sessions exactly when they're extrapolating)
4. **Hunt teaching-style sources.** Do not summarize their mentoring style. Instead,
   find artifacts where 1-on-1 (or live, individual) teaching behavior is *visible*:
   coaching call recordings, live reviews/roasts of audience members' work, office
   hours, back-and-forth Q&As, student critiques, workshop recordings. For each
   artifact record: what it is, the evidence tier (T1/T2/T3 per the standards), what
   interaction is visible, and whether it's a single artifact or a **collection**
   (a playlist, series, or recurring format — collections are noted as such; Stage 2
   enumerates and mines every member). T2 self-descriptions and T3 structural evidence
   are listed too, but separately — they don't satisfy the gate.
5. **Propose research candidates.** Group `[covered]` and `[thin]` items into candidate
   research areas. These are **proposals only — Stage 2 owns the final partition**
   (see `02-research-handoffs.md` for the partitioning criteria). When in doubt, don't
   force a grouping; flag the item as unplaced.

## Quality bar

- Breadth over depth. A one-line accurate naming of a framework beats a paragraph
  guessing its content.
- Evidence ladder applies even at scan altitude: no generic domain knowledge, and
  demonstrated/reconstructed items marked as such, not silently promoted.
- Future-proof: write the scan so a stranger (or another agent) could read it cold and
  understand the mentor's teaching landscape.

## Output structure (`scan.md`)

```markdown
# Broad Scan: <Mentor Name>
Scanned: <date>

## Who they are and why they matter
<brief — credibility, track record, what makes them worth learning from>

## Viability assessment
<public footprint verdict: strong / workable / too thin (recommend stopping)>

## Where they teach
<channel inventory with volume, density, and date-range notes>

## Teaching inventory
<every item tagged [stated|demonstrated|reconstructed] + [covered|thin|absent]>
### Named frameworks & systems
### Recurring themes & core beliefs
### Tactical topic areas
### Self-corrections & changed positions
### Their story arc
### Common audience questions
### Cross-topic junctions
<topic pair · the insight in one line · where observed>

## Teaching-style source hunt
| # | Artifact | Tier | Single/Collection | What interaction is visible | Link |
**Verdict:** T1 evidence found / NOT found

## Coverage map
**Covered:** <list> · **Thin:** <list> · **Absent:** <list>

## Research candidates (proposals — Stage 2 owns the partition)
<groupings + unplaced items>
```

## Checkpoint — stop and report to the user (mandatory)

Stage 2 does not start until the user has seen:
1. The viability verdict.
2. **The teaching-style source verdict.** If no T1 artifacts were found, warn explicitly:
   continuing means the style profile will be self-described/inferred only (T2/T3),
   and sessions will have to label it that way. Ask whether the user has private
   sources to contribute (call recordings, course communities, paywalled material —
   drop them in `mentors/<slug>/research/user-sources/`), wants to proceed degraded,
   or wants to skip the style brief.
3. The coverage map and research candidates — the user may know channels or topics
   the scan missed.
