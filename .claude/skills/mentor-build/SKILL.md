---
name: mentor-build
description: Build a mentor brain by running the research pipeline (broad scan → independent research handoffs → synthesis). Use when the user wants to add a new mentor, says "/mentor-build <name>", "build a mentor", "research <person> as a mentor", or wants to refresh/extend an existing mentor brain.
---

# Build a Mentor Brain

Run the three-stage pipeline defined in `pipeline/`. The argument is the mentor's name;
if the mentorship domain isn't obvious or given, ask for it before starting.

## Stage 0 — Definition
1. Slugify the name (e.g. `jamie-brindle`) and create `mentors/<slug>/`.
2. If the mentor already exists, ask: refresh the scan, add research areas, or rebuild?
3. Run the Stage 0 Q&A per `pipeline/00-definition.md` — identity anchor, domain & goal,
   **era preference** (explain the drift problem: a mentor's newest teaching may target
   a different stage than the user needs; corrections always win regardless, the
   preference only arbitrates drift), and the mentee's starting point. Conversational,
   not a form. Write `mentors/<slug>/definition.md`.

## Stage 1 — Broad scan
Follow `pipeline/01-broad-scan.md` exactly (standards: `pipeline/evidence-standards.md`).
Use web search/fetch extensively — the scan lives or dies on breadth. Write
`mentors/<slug>/scan.md` in the prescribed structure, including the viability
assessment, coverage map, and the teaching-style **source hunt** (artifacts, not
summaries).

**Mandatory checkpoint — stop and report to the user:**
- Viability verdict (thin public footprint → recommend stopping).
- Teaching-style source verdict. **If no T1 artifacts (recorded real interactions)
  were found, warn explicitly:** continuing means a self-described/inferred style
  profile only. Offer: (a) user supplies private sources into
  `mentors/<slug>/research/user-sources/`, (b) proceed degraded, (c) skip the style
  brief. Do not proceed to Stage 2 without their answer.
- Coverage map + research candidates — they may know channels or topics the scan missed.

## Stage 2 — Research handoffs
Follow `pipeline/02-research-handoffs.md`:
1. **Partition first** (Stage 2 owns it; the scan only proposed). Apply the criteria,
   record the mapping in `research/handoffs/00-partition.md`.
2. Write topic briefs to `mentors/<slug>/research/handoffs/NN-<topic>.md` using
   `pipeline/templates/research-handoff.md` — self-contained, scope-bounded, currency
   rule and evidence ladder inlined.
3. Write the **teaching-style brief** using
   `pipeline/templates/research-handoff-observational.md`, pasting in the scan's
   source-hunt table plus any user-supplied sources (mandatory unless the user skipped
   it at the checkpoint).

Then ask the user which research engine to use (AskUserQuestion; see the engine table
in `pipeline/02-research-handoffs.md` Step 3 — summarize trade-offs honestly: Gemini =
widest sweep but verbose and robots-bound; Perplexity = best practical reach, ~3 free
Pro searches/day/account so multiple accounts are normal; Claude subagents = fully
automated but weakest web reach). Mixing engines across briefs is fine.

- **Claude subagents:** spawn one per brief in parallel, prompt = the brief verbatim
  plus: "When done, write your findings as a markdown report to
  `mentors/<slug>/research/findings/NN-<topic>.md`."
- **Gemini Deep Research:** append the Gemini verbosity adapter (from
  `02-research-handoffs.md`) to each handoff file, create the empty findings files,
  then guide the user step by step: one brief per fresh Deep Research instance →
  approve the research plan it proposes → when the report is ready, paste it into the
  matching findings file (into the file, not back into a prompt — it gets diluted).
- **Perplexity Search Pro:** same guided flow, one brief per fresh Pro search; remind
  the user that briefs are self-contained so spreading them across multiple accounts
  works, and conversations don't need to coexist in one account.

Remind the user of the video caveat: no engine watches video; for the observational
style brief, transcripts dropped into `research/user-sources/` are the highest-leverage
manual step.

Apply the acceptance check from `pipeline/02-research-handoffs.md` to each finding as
it arrives. Findings that fail (uncited claims, generic filler, missing mandatory
sections) get re-run or flagged, not synthesized.

## Stage 3 — Synthesis
Follow `pipeline/03-synthesis.md`. Build `mentors/<slug>/brain/` from the templates in
`pipeline/templates/mentor-brain/`. Verify the "done when" criteria, then summarize for
the user: what the brain covers, what's in `gaps.md`, and suggest starting with
`/mentor <slug>`.

## Throughout
- **Do not commit mentor artifacts.** `mentors/` is gitignored (personal data + a real
  person's distilled teachings — neither belongs in the public repo; see DESIGN.md D17).
  Stage boundaries (definition / scan / handoffs+findings / brain) are checkpoints to
  pause and verify at, not commits. Only commit if changes touched the tracked workflow
  (`pipeline/`, skills, docs) — or if the user runs a private fork that removed the
  ignore rules.
- Never let general knowledge masquerade as the mentor's teaching — the pipeline's
  value is provenance.
