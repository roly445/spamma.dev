---
title: "Deployment"
description: "Production deployment with Docker Compose, TLS, and MX records."
weight: 40
---

## Production with Docker Compose

1. Download config files:

   ```bash
   curl -O https://raw.githubusercontent.com/roly445/spamma/main/docker-compose.prod.yml
   curl -O https://raw.githubusercontent.com/roly445/spamma/main/.env.example
   ```

2. Copy env file and set secrets:

   ```bash
   cp .env.example .env
   ```

   Required: `POSTGRES_PASSWORD`, `REDIS_PASSWORD`, `BASE_URI`, `GRAFANA_ADMIN_PASSWORD`.
3. Start services:

   ```bash
   docker compose -f docker-compose.prod.yml pull
   docker compose -f docker-compose.prod.yml up -d
   ```

4. Run the setup wizard at your `BASE_URI` to generate keys, SMTP settings, admin user, and hosting details.

## DNS and MX

- Add an MX record pointing to your Spamma host (priority 10 is typical).
- Ensure the A record for the host points to your server.

## Ports

- 8080: HTTP web
- 8081: HTTPS web (when TLS is configured)
- 25: SMTP (plain)
- 587: SMTP with STARTTLS (enabled when a certificate is present)
- 3000: Grafana
- 9090: Prometheus
- 16686: Jaeger

## TLS options

- **Setup wizard + Let's Encrypt:** generates `certificate_*.pfx`, renews automatically.
- **Bring your own:** place a passwordless `.pfx` in `certs/`; mapped into the container volume.

## Backups and updates

- Backup Postgres: `pg_dump` from the postgres container.
- Backup message volume: tar the `messages` volume.
- Update: `docker compose -f docker-compose.prod.yml pull spamma && docker compose -f docker-compose.prod.yml up -d spamma`.

## Minimal footprint

If you do not need observability, remove Grafana, Prometheus, and Jaeger services from the compose file and their dependencies on the main service.
