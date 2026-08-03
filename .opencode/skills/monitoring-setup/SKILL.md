---
name: monitoring-setup
description: Configuration de monitoring — Sentry, uptime, logs, métriques
---
## Monitoring stack

| Outil | Usage | Prix |
|-------|-------|------|
| **Sentry** | Error tracking | Gratuit (5k events/mois) |
| **Better Stack** (ancien Better Uptime) | Uptime monitoring | Gratuit (3 monitors) |
| **Checkly** | E2E + API monitoring | Gratuit (5 checks) |
| **Logtail / Better Stack** | Log management | Gratuit (1 GB/mois) |
| **Grafana** | Dashboards | Gratuit (auto-hébergé) |
| **Prometheus** | Métriques | Gratuit |
| **Datadog** | Tout-en-un | Payant cher |

## Sentry setup

```ts
// next.js
import * as Sentry from '@sentry/nextjs'
Sentry.init({
  dsn: process.env.SENTRY_DSN,
  tracesSampleRate: 0.1, // 10% en prod
  environment: process.env.NODE_ENV,
  enabled: process.env.NODE_ENV === 'production',
})
```

## Health check endpoint
```ts
// /api/health
app.get('/api/health', (c) => {
  return c.json({ status: 'ok', timestamp: new Date().toISOString(), uptime: process.uptime() })
})
```

## Uptime checks
- Endpoint health check toutes les 5 min
- Synthetique browser check (Checkly / Playwright)
- Alerte email / Slack / Discord si down

## Alertes
- Erreurs 500 : Slack immédiat
- Uptime down : SMS / appel (PagerDuty)
- P95 latence > 2s : Slack
- Erreur rate > 1% : Slack

À enrichir après chaque projet.
