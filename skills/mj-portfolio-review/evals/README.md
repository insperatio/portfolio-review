# Evals

Testing happens on two tracks, both manual, both usable with any agent that can
load a skill.

## Behavior cases

[cases.json](cases.json) holds invented scenarios. They exist to catch the skill
misbehaving: scoring something it never measured, guessing at a target role,
ignoring a cap, pushing past a refusal, drifting into unfair findings. A few of
them run against the offline sites kept in [fixtures](fixtures).

To work through one:

- Start a clean conversation. Stale context ruins the result.
- Give the agent the case's `request` verbatim. Where a case names a `fixture`,
  hand over the path to that folder in place of a URL.
- Answer the skill's intake questions with the `follow_up` text from the top of
  the file.
- Compare the output against that case's `expected` entries plus
  `shared_criteria`. Record each as pass, fail, or unclear, with the quoted line
  that decided it.
- Keep `expected` out of the agent's view throughout.

Any edit to `SKILL.md` or the references invalidates earlier results. Run them
again.

## Live runs

Real portfolios, real scores, chosen to span the seniority range and the score
bands. These answer a different question: are the numbers defensible and does the
tone land.

Reports produced this way stay out of the repository when the portfolio belongs
to somebody else. Those designers did not ask to be reviewed in public.

A useful live run needs a stated target role, because the same portfolio scores
differently against different jobs and that is by design. Running one portfolio
past two agents with identical targets is the test of whether the rubric is
stable.

## What none of this measures

Hiring outcomes. These checks establish that the skill behaves as written and
scores consistently. Whether a higher score produces more interviews is outside
anything tested here.
