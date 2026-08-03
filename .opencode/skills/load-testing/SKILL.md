---
name: load-testing
description: Tests de charge — k6 scripts, métriques clés et seuils
---
## k6 (recommandé)

```js
// load-test.js
import http from 'k6/http'
import { check, sleep } from 'k6'

export const options = {
  stages: [
    { duration: '30s', target: 20 },  // Montée à 20 utilisateurs
    { duration: '1m', target: 20 },   // Maintien
    { duration: '30s', target: 0 },   // Descente
  ],
  thresholds: {
    http_req_duration: ['p(95)<2000'],  // 95% des requêtes < 2s
    http_req_failed: ['rate<0.01'],     // < 1% d'erreurs
  },
}

export default function () {
  const res = http.get('https://example.com/api/posts')
  check(res, { 'status is 200': (r) => r.status === 200 })
  sleep(1)
}
```

## Métriques clés
| Métrique | Seuil alerte | Seuil critique |
|----------|-------------|----------------|
| Temps de réponse moyen | < 500ms | < 2s |
| p95 | < 1s | < 3s |
| p99 | < 2s | < 5s |
| Taux d'erreur | < 1% | < 5% |
| Requêtes/s | Dépend du projet | - |
| CPU serveur | < 70% | < 90% |
| RAM | < 80% | < 95% |

## Types de tests
- **Smoke test** : 1-5 VUs, vérifier que ça marche
- **Load test** : trafic normal
- **Stress test** : au-delà du trafic normal
- **Spike test** : montée brutale
- **Soak test** : longue durée (1h+)

À enrichir après chaque projet avec les bottlenecks découverts.
