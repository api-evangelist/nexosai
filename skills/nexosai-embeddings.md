---
name: Create text embeddings via the nexos.ai Gateway
description: Generate vector embeddings for text using the OpenAI-compatible nexos.ai Gateway embeddings endpoint.
api: openapi/nexosai-gateway-openapi-original.yml
operations: [post-embeddings-v1, get-user-models-v1]
generated: '2026-07-20'
method: generated
---

# Create embeddings (nexos.ai Gateway)

Base URL `https://api.nexos.ai`; OpenAI-compatible.

## Auth
`X-Api-Key: nexos-...` (or `Authorization: Bearer`). Requires an active subscription and API credits, else `402`.

## Steps
1. (Optional) `get-user-models-v1` — `GET /v1/models` — to select an embedding-capable `model`.
2. Call `post-embeddings-v1` — `POST /v1/embeddings` — with `input` (string or array) and `model`.
3. Read the vectors from the returned `data[].embedding` array.

## Notes
- Use the OpenAI SDKs with `base_url=https://api.nexos.ai` for a drop-in client.
- Errors follow the standard JSON envelope (`errors/nexosai-problem-types.yml`).
