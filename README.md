# NASA Farm Adaptation

Decision-support application for the NASA 2026 Space Apps Challenge, "Adapting
Farms with NASA Data". The MVP focuses on helping farmers assess whether land
is suitable for Arabica coffee now and over a selected future horizon, detect
climate risks, and explore ways to improve conditions for existing coffee
plantations.

The repository is a small monorepo with independent frontend, backend, and model components. The current implementation is infrastructure-only: it verifies that the frontend can call the backend and that the backend health endpoint responds.

## Prerequisites

- Docker Desktop (Windows or macOS), or Docker Engine with the Compose plugin (Linux)
- Git

No project-specific Python or JavaScript installation is required.

## Run

```bash
docker compose up --build
```

Then open <http://localhost:8080>. The frontend calls the backend through the Compose network and displays the backend health response.

Useful commands:

```bash
docker compose ps
docker compose logs -f
docker compose down
```

The backend API is available at <http://localhost:8000>. API documentation is available at <http://localhost:8000/docs>.

## Repository layout

- [`app/frontend/`](app/frontend/) - static frontend application served by nginx
- [`app/backend/`](app/backend/) - FastAPI HTTP API
- [`model/`](model/) - isolated, importable model package
- [`data/`](data/) - local data lifecycle directories; contents are ignored by Git
- [`docs/`](docs/) - project documentation
- [`scripts/`](scripts/) - development utility scripts

## Configuration and data

Copy `.env.example` to `.env` to override documented local settings. Secrets, API keys, datasets, and model weights must remain outside version control.

## Troubleshooting

- If a port is already in use, change `FRONTEND_PORT` or `BACKEND_PORT` in `.env`.
- If a build appears stale, run `docker compose build --no-cache`.
- If the frontend reports that the backend is unavailable, wait for `docker compose ps` to show both services as healthy, then refresh the page.
- On Windows and macOS, ensure Docker Desktop is running and that the repository is shared with Docker if prompted.

See the component READMEs for API and development details.
