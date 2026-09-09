# Local setup

```bash
docker compose up -d
docker ps
```

Open http://localhost:5678 and create an n8n owner account. To stop the local stack:

```bash
docker compose down
```

To restart it:

```bash
docker compose restart
```

Import `workflow/ai_opportunity_email_triage.json` from the n8n workflow menu. Each user must create their own Gmail, OpenAI, and Google Sheets credentials in n8n; exported workflow files deliberately contain none.
