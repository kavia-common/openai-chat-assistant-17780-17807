# Ocean Professional Chat API (FastAPI)

A modern FastAPI backend exposing REST endpoints to chat with an AI assistant using the OpenAI API. Styled with the Ocean Professional theme (blue and amber accents).

## Endpoints

- GET `/` — Health check
- GET `/docs` — Swagger UI
- GET `/redoc` — ReDoc
- GET `/docs/ocean` — Themed docs landing page
- GET `/docs-theme` — JSON theme tokens
- POST `/chat` — Send chat messages and receive AI response

## Request/Response

Example `POST /chat` request body:
```json
{
  "messages": [
    {"role": "system", "content": "You are a helpful assistant."},
    {"role": "user", "content": "Hello! Who are you?"}
  ],
  "model": "gpt-4o-mini",
  "temperature": 0.7,
  "max_tokens": 256
}
```

Example response:
```json
{
  "message": {"role": "assistant", "content": "Hello! I'm an AI assistant..."},
  "model": "gpt-4o-mini",
  "usage_prompt_tokens": 15,
  "usage_completion_tokens": 25,
  "usage_total_tokens": 40
}
```

## Environment Variables

Copy `.env.example` to `.env` and fill in values:

- `OPENAI_API_KEY` (required)
- `OPENAI_BASE_URL` (optional) - override for compatible gateways
- `MODEL_FALLBACK` (optional, default: `gpt-4o-mini`)
- `SITE_URL` (optional)

## Run locally

```bash
cd fastapi_backend
uvicorn src.api.main:app --host 0.0.0.0 --port 8000 --reload
```

Open http://localhost:8000/docs

## Notes

- Do not hardcode secrets; use environment variables.
- CORS is permissive for development; tighten for production.
