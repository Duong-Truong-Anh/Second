# Stage 2 — Research Handoffs

**Goal:** turn the broad scan into independent, self-contained research briefs covering
the **WHYs** and **HOWs**, then run them — with as many agents as the material requires.

**Input:** `mentors/<slug>/scan.md` (user-reviewed — the Stage 1 checkpoint has passed),
plus anything in `mentors/<slug>/research/user-sources/`.
**Output:**
- Briefs: `mentors/<slug>/research/handoffs/NN-<topic>.md`
- Findings: `mentors/<slug>/research/findings/NN-<topic>.md` (same number, same topic)

**Standards:** `pipeline/00-evidence-standards.md`. Briefs inline the rules they need —
a brief never references this repo.

## Step 1 — Partition (Stage 2 owns this, the scan only proposed)

Take the scan's research candidates as input, not as the answer. Apply these criteria:

1. **One brief ≈ one mentee-facing decision domain.** Partition by the situations a
   mentee brings to a session ("how do I price this project?"), not by source or media
   type. Where the mentor has named frameworks, prefer *their* boundaries — a brief per
   framework cluster beats a brief per generic topic label.
2. **Sized for one focused research run.** More than ~8 substantive questions, or two
   themes competing for attention → split. A brief that would produce two pages of
   findings → merge.
3. **`[thin]` items don't get their own briefs.** Attach each to its nearest domain
   brief with a note ("coverage looks shallow — confirm or report as gap").
4. **`[absent]` items get no brief at all.** They flow directly to `gaps.md` in Stage 3.
   Researching a documented absence wastes an agent.
5. **Unplaced items** from the scan get resolved here: assigned, merged, or consciously
   dropped (note why).

Record the final partition at the top of the handoffs folder in `00-partition.md`:
which scan items map to which brief, and what was dropped. This is what makes the
partition auditable and re-runnable later.

## Step 2 — Write the briefs

Each brief must satisfy all five rules:

1. **Independent.** An agent reading one brief cold — with no access to the scan, the
   other briefs, or this repo — has everything it needs. Copy the relevant scan context
   *into* the brief; never reference it.
2. **Minimal overlap.** Briefs partition the territory. Where two topics genuinely
   border each other, the brief states the boundary explicitly ("pricing strategy is
   covered elsewhere — do not research it").
3. **No general knowledge.** Findings report only what *this mentor* says, does, or
   teaches, graded by the evidence ladder (stated / demonstrated / reconstructed —
   the template inlines the definitions). If the mentor's position can't be found,
   the correct finding is "not found," not a plausible filler.
4. **Maximize accuracy and currency.** Every finding cited (URL, video + timestamp if
   possible, episode, book chapter) and dated. Every brief carries the currency rule:
   before reporting a major claim, check for later revision or retraction; findings
   include a mandatory "Evolution & corrections" section.
5. **Future-proof.** Briefs are plain markdown runnable by *any* AI agent — a Claude
   subagent, a different AI tool, or a human. No tool-specific or repo-specific
   instructions inside the brief.

Use `pipeline/templates/research-handoff.md` for topic briefs.

### The teaching-style brief is different

It uses `pipeline/templates/research-handoff-observational.md` and is **mandatory**
(unless the user skipped it at the Stage 1 checkpoint). Differences from topic briefs:

- **It starts from the scan's source-hunt table** (plus anything in `user-sources/`),
  pasted into the brief. The agent's job is observation and analysis of those
  artifacts, not open-web search — though it may add newly found T1 artifacts.
- **Collections expand.** If a listed source is a collection (playlist of coaching
  calls, a recurring "roast" series), the agent enumerates the members and mines every
  one that shows real interaction. The scan lists the playlist; the brief's agent
  watches the sessions.
- **Behavior extraction protocol:** for each artifact, record concrete instances as
  *situation → the mentor's move → outcome* (what they did when someone was stuck,
  what they asked when someone was confused, how they adjusted when advice wasn't
  landing). Generalizations come only afterward: a pattern requires ≥2 independent
  instances and cites them all; single instances stay reported as instances.
- **Tier discipline:** every claim carries T1/T2/T3. T2 self-descriptions may be
  *corroborated or contradicted* by T1 observations — contradictions are findings gold;
  report them explicitly.

## Step 3 — Run the briefs

Two equivalent paths — the briefs don't care which:
- **Inside Claude Code:** spawn one research subagent per brief, prompt = the brief file
  verbatim. Run them in parallel.
- **Outside:** copy each brief into any other AI tool/agent and paste the result back
  into `research/findings/`.

## Step 4 — Acceptance check (per finding, before Stage 3)

- [ ] Every claim cited, dated where recoverable, and marked
      (`[stated-verbatim]` / `[stated-paraphrased]` / `[demonstrated]` / `[reconstructed]`;
      teaching-style findings additionally T1/T2/T3)
- [ ] "Evolution & corrections" section present and substantive (an explicit
      "no changes found" after searching counts; an omitted section doesn't)
- [ ] No generic domain advice (spot-check: would this sentence survive with the
      mentor's name swapped out? If yes and uncited, cut)
- [ ] Gaps reported as gaps, not papered over
- [ ] Stayed inside its brief's scope boundary

Findings that fail get re-run or flagged to the user — never quietly synthesized.
