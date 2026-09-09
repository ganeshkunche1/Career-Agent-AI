# Contributing

Thank you for improving the workflow.

## Before opening a pull request

1. Never add credentials, OAuth exports, real email content, spreadsheet IDs, or screenshots containing personal data.
2. Keep the workflow importable and leave credential bindings empty.
3. Use fictional `.example` senders and `synthetic-*` identifiers in fixtures.
4. Run the checks below from the repository root:

```bash
jq empty workflow/ai_opportunity_email_triage.json
docker compose config
```

5. Update the relevant documentation when workflow behavior or configuration changes.

## Pull requests

Describe the behavior changed, the validation performed, and any manual n8n steps required after import. Keep changes focused and update the relevant documentation alongside workflow changes.
