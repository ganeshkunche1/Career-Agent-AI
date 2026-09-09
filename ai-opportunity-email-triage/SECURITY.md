# Security policy

Do not report suspected vulnerabilities through a public issue, and do not include credentials or email data in any report. Instead, contact the repository owner privately through the contact method listed on the repository profile. Include a concise description, impact, and safe reproduction steps.

## Scope

This repository contains an n8n workflow and local Docker configuration. Security-sensitive areas include accidental credential export, unsafe handling of email content, and insecure public deployment of n8n.

Before publishing changes, verify that `.env`, local n8n data, credential exports, logs, and unredacted screenshots remain untracked.
