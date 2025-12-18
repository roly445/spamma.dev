---
title: "How it works"
description: "SMTP capture pipeline, event sourcing, and modular architecture."
weight: 20
---

## Flow at a glance

1. SMTP server receives mail (direct or via MX).
2. Message bytes are parsed into a MIME message.
3. Domains are validated through DomainManagement projections.
4. Events are stored in Marten (PostgreSQL) with CAP handling distributed workflows.
5. Projections build read models consumed by the Blazor WebAssembly UI.

## Architecture

- Modular monolith with clear boundaries:
  - UserManagement: auth, sessions, roles
  - DomainManagement: domains and MX
  - EmailInbox: email ingestion, inbox features
  - Common: shared contracts and integration events
- CQRS with MediatR: commands and queries separated for clarity and scale.
- Event sourcing via Marten: full audit trail, replayable state.
- CAP + Redis: reliable background messaging and integrations.
- Frontend: Blazor WebAssembly + Tailwind SCSS + TypeScript assets built with webpack.

## What runs where

- Server (Spamma.App): static pages (login, setup), authentication cookie issuance, API surface.
- Client (Spamma.App.Client): all interactive UI, CQRS calls, browser APIs.
- Infrastructure: PostgreSQL (event store), Redis (CAP), Docker Compose for local and prod.

## Why it scales for testing

- Real SMTP handling, not mocks.
- Event-sourced append-only storage keeps history while projections stay fast.
- CAP enables async fan-out (notifications, future webhooks) without blocking SMTP.
- Clear module boundaries make it easy to extend (new projections, APIs, or integrations).
