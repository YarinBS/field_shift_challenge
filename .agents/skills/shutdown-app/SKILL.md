---
name: shutdown-app
description: Stop the local Docker Compose application without removing persistent data.
---

# Shut down the application

## Procedure

1. Inspect the Compose project name and services with `docker compose ps`.
2. Run `docker compose down` (without `-v`).
3. Verify with `docker compose ps -a` that the relevant containers are stopped or removed.
4. Report the shutdown status and note that volumes and user data were preserved.

## Safety and errors

Never use `docker compose down -v`, remove volumes, or delete data unless the user
explicitly authorizes that exact destructive action. If shutdown fails, report the command,
service, and logs needed to diagnose it.

## Success criteria

The Compose services are stopped/removed and persistent volumes remain intact.
