# Stage 2 — Research Handoffs

**Goal:** turn the broad scan's "research needs" into independent, self-contained research
briefs covering the **WHYs** and **HOWs**, then run them — with as many agents as the
material requires.

**Input:** `mentors/<slug>/scan.md`
**Output:**
- Briefs: `mentors/<slug>/research/handoffs/NN-<topic>.md`
- Findings: `mentors/<slug>/research/findings/NN-<topic>.md` (same number, same topic)

## Partitioning rules

These rules are the heart of the pipeline. Each brief must satisfy all five:

1. **Independent.** An agent reading one brief cold — with no access to the scan, the
   other briefs, or this repo — has everything it needs. Copy the relevant scan context
   *into* the brief; never reference it.
2. **Minimal overlap.** Briefs partition the territory. Where two topics genuinely
   border each other, the brief states the boundary explicitly ("pricing strategy is
   covered elsewhere — do not research it").
3. **No general knowledge.** The brief instructs the agent to report only what *this
   mentor* says, does, or teaches. Generic domain advice is explicitly forbidden in
   findings. If the mentor's position can't be found, the correct finding is "not found,"
   not a plausible filler.
4. **Maximize accuracy.** Every finding must cite its source (URL, video + timestamp if
   possible, episode, book chapter). Direct quotes preferred over paraphrase for core
   claims. Confidence marked (verbatim / paraphrased / reconstructed-from-multiple-sources).
5. **Future-proof.** Briefs are plain markdown runnable by *any* AI agent — a Claude
   subagent, a different AI tool, or a human. No tool-specific or repo-specific
   instructions inside the brief.

Use `pipeline/templates/research-handoff.md` for every brief.

## Sizing

Let the scan decide the count. A topic gets its own brief when it's deep enough that
sharing an agent's attention would shallow it out. Typical mentor: 5–12 briefs. Always
include one brief dedicated to **teaching & mentoring style** (how they run 1-on-1
interactions, sequence learners, give feedback) — this is the hardest material to find
and the most valuable for sessions.

## Running the briefs

Two equivalent paths — the briefs don't care which:
- **Inside Claude Code:** spawn one research subagent per brief, passing the brief
  verbatim as the prompt.
- **Outside:** copy each brief into any other AI tool/agent and paste the result back
  into `research/findings/`.

## Acceptance check (per finding, before Stage 3)

- [ ] Every claim cited; cites are real and specific
- [ ] No generic domain advice (spot-check: would this sentence be true of *any* expert
      in the field? If yes and uncited, cut it)
- [ ] Gaps reported as gaps, not papered over
- [ ] Stayed inside its brief's scope boundary
