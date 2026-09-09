# Architecture

```mermaid
flowchart TD
  A[Manual test trigger / Gmail trigger] --> B[Gmail search or new message]
  B --> C[Clean Email Data]
  C --> D[OpenAI structured extraction]
  D --> E[Validate structured output]
  E --> F{is_opportunity?}
  F -->|Yes| G[Check duplicate message ID]
  G --> H[Google Sheets append row]
  F -->|No| I[Ignore or inspect execution]
```

The included workflow implements the manual path: **Manual Trigger → Gmail Search → Clean Email Data → OpenAI Analysis → Validate Output → Opportunity? → Google Sheets Append Row**. Use executions to inspect non-opportunities. Before enabling a production Gmail Trigger, copy the processing nodes into that trigger path and test it with a controlled test message.

`Clean Email Data` limits AI input to normalized metadata and a clipped body. `Validate Structured Output` rejects malformed model output and normalizes arrays. The Google Sheet must use the header names documented in [configuration.md](configuration.md).
