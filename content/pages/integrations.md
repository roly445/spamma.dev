---
title: "Integrations"
description: "Send email to Spamma from your apps and pipelines."
weight: 60
---

## SMTP endpoints

- Host: `localhost` (or your Spamma host)
- Port: `1025` for local dev, `25` in prod, `587` with STARTTLS when TLS is configured
- Auth: not required (test-focused)

## .NET example

```csharp
var smtpClient = new SmtpClient("localhost")
{
    Port = 1025,
    DeliveryMethod = SmtpDeliveryMethod.Network,
    UseDefaultCredentials = false
};

using var message = new MailMessage("from@example.com", "to@example.com")
{
    Subject = "Test Email",
    Body = "This email will be captured by Spamma"
};

smtpClient.Send(message);
```

## Node.js (Nodemailer)

```javascript
const nodemailer = require('nodemailer');

const transporter = nodemailer.createTransport({
  host: 'localhost',
  port: 1025,
  secure: false,
  ignoreTLS: true
});

await transporter.sendMail({
  from: 'sender@example.com',
  to: 'recipient@example.com',
  subject: 'Test Email',
  text: 'This email will be captured by Spamma'
});
```

## Python

```python
import smtplib
from email.mime.text import MIMEText

sender = 'sender@example.com'
recipient = 'recipient@example.com'
subject = 'Test Email'
body = 'This email will be captured by Spamma'

msg = MIMEText(body)
msg['Subject'] = subject
msg['From'] = sender
msg['To'] = recipient

with smtplib.SMTP('localhost', 1025) as server:
    server.sendmail(sender, recipient, msg.as_string())
```

## CI pipelines

- Bring up Spamma in your test stage via Docker Compose.
- Point application SMTP settings at the Spamma service host/port.
- Use the UI or upcoming API to assert on captured messages.
