# Configuration

## Credentials

Create three credentials in n8n: Gmail OAuth2, OpenAI API, and Google Sheets OAuth2. Assign them to the matching nodes after importing. Never place keys, OAuth tokens, account names, or spreadsheet IDs in this repository.

## Gmail search

In **Gmail Search**, replace the `q` value with a valid Gmail query. The default is suitable for a recent historical test. Manual search processes existing messages; a Gmail Trigger processes new messages after activation and does not replace a historical backfill.

## OpenAI node

Set a model available to your OpenAI account (the workflow uses `gpt-4o-mini` as an editable default). Keep JSON-object response formatting enabled. The prompt requires unsupported facts to be `Not specified`, and requires an ISO deadline only when explicitly present.

## Google Sheet

Create a spreadsheet and a worksheet with this header row, in this order:

`Opportunity Type, Title, Organization, Deadline, Priority, Priority Score, Summary, Action Required, Skills / Requirements, Location / Mode, Tags, Confidence, Email Subject, Email From, Email Date, Email Message ID, Email Link, Processed At`

In **Google Sheets Append Row**, select your own spreadsheet and worksheet, then map the node fields. A stable Gmail `messageId` is supplied for duplicate prevention.

## Duplicate strategy

Before production, add a Google Sheets **Get Row(s)** lookup on `Email Message ID` before append, then only append when no matching row exists. This is intentionally a manual final wiring step because spreadsheet selection and the current Sheets-node mapping UI are account-specific. It prevents repeat manual searches from appending the same email twice.

## Priority

Scores are 1–10: HIGH is 8–10 for actionable, strongly relevant or deadline-sensitive opportunities; MEDIUM is 4–7 for relevant but less urgent items; LOW is 1–3 for weak, informational, or low-actionability items. Scores do not assume a recipient's personal preferences.
