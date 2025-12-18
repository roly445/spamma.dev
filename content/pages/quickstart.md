---
title: "Quickstart"
description: "Run Spamma locally for development and testing."
weight: 30
---

## Prerequisites

- .NET 10 SDK
- Node.js 20+
- Docker Desktop (for infra bundle)

## Start the stack

```bash
docker-compose up -d
```

## Run the app

```bash
dotnet run --project src/Spamma.App/Spamma.App/Spamma.App.csproj
```

## Build frontend assets (if you change them)

```bash
cd src/Spamma.App/Spamma.App
npm ci
npm run build
```

Open [https://localhost:7181](https://localhost:7181).

## Send a test email

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

Browse the captured message in the UI. Repeat with Nodemailer or Python if preferred.
