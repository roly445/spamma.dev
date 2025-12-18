---
title: "Features"
description: "What Spamma delivers for engineering teams."
weight: 50
---

## Core

- Real SMTP server with full message capture (headers, body, attachments)
- Direct SMTP and MX-based domain capture
- Blazor WebAssembly UI for browsing, search, and inspection
- Multi-domain and multi-user with role-aware access
- Event-sourced audit trail (Marten) with projections for fast reads

## Delivery and storage

- Attachments preserved alongside raw MIME
- Message content stored via providers (file-backed by default) with cleanup paths
- Commands and queries orchestrated with CQRS/MediatR
- CAP with Redis for reliable background workflows

## Operations

- Docker Compose bundle with Postgres, Redis, SMTP, and observability stack
- TLS on 587 when a certificate is present; plain SMTP on 25 for local/dev
- Configurable via appsettings and environment variables

## In progress / planned

- API surface for programmatic access to captured mail
- Richer organization and tagging of messages
- Additional projections for analytics
