# Frontend

The frontend is an independent static application served by nginx. Nginx proxies `/api/*` requests to the Compose `backend` service, keeping browser requests same-origin and avoiding frontend-specific environment substitution.

Run it with `docker compose up --build` from the repository root and open <http://localhost:8080>.
