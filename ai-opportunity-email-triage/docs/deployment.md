# Deployment

Local development runs n8n on Docker Desktop and is suitable for building and testing. Production deployment needs persistent storage, an encryption key, a controlled public callback URL for OAuth/webhooks, backups, access control, and monitoring. This repository distributes the workflow only; it does not create a hosted service or share credentials.

Possible future targets include a managed n8n offering, a secured VM, or a container platform. Reconnect credentials independently in every target environment and retest before activating a Gmail trigger.
