---
name: restart-app
description: Restart the Docker Compose application while applying code and configuration changes safely.
---

# Restart the application

## Procedure

1. Inspect `docker-compose.yml`, Dockerfiles, dependency manifests, and recent changes.
2. Decide whether each service needs an image rebuild:
   - rebuild after Dockerfile, dependency, build-context, or copied-source changes;
   - recreate after Compose, environment, port, or service configuration changes;
   - use a plain restart only when neither image nor container configuration changed.
3. Prefer `docker compose up -d --build` when rebuilding is needed. Otherwise use
   `docker compose up -d` to recreate changed containers, or `docker compose restart`
   only for an unchanged configuration.
4. Preserve named volumes and local data. Never use `docker compose down -v`.
5. Verify with `docker compose ps`, health endpoints, and relevant logs.

## Error handling

Report which services were rebuilt, recreated, or restarted. If health checks fail, include
the failed service and logs; do not claim a successful restart or silently fall back.

## Success criteria

All affected services are running and healthy, configuration changes are active, and the
frontend and backend endpoints are accessible without data loss.
