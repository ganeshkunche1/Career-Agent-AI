# Testing

1. Import the workflow, connect credentials, and create the Sheet headers from [configuration.md](configuration.md).
2. Use the synthetic cases in `sample-data/sample-opportunity-inbox.csv`; send only copies to a controlled test Gmail inbox, or paste a case into a temporary Set node before `Clean Email Data`.
3. Run **Execute Workflow** with a Gmail search limited to one test message. Inspect every node's output.
4. Confirm opportunity rows have all required fields, arrays become comma-separated text, and no irrelevant case reaches Sheets.
5. Run the same message a second time after adding the documented Sheets lookup; expect no second row.

Expected coverage: internship, job, hackathon, fellowship/scholarship, irrelevant, missing deadline, HTML body, missing metadata, ambiguous opportunity, and duplicate. For an email without an explicit deadline, the result must be `Not specified`, never an invented date.
