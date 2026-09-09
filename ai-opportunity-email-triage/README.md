# Opportunity Email Triage

An n8n workflow for collecting career and learning opportunities from Gmail and recording qualified results in Google Sheets. It normalizes email content, uses OpenAI to extract consistent fields, and keeps the resulting tracker ready for review.

## Features

- Historical/manual Gmail search with an editable valid Gmail query
- Defensive email normalization and body-size limiting
- Structured extraction with source-grounded output rules
- Opportunity-only routing and a Sheets-ready tracking schema
- Documented duplicate-prevention, testing, production-trigger, and deployment paths

## Architecture

Gmail → Clean Email Data → OpenAI Analysis → Validate Output → Opportunity filter → Google Sheets. See [architecture](docs/architecture.md).

## Extracted fields

`opportunity_type`, `title`, `organization`, `deadline`, `priority`, `priority_score`, `summary`, `action_required`, `skills_requirements`, `location_mode`, `tags`, and `confidence`, plus useful email metadata. Missing facts must be `Not specified`; the model must not invent deadlines, links, eligibility, salary, or requirements.

## Priority system

HIGH = 8–10, MEDIUM = 4–7, LOW = 1–3. The score reflects relevance, actionability, and explicit deadline urgency—not personal preferences. See [configuration](docs/configuration.md).

## Requirements

- Docker Desktop and Docker Compose
- n8n account on your local instance
- Your own Gmail, OpenAI, and Google Sheets credentials

## Run locally

```bash
git clone <your-repository-url>
cd ai-opportunity-email-triage
docker compose up -d
```

Open http://localhost:5678. See [setup](docs/setup.md) for stop/restart commands.

## Importing and configuring the workflow

1. In n8n, import `workflow/ai_opportunity_email_triage.json`.
2. Connect your Gmail credential to **Gmail Search**.
3. Connect your OpenAI credential to **OpenAI Analysis** and select a model.
4. Create your Google Sheet with the exact headers in [configuration](docs/configuration.md), then connect/select it in **Google Sheets Append Row**.
5. Edit the Gmail query and run a one-message test.
6. Add the documented message-ID lookup before enabling production processing.

## Test and production modes

The included manual trigger is for controlled historical tests. A Gmail Trigger is the production design for new incoming mail; copy the verified processing path to it, test, then activate it. Read [testing](docs/testing.md) before processing a mailbox.

## Security

Credentials live only in n8n. `.env`, local data, credentials, and logs are ignored by Git. Avoid putting raw email content in workflow notes, source files, screenshots, or public issues.

## Project structure

```text
workflow/      importable n8n workflow
docs/          setup, architecture, configuration, testing, deployment help
sample-data/   test fixtures
config/        configuration reference
```

## Notes

Add redacted screenshots to `screenshots/` if they help explain a setup or execution. Before activating the workflow for ongoing use, configure the message-ID lookup described in [configuration](docs/configuration.md) to prevent duplicate rows.

## License

MIT. See [LICENSE](LICENSE).

## Contributing and security

Contributions are welcome; start with [CONTRIBUTING.md](CONTRIBUTING.md). For a possible security issue, follow [SECURITY.md](SECURITY.md) rather than opening a public issue.
