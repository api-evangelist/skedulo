---
name: Manage webhooks
description: Subscribe to Skedulo data-change events by creating, listing, and deleting webhooks.
api: openapi/skedulo-webhooks-openapi.yml
operations: [webhooksFetch, webhooksCreate, webhooksDelete]
---

# Manage webhooks

Register outbound HTTP callbacks that fire when Skedulo records change. Each webhook is a
filter + target URL + GraphQL query that shapes the delivered payload.

## Auth
Bearer JWT API token in the `Authorization` header. Webhooks/triggered-actions live under the
events service (`https://api.skedulo.com/events`).

## Steps
1. **Inspect the webhook payload schema** — `GET /webhooks/schema` (`webhookGraphQLSchema`)
   to see what the GraphQL query for a webhook can select.
2. **Create a webhook** — `POST /webhooks` (`webhooksCreate`) with the filter, target URL, and
   GraphQL query. Always include a filter to avoid excessive deliveries.
3. **List webhooks** — `GET /webhooks` (`webhooksFetch`) to review configured webhooks.
4. **Delete a webhook** — `DELETE /webhooks/{id}` (`webhooksDelete`) when it is no longer needed.

## Notes
- For inbound SMS or SMS-sending actions use **Triggered Actions** instead of webhooks.
- Debug deliveries via the triggered-action/webhook logs (`triggeredActionLogs`).
- See `asyncapi/skedulo-webhooks.yml` for the full event surface.
