---
title: "Spamma"
description: "Self-hosted SMTP email capture with a Blazor WebAssembly UI, built for technical teams."
---

## Self-hosted email sandbox for engineering teams

Spamma is an open-source, self-hosted alternative to Mailtrap and MailHog. It runs a real SMTP server, captures every message (headers, body, attachments), and presents them in a fast Blazor WebAssembly UI. Built on .NET 10 with event sourcing (Marten), CQRS, and CAP, it stays reliable under load and keeps every action auditable.

- Real SMTP + MX capture for production-like testing
- Multi-domain, multi-user, role-aware access controls
- Event-sourced audit trail with projections for fast reads
- Docker Compose bundle (Postgres, Redis, observability)

**Get started:** [Quickstart](/pages/quickstart/) · [Setup wizard](/pages/setup-wizard/) · [Deployment](/pages/deployment/) · [How it works](/pages/how-it-works/)

## Setup in minutes

- Run `docker-compose` and open the built-in setup wizard
- Generate TLS (Let’s Encrypt or bring-your-own .pfx)
- Configure SMTP endpoints and domains
- Create the first admin and finish with a working instance

## Built for real workflows

- **Developers:** Point local apps at SMTP:1025 and iterate quickly
- **QA/CI:** Use Compose in pipelines to validate email flows deterministically
- **Staging:** Capture MX traffic per domain with role-based access
- **Ops:** Observe throughput and errors with Prometheus/Grafana/Jaeger

## What you’ll see in the UI

- Inbox views per domain with sender/recipient/subject filters
- Full message detail: headers, HTML/text bodies, attachments
- Searchable, event-backed history for audits and debugging
