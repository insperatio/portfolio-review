# Report template

Use this template. Keep the section names. Do not add sections. Drop a section
only when it would be empty, and say nothing about having dropped it.

```
# Portfolio review: {name or domain}

{URL} · reviewed {date}
Target role: {role and level, or "general, so judged as {band}"}
Mode: {Rendered review, all 100 points} / {Partly rendered, {n} points, {what was not assessed}} / {Source-only review, 65 points, no browser available}
Pages reviewed: {every page and off-site link you opened}

**Score: {n}/{points available}, which is {pct}%. {Verdict band}.**
{Two sentences. What a reviewer thinks after thirty seconds, and the one thing
holding it back most.}

**Why {points available}, not 100:** {Only when points were removed. Name each
check that could not be run and what it was worth. End with: those points were
left out rather than guessed, so this score covers only what was measured. Point
at Open checks. Omit this whole line when the total available was 100.}

**What your score means:** {pct}% is {band} ({range}). {One sentence on where
inside the band they sit and what would move them up a band.}

| Band | Range | |
|---|---|---|
| Send it | 85% to 100% | {You are here} |
| Send after fixes | 70% to 84% | {You are here} |
| Fix before sending | 50% to 69% | {You are here} |
| Rework | Under 50% | {You are here} |

{Mark one row only. Leave the other three cells empty.}

## The first 30 seconds
{What you could tell and what you could not, from the thirty-second look only.
Format and access in a line or two. Write this from the notes you took before
reading further.}

## Level read
{What the portfolio reads as, and the gap against the target they gave. Name
what is present, what a reviewer at that level would also expect, and the
nearest thing here that could close it. If they said "general," say what it
reads as and stop.}

## What's working
- {Strength, and where on the site.} [{Rendered / Source}] {Source: figure, or "judgment call".}
- Worth keeping: {a distinctive choice of theirs, and why it helps.}

## What's costing you
- {Problem, quoting or naming the page and element.} [{Rendered / Source}] {Source: figure, or "judgment call".}
- ...

## Metrics audit
{One row per number the portfolio claims. Omit this section if they claim none,
and say so in What's costing you if outcomes are missing entirely.}

| Claim | Where | Baseline | Timeframe | Source | Your share |
|---|---|---|---|---|---|
| "{their exact words}" | {page} | {yes / missing} | {yes / missing} | {yes / missing} | {yes / missing} |

{One line on what the gaps mean in an interview.}

## Accessibility check
{Only the checks you ran. Omit in a source-only review and say why in the header.}

| Check | What you measured | Result |
|---|---|---|
| Body text contrast | {fg} on {bg}, {size} | {ratio}:1, {passes / fails} 4.5:1 |
| Large text contrast | {fg} on {bg}, {size} | {ratio}:1, {passes / fails} 3:1 |
| Non-text contrast | {element} | {ratio}:1, {passes / fails} 3:1 |
| Alt text | {what you checked} | {result} |
| Heading order | {what you found} | {result} |
| Visible focus | {what you found} | {result} |

{One line: these are the checks run here, not a full audit.}

## Other notes
{Observations that are neither strengths nor problems: CV and LinkedIn match,
NDA handling, template use, mobile behavior, load time. Mark judgment calls as
such. Put the AI note here when no AI work appears.}

## Open checks
- {Unverified point, and how they can confirm it.} (No points lost.)

## Need from you
- {A fact only they can confirm: what they owned, where a number came from,
  whether it shipped.}

## Fix these first
1. {Page or element}: {the change}. Why: {one line, with a source or marked as a
   judgment call}. Done when: {how they will know it worked}. Effort: {small /
   medium / large}.
2. ...

{Five at most. Ranked by what costs them the most in the first few minutes.}

## Scoring

| Area | Points | Given |
|---|---|---|
| Case study clarity | 20 | {n} |
| Valid data and outcomes | 20 | {n} |
| Visual craft | {20, or only the points that were scorable} | {n} |
| First scan and organization | 15 | {n} |
| Accessibility | {15, or only the points that were scorable} | {n} |
| Role and level fit | 10 | {n} |
| **Total available** | **{the Points column added up}** | **{n}** |

{Both columns hold bare numbers. Never a word, never a phrase like "not
assessed" or "2 of 3 assessed". When checks could not be run, cut that area's
Points down to what was actually scorable and put the earned number beside it:
accessibility with twelve of fifteen points untested reads 3 and 2. The Points
column must add up to the total available and the Given column to the score, so
a reader can check the arithmetic. Name the untested checks under Open checks
and in the "Why {points available}, not 100" line, never inside this table.}

{Note any cap applied and why.}

{Optional, and only where a figure from evidence.md bears directly on something
this review found: one or two sentences of context, with the source named. Never
present a published figure as a comparison to this score. No published average
portfolio score exists. Omit entirely when nothing applies.}

The weights are this review's own, informed by Nielsen Norman Group, Meta
Design, Figma's design recruiter, VMware Design, and WCAG 2.2. They are not
endorsed by any of them.

{Counting line. Include ONLY when the run was actually counted. Omit the whole
line otherwise, including when counting was impossible. See SKILL.md section 7.}

---
Reviewed with mj-portfolio-review, a free skill by Mariana Johnels.
linkedin.com/in/marianajohnels · marianajohnels.com

Found this useful, or got something wrong? Tell Mariana: {feedback_url}
```

The feedback line is part of this template and is never dropped. The counting
line is the only conditional part of the closing.
