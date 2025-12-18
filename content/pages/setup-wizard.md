---
title: "Setup wizard"
description: "Static server-rendered wizard to get Spamma running in minutes."
weight: 35
---

## Overview

The setup wizard is entirely server-rendered (no client interactivity needed) and walks you through keys, hosting, email, TLS, and the first admin account. You can rerun it; each step detects existing config and lets you skip or reconfigure.

## Steps

1. **Welcome** — overview and what you need (time, SMTP details, admin email, optional TLS prerequisites).
2. **Security keys** — collect entropy with mouse movement to generate signing/JWT keys. If keys exist, you can skip or regenerate (with clear warnings about session invalidation).
3. **Hosting** — set `BaseUrl`, `MailServerHostname`, and MX priority. Shows an example MX record.
4. **Email configuration** — set From name/email, SMTP host/port, auth, SSL toggle, and presets for development (localhost:1025), Gmail, SendGrid, Mailgun. Skip or reconfigure if settings already exist.
5. **Certificates (optional)** — skip, or issue via Let’s Encrypt (HTTP-01, needs port 80). Enter an email for ACME. Status and error feedback are shown inline.
6. **Admin user** — create the first admin via magic link auth (passwordless). If an admin exists, you can skip or add another.
7. **Complete** — shows a checklist (keys, hosting/email, admin, optional TLS). Finalize disables setup mode and sends the welcome email with a magic link.

## Notes

- All setup pages are static and marked with `ExcludeFromInteractiveRouting` on the server project.
- TLS on port 587 becomes available once a cert is present; you can skip certificates initially.
- You can return to any step; existing values are displayed read-only with skip/reconfigure options.
