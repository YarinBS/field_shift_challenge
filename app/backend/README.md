# Backend

The backend is a FastAPI service. It owns the HTTP API, configuration boundary, future data integrations, and coordination of model inference.

## API

`GET /api/health`

```json
{"status":"ok","service":"backend"}
```

Interactive OpenAPI documentation is available at `/docs` when the service is running.

## Local development

The supported development path is Docker Compose from the repository root. For direct development, install `requirements.txt` and set `PYTHONPATH` to include `model/src` and `app/backend/src`.
