# Application

The application is split into an independently served frontend and a Python backend. The frontend is exposed on port 8080 by default; the backend is exposed on port 8000 by default.

The frontend-to-backend contract is currently:

- `GET /api/health` returns `{"status": "ok", "service": "backend"}`
- The frontend uses `/api/health` through its nginx reverse proxy, so browser requests remain same-origin.

See [`frontend/README.md`](frontend/README.md) and [`backend/README.md`](backend/README.md).
