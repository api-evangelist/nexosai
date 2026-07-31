---
name: Provision and rotate nexos.ai team API keys
description: Create, list, update, rotate, and revoke team-scoped API keys on the nexos.ai Gateway for governed, per-team access to models.
api: openapi/nexosai-gateway-openapi-original.yml
operations: [list-team-api-keys-v1, create-team-api-key-v1, regenerate-team-api-key-v1, delete-team-api-key-v1, rotate-api-key-v1]
generated: '2026-07-20'
method: generated
---

# Manage team API keys (nexos.ai Gateway)

Base URL `https://api.nexos.ai`. Authenticate with an admin-scoped `X-Api-Key`.

## Steps
1. List existing keys: `list-team-api-keys-v1` — `GET /v1/teams/{teamId}/api_keys`.
2. Create a key: `create-team-api-key-v1` — `POST /v1/teams/{teamId}/api_keys`. Save the returned key value immediately — it is shown once. Team keys use the `nexos-team-` prefix and carry team-level settings (enabled models, fallbacks).
3. Update a key: `update-team-api-key-v1` — `PATCH /v1/teams/{teamId}/api_keys/{keyId}`.
4. Rotate (deprecate old, issue new): `regenerate-team-api-key-v1` — `PATCH /v1/teams/{teamId}/api_keys/{keyId}/regenerate`; or rotate the calling key with `rotate-api-key-v1` — `PATCH /v1/apikey/rotate`.
5. Revoke: `delete-team-api-key-v1` — `DELETE /v1/teams/{teamId}/api_keys/{keyId}`.

## Notes
- Bulk operations exist: `update-many-team-api-keys-v1` — `POST /v1/teams/{teamId}/api_keys/bulk`.
- Bound spend with the Budget Limit Management endpoints (`/v1/companies/{companyId}/budget_limits`).
- `404` = team/key not found; `401` = caller not authenticated. See `errors/nexosai-problem-types.yml`.
