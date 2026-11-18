# The usage log

**Already built and wired up.** The form exists, it is published, responses land
in a linked sheet, and `references/tracking.json` holds the real IDs. Nothing
below needs doing. It is kept as a record of how it was set up and what to change
if you ever rebuild it.

| Thing | Where |
|---|---|
| Form (edit) | https://docs.google.com/forms/d/1q9B6Et3PLwZWvqOLT2fwbkTBRwcpzL_AYt6lhaPRnK0/edit |
| Responses sheet | https://docs.google.com/spreadsheets/d/1Pfs81bAwvCGJhp84qOLEU461IQmVUj5l9vy__XhSG1w/edit |
| Live form | https://docs.google.com/forms/d/e/1FAIpQLSfNOQSNtWFR84Y4Zd7k45COe_dHC858sNoudDH-kVEd3SFKoA/viewform |

Settings as configured: three short-answer questions named `date`,
`portfolio_url` and `agent`, none required; "Collect email addresses" set to
**Do not collect**; "Limit to 1 response" off; responders set to anyone with the
link. The sheet columns read Timestamp, date, portfolio_url, agent.

---

## How it was built

## 1. Create the form

Go to forms.google.com and make a blank form.

- **Title:** mj-portfolio-review usage
- **Description:** Automatic log from the mj-portfolio-review skill. Submitted only
  when a user agrees.

Add exactly three questions, all **short answer**, all **not required**:

| # | Question title | Why not required |
|---|---|---|
| 1 | date | Keeps a submission from failing on a blank field |
| 2 | portfolio_url | Empty when the user chose count only |
| 3 | agent | Empty if the assistant cannot identify itself |

Do not add a question for anything else. Do not turn on "Collect email
addresses." If that setting is on, the form records the submitter's Google
account, which would break the privacy promise in the README.

## 2. Send responses to a sheet

In the **Responses** tab, click the Sheets icon and create a new spreadsheet.
Name it something like "portfolio-review usage."

## 3. Get the three entry IDs

Click **Send**, choose the link icon, and copy the form URL. It looks like:

```
https://docs.google.com/forms/d/e/1FAIpQLSd.../viewform
```

The part between `/d/e/` and `/viewform` is your **form_id**.

Now open that viewform URL in a browser, right click the page, and choose **View
page source**. Search the source for `entry.` and you will find three numeric
IDs in the order your questions appear, like `entry.1234567890`. Match them to
the questions by the question text that appears near each one.

If reading page source is annoying, there is an easier way: in the form editor,
click the three dots and choose **Get pre-filled link**, type a recognizable
value into each field such as `AAA`, `BBB`, `CCC`, then submit. The link it gives
you back contains each entry ID next to the value you typed, so you can tell
which is which.

## 4. Fill in tracking.json

Open `skills/mj-portfolio-review/references/tracking.json` and replace the
placeholders:

```json
{
  "form_id": "1FAIpQLSd...",
  "entry_date": "entry.1234567890",
  "entry_url": "entry.0987654321",
  "entry_agent": "entry.1122334455",
  "feedback_url": "https://marianajohnels.com/portfolio-review/"
}
```

Commit that file. It contains no secrets. A form ID is public by design, and
anyone can submit to a public Google Form whether or not they have your ID.

## 5. Test it

Install the skill locally and run a review on any site. Answer yes to the logging
question. Check that a row appears in the sheet with today's date, the URL, and
the agent name, and nothing else.

Then run a second review and answer no. Confirm no row appears.

## Reading your numbers

Open the sheet. The row count is your usage count. Two things to keep in mind:

- It is a floor, not a total. It only counts people who said yes in an
  environment where the send worked. Real usage is higher.
- It is a different number from the skills.sh badge, which counts installs. One
  install can produce many reviews, or none.

If you want a quick summary, add a second tab and paste these:

```
=COUNTA('Form Responses 1'!A2:A)                      total reviews logged
=COUNTIF('Form Responses 1'!C2:C,"<>")                 with a portfolio URL
=SORT(UNIQUE('Form Responses 1'!D2:D))                 which agents people use
```

Adjust the column letters if your question order differs. Column A is the
timestamp Google adds automatically.

## If you outgrow it

The weak spot is that a public form has no spam protection. Anyone who finds the
form ID in the repo can submit junk rows. At low volume you would notice and
could just delete them. If it becomes a problem, the move is a Supabase table
behind an insert-only edge function with rate limiting, and the only thing that
changes in the skill is the POST target in `tracking.md` and the config file.
Nothing about the consent flow or the payload would change.
