# Counting and feedback

Two separate things, deliberately kept apart.

**Counting** is anonymous and automatic. It carries no URL and nothing from the
review.

**Feedback** is a link. The person opens it if they want to, and decides what to
put in it.

They never share a pipe. The count stays clean, the feedback stays voluntary, and
the privacy claim in the README is simple enough to verify by reading this file.

## Counting

### What is sent

Two fields. Nothing else, ever.

| Field | Value |
|---|---|
| `date` | Today's date, no time. |
| `agent` | Which assistant ran the review, for example "Claude Code" or "Cursor". |

**Never sent:** the portfolio URL, the score, the band, the findings, the fixes,
the target role, the seniority, their name, their email, any part of the
conversation, or anything about the machine it ran on.

The URL is the line. It identifies a person, their work, and usually their whole
career history. It is not collected by counting, and no configuration of this
file turns that on.

### How to send it

Read `tracking.json`. If it is missing, or `usage_form_id` is absent or blank,
send nothing and say nothing. That is also how a user turns counting off.

After the report is delivered, make one request:

```
POST https://docs.google.com/forms/d/e/{usage_form_id}/formResponse
Content-Type: application/x-www-form-urlencoded

{entry_date}={date}&{entry_agent}={agent}
```

One attempt. No retries. Treat any response as done, since the response is opaque
either way. If it fails, say nothing: a failed count is not the user's problem.

Never report a send as successful without having made the request.

Where outbound requests are blocked, which includes claude.ai, do not try and do
not substitute a link. An uncounted run is the correct outcome there. Do not ask
the person to count themselves.

### Disclosure

Counting is silent, so it has to be stated plainly somewhere the person will see
it. Put this line at the end of the report, just above the signature:

> Counted anonymously: today's date and which AI tool ran this, nothing else. No
> URL, nothing from your review. Turn it off by blanking `usage_form_id` in the
> skill's `references/tracking.json`.

Say it once per conversation. Do not ask permission, because this is a statement
rather than a request, and do not apologize for it.

## Feedback

One line at the end of the report, under the disclosure. An offer, not a
question, and never a push:

> Found this useful, or got something wrong? Tell Mariana:
> {feedback_url}

Say it once. If the person ignores it, that is the end of it. Never ask whether
they are going to fill it in, never follow up, and never offer to fill it in for
them.

The form asks for what would improve the skill, what the review got wrong, and
optionally their portfolio URL, what to call them, and an email. The email is
used only for the boxes they tick on the form. None of that is this skill's
business: the skill's whole job is to show the link and move on.

### Why the URL lives here and not in counting

A portfolio URL given on a feedback form is given. The person opened the form,
read the fields and typed it in. The same URL harvested at the end of a review is
taken. Same string, completely different thing, and only one of them is yours to
collect.
