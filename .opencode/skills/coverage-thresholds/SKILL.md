---
name: coverage-thresholds
description: Seuils de couverture de tests par type de projet
---
## Seuils recommandés

| Type | Unité | Intégration | E2E |
|------|-------|-------------|-----|
| Landing page | 60% | 40% | 30% (1 parcours) |
| SaaS MVP | 70% | 60% | 50% (parcours critique) |
| SaaS production | 80% | 70% | 70% (tous parcours) |
| E-commerce | 80% | 75% | 80% (checkout) |
| API pure | 85% | 80% | 50% |
| Library | 90% | 80% | - |

## Configuration Vitest
```ts
export default defineConfig({
  test: {
    coverage: {
      provider: 'v8',
      reporter: ['text', 'json-summary', 'html'],
      thresholds: {
        branches: 70,
        functions: 75,
        lines: 80,
        statements: 80,
      },
    },
  },
})
```

## Règles
- En dessous du seuil → le pipeline CI échoue
- Les seuils augmentent avec la maturité du projet
- Pas de régression : le coverage ne doit pas baisser

À enrichir après chaque projet.
