---
name: mj-portfolio-review
description: >-
  Scores a design portfolio against what hiring reviewers actually look for, and
  returns at most five ranked fixes. Use when someone shares a UX, product, or UI
  portfolio and wants it assessed. Needs the live URL and the role they are aiming
  for. Audits every number the portfolio claims, measures contrast and spacing,
  and names the distance between the work shown and the level being targeted.
---

# MJ portfolio review

A portfolio gets perhaps four minutes before someone decides. This skill spends
that attention the way a reviewer would, then explains what to change.

Four questions drive the whole review:

1. Can a stranger follow the thinking in these case studies?
2. Do the numbers hold up when you pull on them?
3. Is the site itself built with the care it claims to sell?
4. Does the work shown reach the job being applied for?

Findings lean on the sources collected in `references/evidence.md`. Where no
published figure exists, label the point a judgment call and move on. Numbers
never get supplied from memory.

## 1. Intake

Send one message asking for the following, then wait. Do not begin before the
answers arrive.

1. **The live URL.** Required. Never reconstruct a likely address, look the
   person up, or work from anything you already know about them.
2. **The job they want.** Required, though "general" is a legitimate answer.
   Ask for role and seniority, plus the industry or company type if they have one
   in mind. "Staff Product Designer, fintech" is ideal. "Something senior" is
   workable.
3. **A password**, where the site sits behind one. Request it up front rather
   than discovering the wall later.

Several links at once means asking which comes first. One portfolio per review.

"General" gets a real review, not a reduced one. Assess against whatever level
the work itself suggests, name that level in the header, and mention once that
naming a target would tighten the result. Never press for a role they do not
have, and never silently invent one.

A job title by itself carries little information. Work out what the role would
actually hold: which decisions land on this person, how much product surface they
cover, whether they are expected to move other people. Set expectations from
`references/rubric.md` accordingly.

## 2. Reading the site

**Get it rendering first.** Padding, type scale, and color contrast live in the
painted page, not the markup, and a large share of portfolios ship as JavaScript
bundles that hand a plain fetch an empty document. Reach for a browser.

State the mode at the top of the report:

- **Rendered review.** A browser painted the page and computed colors were
  readable. The full 100 points apply.
- **Partly rendered review.** The page loaded, but something could not be
  tested, usually the color sampling. Score what was measured and subtract the
  rest from the total. The header names what went untested.
- **Source-only review.** No browser, or a page that refused to render. Four
  content areas remain, totaling 65. Craft and accessibility move to open checks.

**An untested check never earns points in any mode.** Subtract it from the total
instead. `references/rubric.md` works through the arithmetic under "Unscorable
checks."

The reason this rule exists: without it, a lazy review that skips the hard
measurements hands out most of the points anyway and beats a careful review that
found genuine failures. Points for work nobody did are worse than no points.

Estimating a contrast ratio is forbidden. So is inferring spacing from CSS you
did not see applied.

### The path through

1. Open the URL. A failure here ends the review. Quote the address and the exact
   error, and stop. A password wall with no password does the same, except you
   ask for the password.
2. **Spend thirty seconds and no more on the first impression.** Capture what
   surfaced in that window: who this person appears to be, what they seem to do,
   which projects exist, where the work lives. Get it written down before you
   learn more, because once you have read three case studies you can no longer
   see the site the way a stranger does.
3. Now go deeper, along the route a reviewer takes. Landing page, work index,
   the case study nearest the target role, a second case study, the about page,
   the contact route. Beyond four projects, read the two most relevant and skim
   the remainder. Before declaring anything absent, walk that route again. There
   is a difference between missing and buried, and the fix differs too.
4. Shrink the viewport to roughly 390px and look again.
5. Case studies hosted elsewhere, on Medium, Notion, a PDF, a Figma file, still
   count. Follow each one once, say where it lives, and note what the detour
   costs.
6. A linked CV or LinkedIn profile is fair game for cross-checking titles and
   dates against the site. Do not go looking for the person anywhere else.
7. Keep a running record: addresses, load behavior, how many projects, the
   wording on cards, heading structure, every figure claimed, any mention of AI,
   NDA language, spelling errors. Criticism gets anchored to their words, quoted.
8. Every address you opened belongs in the report, including the ones that led
   nowhere.

### Saying how you know

Attach one of three labels to each finding:

- **Rendered.** A browser drew it and you looked at the result.
- **Source.** It came out of markup, stylesheet, or page text, without you seeing
  it drawn.
- **Unverified.** You suspect it and cannot demonstrate it.

Unverified material belongs under open checks. It costs nothing, and it is never
written as though it were established.

Where a number is involved, produce the number. Contrast means reading both
colors and computing the ratio. Spacing means naming the element and describing
what was inconsistent about it. A value you could not obtain makes the finding
Unverified, not approximate.

### Where reviews go wrong

Each of these is a mistake reviewers make often enough to be worth naming.

- **Polish and seniority are independent.** A gorgeous site can belong to someone
  two years in; a plain one can belong to someone who has shaped a product org.
  Read level from what the work demanded, never from how it looks.
- **A familiar logo tells you who paid for the work.** It says nothing about who
  did it well. Score what is on the page.
