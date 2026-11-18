# mj-portfolio-review

[![skills.sh](https://skills.sh/b/insperatio/portfolio-review)](https://skills.sh/insperatio/portfolio-review)

A free agent skill that reviews a UX, product, or UI design portfolio and returns
a scored report with at most five ranked fixes.

It asks for your portfolio URL and the role you are targeting, reads the site and
its case studies, audits the numbers you claim, checks spacing, type hierarchy,
and WCAG 2.2 AA contrast, then scores it out of 100.

Built by [Mariana Johnels](https://marianajohnels.com), a senior UX and product
designer. Free, MIT licensed, and your portfolio URL is never collected.

## Install

```sh
npx skills add insperatio/portfolio-review
```

Works with Claude Code, Cursor, Codex, and other agents the
[skills CLI](https://www.skills.sh/docs) supports.

**On Claude.ai**, download or clone this repo and upload the
`skills/mj-portfolio-review` folder as a skill. Note that Claude.ai cannot render
a page in a browser, so the review runs in source-only mode and scores out of 65.
See "Two modes" below.

Then ask for a review:

> Review my portfolio at example.com. I'm targeting a Senior Product Designer
> role at a B2B SaaS company.

## What it checks

| Area | Points |
|---|---|
| Case study clarity | 20 |
| Valid data and outcomes | 20 |
| Visual craft | 20 |
| First scan and organization | 15 |
| Accessibility | 15 |
| Role and level fit | 10 |

**Case study clarity** is judged against the seven parts Nielsen Norman Group
recommends, without treating them as a checklist. A short case study that shows
the problem, the decisions, the role, and the result scores well.

**Valid data and outcomes** runs a metrics audit. Every number you claim is
checked for four things: a baseline, a timeframe, a source, and your share of the
result. "Increased conversion 23%" with none of those is the single most common
thing that collapses under questioning in an interview.

**Visual craft** looks at spacing consistency, type hierarchy, body text
legibility, alignment, image treatment, and typos. Plain is not a deduction and
bold is not a bonus.

**Accessibility** checks text contrast against 4.5:1, large text and non-text
contrast against 3:1, alt text, heading order, and visible focus. The report says
"passes WCAG 2.2 AA contrast" or "fails it" on the specific checks it ran. It
never says "ADA compliant," because the ADA does not set contrast ratios.

**Role and level fit** compares the scope shown against the role you are
targeting, and names the gap.

Verdict bands: 85 and up send it, 70 to 84 send after fixes, 50 to 69 fix before
sending, under 50 rework.

The point values are this skill's own judgment. They are not endorsed by any of
the sources below.

## Two modes

Spacing and contrast cannot be judged from source HTML, and many portfolios are
JavaScript applications that return an empty page to a plain fetch. So the report
always says which mode it ran in.

- **Rendered review.** A browser loaded the page and could read its computed
  colors. All 100 points are scored.
- **Partly rendered review.** A browser loaded the page but some check could not
  be run, usually reading the colors for contrast. Those points leave the total.
- **Source-only review.** No browser was available. The four content areas are
  scored, out of 65, and visual craft and accessibility move to "Open checks."

In every mode, **a check that was not run is never scored.** Its points come out
of the total instead of being awarded. Otherwise a review that measures nothing
would rate a portfolio higher than one that measures everything and finds real
failures. Scores are always shown as given over available, with the percentage.

## How it handles evidence

Every finding is tagged **Rendered** (seen live in a browser), **Source** (read in
the HTML or text), or **Unverified** (likely but not confirmed). Unverified
findings go under "Open checks," cost no points, and are never stated as
problems.

Facts only you can confirm, such as what you owned or where a number came from,
go under "Need from you." The skill does not write replacement copy that guesses
them.

It will not infer your seniority from how polished the site looks, treat a
well-known client as proof of quality, ask you for longer case studies, or accuse
you of inventing a metric.

## Privacy

**What is collected automatically:** two fields at the end of each review, the
date and which AI assistant ran it. That is the whole thing. It tells Mariana
whether anyone uses this, which is the only reason it exists.

**What is never collected automatically:** your portfolio URL, your score, the
findings, the fixes, your target role, your seniority, your name, your email, or
any part of the conversation. Your URL identifies you and your entire work
history, so the skill does not take it.

**To turn counting off**, blank out `usage_form_id` in
[`references/tracking.json`](skills/mj-portfolio-review/references/tracking.json).
The skill then sends nothing and says nothing about it. On claude.ai nothing is
sent regardless, because that environment cannot make outbound requests, and the
skill does not ask you to submit a count by hand.

**Feedback is separate and voluntary.** Every report ends with a link. If you
open it, you can say what would make the skill better, what the review got wrong,
and optionally leave your portfolio URL, a name, and an email. The email is used
only for whichever boxes you tick on the form, and nothing else.

That split is deliberate. A URL you type into a feedback form is given. The same
URL taken silently at the end of a review is taken. The code that does both is in
[`references/tracking.md`](skills/mj-portfolio-review/references/tracking.md), so
you can check that this description is true rather than trusting it.

## Credits

The review judgment, rubric, and point weights are this skill's own. The
mechanics it borrows are credited here.

- **[UXfolio, State of UX Portfolios 2026](https://uxfol.io/state-of-ux-portfolios-2026/report)**,
  a survey of more than 100 hiring managers and design leaders. Only figures read
  directly from the report are cited, and they are marked as theirs. Not
  affiliated with UXfolio.
- **[Nielsen Norman Group](https://nngroup.com/articles/ux-design-portfolios/)**,
  on case study structure and project count, from a survey of 204 UX
  professionals who hire.
- **[Meta Design](https://www.meta.com/design-at-meta/blog/5-ways-to-improve-your-design-portfolio-today/)**,
  on length, structure, and justifying design decisions.
- **[Figma's design recruiter, Korin Harris](https://dribbble.com/resources/career/design-recruiter-portfolio-tips)**,
  on landing pages, thumbnail consistency, and proofreading.
- **[VMware Design](https://medium.com/vmwaredesign/product-design-portfolios-63618e1692b6)**,
  on how the scope bar moves from junior to lead to design leader.
- **[WebAIM](https://webaim.org/articles/contrast/)** and WCAG 2.2, on contrast
  thresholds.

Sources and the exact figures used are in
[`references/evidence.md`](skills/mj-portfolio-review/references/evidence.md).

## What this is not

It is not a hiring decision, and it does not judge your talent. It reviews a
website against what reviewers say they look for. A high score is not a job, and
a low score is a list of things to fix.

It also cannot see what you owned, where your numbers came from, or whether your
work shipped. Those go in the "Need from you" list for you to answer yourself.

## Layout

```
skills/mj-portfolio-review/
  SKILL.md                      the review flow
  references/
    rubric.md                   areas, level bars, deal-breakers, bands
    evidence.md                 every source and figure, verified
    report-template.md          report structure
    tracking.md                 what is counted, and the feedback link
    tracking.json               form config
  evals/                        test cases
site/portfolio-review/          landing page files
```

## License

MIT. See [LICENSE](LICENSE).
