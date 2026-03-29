# Rivium Self-Hosted

Run Rivium services on your own infrastructure. Your data, your control.

## Available Services

| Service | Description | Docker Image |
|---------|-------------|-------------|
| [**Rivium Console**](console/) | Shared dashboard for all services | [Dashboard](https://github.com/orgs/Rivium-co/packages/container/package/rivium-console-selfhosted-dashboard) · [API](https://github.com/orgs/Rivium-co/packages/container/package/rivium-console-selfhosted-api) |
| [**RiviumTrace**](trace/) | Error tracking, APM & logs | [API](https://github.com/orgs/Rivium-co/packages/container/package/rivium-trace-selfhosted) |

## Quick Start

```bash
mkdir rivium-selfhosted && cd rivium-selfhosted

# 1. Console (dashboard)
cp console/docker-compose.yml .
cp console/.env.example .env
# Edit .env — set JWT secrets and database password
docker compose up -d
# → http://localhost:3000 (register to become server owner)

# 2. RiviumTrace (error tracking)
cp trace/docker-compose.yml docker-compose.trace.yml
cp trace/.env.example .env.trace
# Edit .env.trace — set JWT secret and database password
docker compose -f docker-compose.trace.yml --env-file .env.trace up -d
# → Go to Console → Rivium Trace tab
```

## Plans & Pricing

Works immediately with a **free tier** — no license key, no sign-up.

| Feature | Free | Pro $29/mo | Business $79/mo |
|---------|------|-----------|-----------------|
| **Projects** | 1 | 5 | Unlimited |
| **Errors/month** | 50 | 2,000 | Unlimited |
| **Team members** | 2 | 5 | 50 |
| **Error tracking & Logs** | Yes | Yes | Yes |
| **APM & Web Vitals** | No | Yes | Yes |
| **Source maps / dSYM** | No | Yes | Yes |
| **Custom alert rules** | 1 | 3 | Unlimited |
| **Cron monitors** | 1 | 10 | Unlimited |
| **Integrations** | Email | Slack + Email | All |

Yearly pricing (2 months free): Pro $290/yr, Business $790/yr

## License Activation

1. Go to [rivium.co](https://rivium.co) → Dashboard → Billing → Self-Hosted
2. Choose a plan and complete payment
3. Copy your license key
4. Open your console → Dashboard → License → Paste and activate

## SDK Setup

Point your SDKs to your self-hosted RiviumTrace:

```javascript
// Next.js / Node.js
init({
  apiKey: 'rv_live_your_key_here',
  apiUrl: 'http://localhost:3001',  // your Trace server
});
```

```dart
// Flutter
RiviumTrace.initWithZone(
  RiviumTraceConfig(
    apiKey: 'rv_live_your_key_here',
    apiUrl: 'http://localhost:3001',
  ),
  () => runApp(MyApp()),
);
```

6 SDKs: Flutter, Next.js, Node.js, Laravel, iOS (Swift), Android (Kotlin)

## Ports

| Port | Service |
|------|---------|
| 3000 | Console Dashboard |
| 3004 | Console Auth API |
| 3001 | RiviumTrace API |

## Requirements

- Docker & Docker Compose
- 512 MB RAM (Console) + 1 GB RAM (RiviumTrace)

## Updates

```bash
docker compose pull && docker compose up -d
docker compose -f docker-compose.trace.yml pull && docker compose -f docker-compose.trace.yml up -d
```

## Support

- Free: [GitHub Issues](https://github.com/Rivium-co/rivium-selfhosted/issues)
- Pro: Email support
- Business: Priority support
- Contact: support@rivium.co

## Links

- Website: [rivium.co](https://rivium.co)
- Docs: [rivium.co/cloud/rivium-trace](https://rivium.co/cloud/rivium-trace)
