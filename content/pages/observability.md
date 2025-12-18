---
title: "Observability"
description: "Metrics, dashboards, and tracing that ship with Spamma."
weight: 80
---

## Included stack

- Prometheus (port 9090) for metrics storage
- Grafana (port 3000) for dashboards
- Jaeger (port 16686) for distributed tracing

## What you get

- Email processing metrics (throughput, errors)
- Service health dashboards
- Traces for request paths to debug latency or failures

## Usage

- Access Grafana at [http://localhost:3000](http://localhost:3000) (credentials from `.env`).
- Query Prometheus directly at [http://localhost:9090](http://localhost:9090).
- Inspect traces at [http://localhost:16686](http://localhost:16686).

Remove these services from `docker-compose.prod.yml` if you want a lighter footprint.
