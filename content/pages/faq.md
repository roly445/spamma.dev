---
title: "FAQ"
description: "Common answers for running and using Spamma."
weight: 90
---

## Why am I not seeing emails?

- Verify MX records point to the host.
- Confirm port 25 (or 587) is open and not blocked by a firewall or ISP.
- Check container logs for SMTP errors.

## Can I change the SMTP port?

Yes. Map an external port to internal 25 in Docker Compose (for example `587:25`) if 25 is blocked.

## Can I use external Postgres or Redis?

Yes. Point connection strings to your external instances and remove the bundled services from compose.

## How do I enable TLS?

Provide a `.pfx` certificate in `certs/` (passwordless) or use the setup wizard to generate with Let's Encrypt. Port 587 will be enabled when a cert is present.

## Is there an API?

An API for programmatic access is planned. For now, use the UI and SMTP inputs for testing.
