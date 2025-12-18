---
title: "Security"
description: "Self-hosted control, TLS options, and access boundaries."
weight: 70
---

## Self-hosted by design

- Keep all captured mail within your infrastructure.
- Uses PostgreSQL for event storage and file-backed content by default.

## Authentication and roles

- Server issues an HttpOnly cookie after login (magic links or passkeys).
- Role-aware access for multi-user setups.

## TLS and ports

- Plain SMTP on 25 for local/dev.
- STARTTLS on 587 when a certificate is present (Let's Encrypt via setup wizard or bring-your-own `.pfx`).
- Web at 8080 (HTTP) and 8081 (HTTPS when certs are configured).

## Hardening tips

- Limit exposed ports to what you need (typically 25/587 and 8081).
- Use strong secrets in `.env` for Postgres and Redis when deploying with Docker Compose.
- Place Spamma behind your preferred reverse proxy if desired.
