# Troubleshooting

| Problem | Practical fix |
| --- | --- |
| n8n does not open | Run `docker ps`; then `docker compose up -d` and inspect `docker compose logs n8n`. |
| Gmail/Sheets OAuth fails | Reconnect the credential in n8n and verify the OAuth consent screen, redirect URL, and Google API access. |
| No Gmail results | Test the query directly in Gmail; reduce it to a known matching term. |
| OpenAI fails or JSON is invalid | Check the API credential/model, inspect the raw response, and retry a small message. |
| Sheets append fails | Confirm spreadsheet access, worksheet name, and exact header row. |
| Duplicate rows | Add the documented lookup by `Email Message ID` before append. |
| Rate limits | Reduce search limits, retry with backoff, and process in smaller batches. |

Do not paste credentials, raw emails, or tokens into public issue reports.
