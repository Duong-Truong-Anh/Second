# Research Brief NN: <Topic> — <Mentor Name>

> You are a research agent. This brief is self-contained: everything you need is here.
> Do not assume access to any other files, briefs, or prior conversation.

## Mission
Research what **<Mentor Name>** teaches about **<topic>** — specifically the WHYs
(their reasoning, beliefs, and principles behind it) and the HOWs (their concrete
methods, steps, examples, and rules of thumb).

## Who the mentor is
<2–4 sentences copied/adapted from the scan: who they are, domain, why credible.
Enough for the agent to disambiguate them from similarly named people.>

## What we already know (from the broad scan)
<The scan's one-line namings relevant to this topic: framework names, recurring
phrases, where this topic shows up in their content. Include the scan's coverage
notes — items marked thin come with: "coverage looks shallow — confirm or report
as gap." This is the agent's trailhead.>

## Scope boundary
- **In scope:** <the precise territory of this brief>
- **Out of scope (covered by other research, do not pursue):** <bordering topics>

## Questions to answer
<Numbered, specific. Examples of the right altitude:>
1. What exact steps does the mentor prescribe for <X>? Quote them where possible.
2. WHY do they prescribe it that way — what reasoning or experience do they cite?
3. What mistakes do they warn about, and what stories do they tell about them?
4. How does their advice differ for a beginner vs someone established?

## Source guidance
<Known channels and specific videos/episodes/articles likely to cover this topic,
from the scan. The agent should go beyond these but start here.>

## Rules (non-negotiable)

1. **Mentor-specific only, graded by this evidence ladder.** Mark every claim:
   - `[stated-verbatim]` / `[stated-paraphrased]` — the mentor explicitly says it as
     advice or position.
   - `[demonstrated]` — the mentor shows it through examples, stories, or visible
     actions without naming it as advice. Admissible; cite the demonstration itself.
     Never report a demonstrated claim as stated.
   - `[reconstructed]` — a pattern you infer across their material, never stated or
     singly demonstrated. Requires ≥2 independent instances, all cited.
   - **Generic domain knowledge is forbidden.** Test: if the sentence would survive
     with the mentor's name swapped for any expert's and no citation breaks, cut it.
2. **Cite and date everything.** URL, video title + timestamp where possible, podcast
   episode, book + chapter — and publication date wherever recoverable.
3. **Currency check.** Mentors change their minds. Before reporting any major claim,
   search for later revisions or retractions ("I was wrong about", "I no longer
   recommend", newer content on the same topic). Report the mentor's *current*
   position as the finding; report superseded positions under Evolution & corrections.
4. **Report gaps as gaps.** "I could not find the mentor's position on X" is a valid
   and valuable finding. Never fill a gap with plausible invention.

## Output format
Return a markdown document:

```markdown
# Findings NN: <Topic> — <Mentor Name>
Researched: <date>

## Summary
<5–10 lines: the shape of what the mentor teaches here>

## Findings
### <Sub-topic>
<claims, each cited, dated, and marker-graded>

## Evolution & corrections   ← mandatory section
<positions the mentor has revised or retracted in this territory, with before/after
and dates — or "searched for revisions; none found">

## Quotes worth keeping
<the most teaching-dense direct quotes, cited>

## Gaps
<questions from the brief that could not be answered, and what was tried>

## Sources consulted
<full list with dates, including dead ends>
```
