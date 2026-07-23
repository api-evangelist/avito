---
name: Respond to buyers in Avito Messenger
description: Handle buyer-seller conversations: list chats, read a chat and its message history, send a reply, and mark the chat as read.
api: openapi/avito-messenger-openapi.json
operations: [getChatsV2, getChatByIdV2, getMessagesV3, postSendMessage, chatRead]
---

# Respond to buyers in Avito Messenger

**API:** Avito messenger (`https://api.avito.ru/`) — OpenAPI at `openapi/avito-messenger-openapi.json`.

## Authentication
All calls use OAuth 2.0 Bearer tokens. Use the **authorization_code** flow to act on behalf of a user, or **client_credentials** to act as your own business account. Token endpoint: `https://api.avito.ru/token`. See `authentication/avito-authentication.yml` and required scopes in `scopes/avito-scopes.yml`. Send `Authorization: Bearer <access_token>` on every request.

## Conventions
- Base URL `https://api.avito.ru/`; JSON request/response.
- Rate limiting is signaled with `X-RateLimit-Limit` / `X-RateLimit-Remaining`; a `429` means back off (`rate-limits/avito-rate-limits.yml`).
- Errors return `{ "error": { "code": <int>, "message": <string> } }` (`errors/avito-problem-types.yml`) — there is **no** idempotency key, so do not blindly retry unsafe writes.
- Most paths are scoped to your `user_id`.

## Steps
1. `getChatsV2` — call the operation of that id in the spec.
2. `getChatByIdV2` — call the operation of that id in the spec.
3. `getMessagesV3` — call the operation of that id in the spec.
4. `postSendMessage` — call the operation of that id in the spec.
5. `chatRead` — call the operation of that id in the spec.
