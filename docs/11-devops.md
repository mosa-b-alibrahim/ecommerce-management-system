# 11 - DevOps

## Goal
Make local setup reproducible and deployment-friendly without adding infrastructure before it is learned.

## Docker stage (Week 10)
Learn image, container, Dockerfile, ports, networks, volumes, environment variables, Compose.

Target:
```text
docker compose up
  -> Spring Boot backend
  -> PostgreSQL
  -> optional simple frontend
```

## Configuration
Use environment variables/config profiles for database URL, credentials, JWT secret/key material, AI keys, and cloud-specific settings. Commit `.env.example`, never real secrets.

## Environments
At minimum understand local/test/cloud differences. Automated tests should not depend on a developer's manually configured database.

## Logging
Useful application/business error context; no passwords/tokens/secrets. Add correlation/request IDs only if useful and understood.

## Operational checklist
- application starts from clean setup,
- migrations run predictably,
- health/smoke endpoint strategy documented,
- logs can diagnose startup/database errors,
- graceful failure when required configuration is missing.
