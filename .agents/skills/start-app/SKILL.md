---
name: start-app
description: Start and verify the complete application locally with Docker Compose.
---

# Start the application

## Procedure

1. Read `docker-compose.yml`, `.env.example`, and the relevant component READMEs.
2. Check that Docker and the Compose plugin are available:
   `docker --version` and `docker compose version`.
3. Check required environment configuration. If `.env` is absent, use documented defaults
   only when the Compose file permits them; otherwise stop and report what is missing.
4. Build and start the stack with:
   `docker compose up --build -d`.
5. Wait for services to become healthy. Use `docker compose ps` and inspect logs with
   `docker compose logs --tail=100 <service>` when a service is not ready.
6. Check the backend health endpoint and the frontend URL documented by the Compose
   configuration. Verify the frontend can reach the backend through its configured route.

## Error handling

- Never report success while a service is unhealthy, exited, or inaccessible.
- Report the failed command, service, relevant log excerpt, and a concrete next step.
- Do not delete containers, volumes, images, or data to work around a failure.

## Verification and success criteria

Success requires healthy/running Compose services, a successful backend health response,
and an accessible frontend. Report the local URLs, service status, and any warnings.
