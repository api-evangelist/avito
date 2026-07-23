---
name: Publish listings via Avito Autoload feed
description: Bulk-publish and update listings through Autoload: configure the autoload profile, trigger an upload of your XML feed, and monitor upload results.
api: openapi/avito-autoload-openapi.json
operations: [createOrUpdateProfileV2, upload, getCurrentUpload, getLastSuccessfulUpload, getUploads]
---

# Publish listings via Avito Autoload feed

**API:** Avito autoload (`https://api.avito.ru/`) — OpenAPI at `openapi/avito-autoload-openapi.json`.

## Authentication
All calls use OAuth 2.0 Bearer tokens. Use the **authorization_code** flow to act on behalf of a user, or **client_credentials** to act as your own business account. Token endpoint: `https://api.avito.ru/token`. See `authentication/avito-authentication.yml` and required scopes in `scopes/avito-scopes.yml`. Send `Authorization: Bearer <access_token>` on every request.

## Conventions
- Base URL `https://api.avito.ru/`; JSON request/response.
- Rate limiting is signaled with `X-RateLimit-Limit` / `X-RateLimit-Remaining`; a `429` means back off (`rate-limits/avito-rate-limits.yml`).
- Errors return `{ "error": { "code": <int>, "message": <string> } }` (`errors/avito-problem-types.yml`) — there is **no** idempotency key, so do not blindly retry unsafe writes.
- Most paths are scoped to your `user_id`.

## Steps
1. `createOrUpdateProfileV2` — call the operation of that id in the spec.
2. `upload` — call the operation of that id in the spec.
3. `getCurrentUpload` — call the operation of that id in the spec.
4. `getLastSuccessfulUpload` — call the operation of that id in the spec.
5. `getUploads` — call the operation of that id in the spec.