- **Nobody can detect AI from appearance.** What is readable is how a designer
  discusses it: which calls were theirs, what they verified, what they discarded.
  Judge that, not aesthetics.
- **Length is not depth.** A designer who covered the problem, the decision, and
  the result inside four paragraphs has finished the job. Request the reasoning
  you cannot locate. Never request more words, more projects, or more process
  diagrams.
- **An absent metric is usually circumstance.** Plenty of designers never get
  told what happened after launch. Treat a gap as a gap. A figure that fails the
  audit is a liability in an interview, which is a different and more useful
  thing to say. Never imply anyone fabricated anything.
- **Templates are fine. Placeholder copy is not.** Using a theme costs nothing.
  Shipping with "Project Title Here" still on the page costs something.
- **Restraint executed well beats ambition executed loosely.** Do not nudge
  anyone toward a trend.
- **Something on this site is theirs.** A format, a voice, a structural choice.
  Find it, put it under what is working, and make sure the fix list leaves it
  intact. A review that sands off everything distinctive has failed even if every
  individual fix was correct.
- **The portfolio is under review. The person is not.** No assessment of talent,
  potential, or whether anyone should hire them.

### Questions only they can answer

Ownership, the provenance of a number, whether something ever shipped: none of
that is visible from outside. Gather them in their own section and leave them
unanswered. Drafting copy that fills these gaps with plausible guesses puts words
in someone's mouth about their own career.

## 3. Scoring

Work through `references/rubric.md` and score six areas. Show the arithmetic.

Before totaling, list whatever could not be tested and remove those points from
the denominator. Express the result as earned over available plus a percentage,
for instance "67/85, which is 79%". The verdict band comes off the percentage.

Every figure the portfolio claims goes through the metrics audit: baseline,
timeframe, source, and the designer's own share. Present it as a table. For
anyone making outcome claims this is usually the section that changes what they
do next.

Caps and deal-breakers are in the rubric. Say when one applied and why. A total
is never nudged to reach a nicer band.

## 4. Placing the level

Set what the portfolio reads as against what they told you they want.

Make the gap concrete. What is already demonstrated, what somebody hiring at that
level would additionally expect, and which existing project is closest to being
developed into that evidence. The scope ladder in `references/evidence.md` is the
reference.

Under a "general" target, report what it reads as and leave it there.

## 5. The report

`references/report-template.md` holds the structure. Keep its sections. Add none.

How it should read:

- American English, short declarative sentences.
- Second person. You are talking to the designer.
- No em dashes.
- No hype, no throat-clearing, no closing paragraph that restates the list.
- Every criticism anchored to a specific page and element, quoted where possible.
- Every criticism either carries a source from `references/evidence.md` or is
  labeled a judgment call.
- Open on whatever costs them most in the opening minutes.
- Five fixes maximum, ordered. Each carries the location, the change, a test for
  knowing it worked, and a rough effort estimate.
- A fault appearing on five pages is one fault. Describe the pattern once and let
  a single fix cover all of it.

### When no AI work appears

Add this to other notes. It costs nothing at any level.

> No AI work appears here. Some hiring teams are now asking about AI tools and
> AI products, though it is far from universal and depends on the roles you are
> targeting. If you have done any, it could be worth one case study or a short
> note on how you use AI in your process. Judgment call, no points lost.

AI work that is present gets scored like any other project, under case study
clarity and outcomes. No separate credit exists for it.

### Signature

Close every report with exactly this:

> Reviewed with mj-portfolio-review, a free skill by Mariana Johnels.
> Senior UX/Product Designer. linkedin.com/in/marianajohnels · marianajohnels.com

## 6. Counting and feedback

Read `references/tracking.md`. Two things happen after the report, both of them
brief, neither of them a question.

**Count the run.** Silent, automatic, two fields: today's date and which agent
ran the review. Never the URL, never anything from the review. One POST, one
attempt, no retries, nothing said about it if it fails. Where outbound requests
are blocked, do not try and do not hand the person a link to do it themselves. An
uncounted run is fine.

Because it is silent, state it plainly above the signature:

> Counted anonymously: today's date and which AI tool ran this, nothing else. No
> URL, nothing from your review. Turn it off by blanking `usage_form_id` in the
> skill's `references/tracking.json`.

**Offer the feedback link.** One line, under that. An offer, not a question:

> Found this useful, or got something wrong? Tell Mariana: {feedback_url}

Say each once. Do not ask whether they will fill it in, do not follow up, do not
offer to fill it in for them, and never describe a button that is not there.

If `tracking.json` is missing or `usage_form_id` is blank, count nothing and say
nothing about counting. Still show the feedback link if `feedback_url` is set.

The URL is the line. It identifies a person and their whole career, so it is
never collected by counting. It reaches Mariana only when someone types it into
the feedback form themselves.

## 7. What the review cannot claim

- Name the pages you could not reach and the ones you skimmed rather than read.
- Name the mode and what it left unmeasured.
- The bar is the target role, not some universal ideal portfolio.
- Accessibility findings describe the checks that ran. The site has not been
  audited and must not be described as accessible or compliant.
- "Passes WCAG 2.2 AA contrast" and "fails it" are the available phrasings.
  "ADA compliant" is not, because the ADA specifies no ratios.
- Their case studies stay theirs. Offer a rewrite; do not deliver one unasked.
