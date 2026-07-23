---
name: Manage Avito listings and pricing
description: Manage a business seller's Avito listings: enumerate items, read details, update prices, apply paid promotion (VAS), and pull performance analytics.
api: openapi/avito-item-openapi.json
operations: [getItemsInfo, getItemInfo, updatePrice, applyVas, itemAnalytics]
---

# Manage Avito listings and pricing

**API:** Avito item (`https://api.avito.ru/`) — OpenAPI at `openapi/avito-item-openapi.json`.

## Authentication
All calls use OAuth 2.0 Bearer tokens. Use the **authorization_code** flow to act on behalf of a user, or **client_credentials** to act as your own business account. Token endpoint: `https://api.avito.ru/token`. See `authentication/avito-authentication.yml` and required scopes in `scopes/avito-scopes.yml`. Send `Authorization: Bearer <access_token>` on every request.

## Conventions
- Base URL `https://api.avito.ru/`; JSON request/response.
- Rate limiting is signaled with `X-RateLimit-Limit` / `X-RateLimit-Remaining`; a `429` means back off (`rate-limits/avito-rate-limits.yml`).
- Errors return `{ "error": { "code": <int>, "message": <string> } }` (`errors/avito-problem-types.yml`) — there is **no** idempotency key, so do not blindly retry unsafe writes.
- Most paths are scoped to your `user_id`.

## Steps
1. `getItemsInfo` — call the operation of that id in the spec.
2. `getItemInfo` — call the operation of that id in the spec.
3. `updatePrice` — call the operation of that id in the spec.
4. `applyVas` — call the operation of that id in the spec.
5. `itemAnalytics` — call the operation of that id in the spec.
