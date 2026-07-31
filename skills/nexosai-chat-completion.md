---
name: Generate a chat completion via the nexos.ai Gateway
description: Call the OpenAI-compatible nexos.ai Gateway API to generate a model response from conversation messages, with optional storage and metadata.
api: openapi/nexosai-gateway-openapi-original.yml
operations: [post-chat-completions-v1, get-user-models-v1]
generated: '2026-07-20'
method: generated
---

# Generate a chat completion (nexos.ai Gateway)

The nexos.ai Gateway API is OpenAI-compatible. Base URL is `https://api.nexos.ai`.

## Auth
Send your nexos.ai API key in the `X-Api-Key` header (`nexos-...` user key or `nexos-team-...` team key), or as `Authorization: Bearer <key>`. API usage requires a paid subscription **and** purchased API credits (a separate add-on) — otherwise the API returns `402 Payment Required`.

## Steps
1. (Optional) List available models with `get-user-models-v1` — `GET /v1/models` — to pick a `model` name, UUID, or agent UUID.
2. Call `post-chat-completions-v1` — `POST /v1/chat/completions` — with a JSON body containing `messages[]` (each with `role` and `content`; text, image, and audio modalities are supported depending on the model) and `model`.
3. Set `store: true` and a `metadata` object if you want the completion retained and filterable in the dashboard.
4. Read the assistant reply from `choices[0].message.content`.

## Notes
- Because it is OpenAI-compatible, the official OpenAI SDKs work by setting `base_url=https://api.nexos.ai` and `api_key=<nexos key>` (see `openai-sdks/`).
- Errors: `400` malformed request, `401` unauthenticated, `402` no subscription/credits, `500` server error (retry with backoff). See `errors/nexosai-problem-types.yml`.
- Spend is bounded by per-company/team/user budget limits and organization guardrails.
