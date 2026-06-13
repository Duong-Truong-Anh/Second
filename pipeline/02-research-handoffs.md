# Stage 2 — Research Handoffs

**Goal:** turn the broad scan into independent, self-contained research briefs covering
the **WHYs** and **HOWs**, then run them — with as many agents as the material requires.

**Input:** `mentors/<slug>/scan.md` (user-reviewed — the Stage 1 checkpoint has passed),
plus anything in `mentors/<slug>/research/user-sources/`.
**Output:**
- Briefs: `mentors/<slug>/research/handoffs/NN-<topic>.md`
- Findings: `mentors/<slug>/research/findings/NN-<topic>.md` (same number, same topic)

**Standards:** `pipeline/evidence-standards.md`. Briefs inline the rules they need —
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
6. **Every junction gets an explicit home.** Each cross-topic junction from the scan is
   assigned to exactly one brief — usually the topic where the insight does its work,
   not where the mentor happened to say it. A junction without an assignment is a
   partition bug: neither brief will claim it, neither will find it.

Record the final partition at the top of the handoffs folder in `00-partition.md`:
which scan items map to which brief, **which brief owns each junction**, and what was
dropped. This is what makes the partition auditable and re-runnable later.

## Step 2 — Write the briefs

Each brief must satisfy all five rules:

1. **Independent.** An agent reading one brief cold — with no access to the scan, the
   other briefs, or this repo — has everything it needs. Copy the relevant scan context
   *into* the brief; never reference it.
2. **Exclusive centers, shared edges.** Briefs own their core territory exclusively —
   the boundary clause names neighboring *centers* as off-limits ("pricing strategy
   is another agent's core — do not research it for its own sake"). But edges are
   shared: material that links this brief's topic to another is in scope when it
   illuminates this topic, and gets reported under a "Junctions" section rather than
   dropped. Some duplication at the edges is expected and welcome — synthesis dedupes;
   nothing dedupes an insight nobody captured.
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

### The voice brief is also required

It uses `pipeline/templates/research-handoff-voice.md` and is **mandatory** — sessions
speak in the mentor's voice, and skipping this is what makes a mentor feel like a
generic agent reading notes. Unlike the teaching-style brief, voice is **well-sourced**:
it mines the mentor's high-volume *monologue* content (videos, posts, talks) for
register, metaphors, phrasings, and explanatory structure — not 1-on-1 interaction. It
captures *how they sound*, not *what they teach* (the topic briefs own the content) and
not *how they mentor* (the teaching-style brief owns behavior). Quote verbatim — voice
lives in exact words, and paraphrase destroys it. This brief can run lighter than the
topic briefs; its goal is texture, not coverage.

## Step 3 — Choose a research engine and run

Briefs are engine-agnostic: **the findings format is the contract; the engine is
interchangeable.** Engines differ sharply in reach (robots.txt policy, paywall
handling, search depth), so the orchestrating agent presents the options and the user
chooses. Mixing engines across briefs of the same mentor is fine.

| Engine | Strengths | Limits & cost |
|---|---|---|
| **Gemini Deep Research** | Widest sweep: multi-stage research plan over many sources in parallel. Best for sprawling topics. | Obeys robots.txt strictly (anti-AI-blocked sites invisible); hard paywall stop. Reports come back long and academic — use the verbosity adapter below. |
| **Perplexity Search Pro** | Strong practical reach (aggressive about blocks), condensed output close to the findings format already. | Free tier: ~3 Pro searches/day/account. Briefs are self-contained, so spreading them across multiple accounts works fine — conversations don't need to share an account. |
| **Claude subagents** | Fully automated: spawned in parallel, write their own findings files, no copy-paste. | Most restrictive web reach (sandboxed cite-then-fetch, no paywalls/cookies). Fine for well-indexed mentors; weakest for obscure ones. |

**Guided flow per path:**
- **Subagents:** spawn one per brief; prompt = the brief verbatim plus one line:
  "When done, write your findings as a markdown report to
  `mentors/<slug>/research/findings/NN-<topic>.md`."
- **External engine (Gemini or Perplexity):** the orchestrating agent first appends the
  engine adapter (below) to each brief, creates the empty findings files with their
  headers, then walks the user through it: paste one brief per **fresh instance**;
  for Gemini, approve the research plan it proposes; when the report is ready, copy
  it into the matching findings file — **into the file, not back into a prompt**,
  where it gets diluted.

### Engine adapters (appended to each brief before copying)

**Gemini Deep Research:**
> Final report requirements: maximum ~1,500 words. Plain, direct language — no academic
> framing, no literature-review padding. Follow the brief's "Output format" structure
> exactly. Keep every citation and date; trim prose, never sources.

**Perplexity:** usually none needed. If a response comes back thin, ask follow-ups in
the same thread for the brief's unanswered questions before moving on.

**Video caveat (applies to all engines):** none of them actually *watch* video — they
work from transcripts, descriptions, and discussions. This matters most for the
observational teaching-style brief. Where transcripts exist, point the brief's source
list at them; where they don't, fetching transcripts into
`mentors/<slug>/research/user-sources/` before running the style brief is the single
highest-leverage manual step in the whole pipeline.

## Step 4 — Acceptance check (per finding, before Stage 3)

- [ ] Every claim cited, dated where recoverable, and marked
      (`[stated-verbatim]` / `[stated-paraphrased]` / `[demonstrated]` / `[reconstructed]`;
      teaching-style findings additionally T1/T2/T3)
- [ ] "Evolution & corrections" section present and substantive (an explicit
      "no changes found" after searching counts; an omitted section doesn't)
- [ ] "Junctions" section present; assigned junctions from `00-partition.md` were
      pursued (found or reported as not found — not silently skipped)
- [ ] No generic domain advice (spot-check: would this sentence survive with the
      mentor's name swapped out? If yes and uncited, cut)
- [ ] Gaps reported as gaps, not papered over
- [ ] Stayed inside its brief's scope boundary

Findings that fail get re-run or flagged to the user — never quietly synthesized.
