---
name: Manage API tokens
description: Create, list, verify, and revoke Skedulo API tokens for programmatic access.
api: openapi/skedulo-authentication-openapi.yml
operations: [whoami, createApiToken, fetchAll, revokeToken]
---

# Manage API tokens

Provision and rotate the Bearer JWT tokens that authenticate Skedulo API calls.

## Auth
Bearer JWT API token in `Authorization`. Base URL: `https://api.skedulo.com/auth`.

## Steps
1. **Confirm identity** — `GET /whoami` (`whoami`) to verify the current token, its user, tenant,
   and roles.
2. **Create a token** — `POST /token` (`createApiToken`) with an empty `{}` body for a
   long-lived token or an expiry for a time-limited one.
3. **List tokens** — `GET /tokens` (`fetchAll`) to audit issued tokens.
4. **Revoke** — `POST /token/revoke` (`revokeToken`) to invalidate a token; `POST /token/unrevoke`
   to restore it.

## Notes
- Tokens are secrets — store them in an encrypted vault; never commit them.
- A dedicated API user can be set for the tenant (`setApiUser`) to own integration access.
