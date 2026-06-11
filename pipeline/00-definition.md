# Stage 0 — Definition

**Goal:** pin down exactly *who* the mentor is, *what* the mentorship is for, *which
version* of the mentor matters, and *where* the mentee starts — before any research is
spent. A short Q&A between the agent and the user, not a research task.

**Input:** a mentor name and a rough intent.
**Output:** `mentors/<slug>/definition.md`

## Why this stage exists

Two failure modes are cheap to prevent here and expensive everywhere else:
1. **Wrong person.** Same-name collisions are common; a scan that disambiguates wrong
   wastes the entire pipeline.
2. **Wrong era.** "Latest position wins" (the currency rule) silently assumes the
   mentor's newest teaching is the most relevant. But mentors drift: the person who
   taught solo freelancing in 2018 may teach agency scaling in 2026, with nothing
   retracted — the old advice isn't *wrong*, it's aimed at a different stage. Which
   version the mentee needs is a user decision, and it must be made before research
   prioritizes sources.

## Questions to settle (conversationally — not a form)

1. **Identity anchor.** Full name plus distinguishing markers the user can confirm:
   a channel link, a known work, the domain they're famous in. The scan uses this to
   disambiguate.
2. **Domain and goal.** What the mentorship is for, in the user's words. This bounds
   the scan inventory and the Stage 2 partition — a mentor may teach five domains;
   research the one the mentee is here for (plus genuinely adjacent territory).
3. **Era / version preference.** Show the user the drift question explicitly:
   - *Current* — the mentor's present-day teaching (default).
   - *A defined earlier phase* — e.g., "when they were still a solo freelancer,
     pre-agency."
   - *Stage-matched* — the era when the mentor was closest to where the mentee wants
     to go next.
   Record the choice and the reasoning. **Note the arbitration rule it feeds:**
   corrections (the mentor says the old position was wrong) always resolve to the
   latest position regardless of this preference; the era preference only arbitrates
   *drift* — see `pipeline/evidence-standards.md`.
4. **Mentee starting point.** One honest paragraph: experience, constraints, what
   they've actually done (not read about). Seeds `mentee/profile.md` and tells
   research agents whether beginner or advanced material matters more.

## Output structure (`definition.md`)

```markdown
# Definition: <Mentor Name>
Defined: <date>

## Identity anchor
<name + confirmable markers>

## Domain & goal
<what this mentorship is for; explicit exclusions if any>

## Era preference
<current / earlier phase (which) / stage-matched — and why.
Reminder recorded: corrections always win; this preference arbitrates drift only.>

## Mentee starting point
<one paragraph>
```
