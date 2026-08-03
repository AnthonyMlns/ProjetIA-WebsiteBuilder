---
name: cost-tracker
description: Suivi des coûts mensuels par service, alertes de dépassement
---
## Coûts par service (à remplir par projet)

| Service | Plan | Coût/mois | Notes |
|---------|------|-----------|-------|
| Hébergement | - | - | - |
| BDD | - | - | - |
| Domaine | - | - | - |
| Email | - | - | - |
| Monitoring | - | - | - |
| CDN | - | - | - |
| API tierces | - | - | - |
| Auth | - | - | - |
| **Total** | | **€0/mois** | |

## Alertes
- Mettre un budget max par projet
- Alerte à 80% du budget
- Revue mensuelle des coûts
- Identifier les services inutilisés

## Optimisations
- Mettre en veille les environnements non prod (sleep mode)
- Utiliser le cache pour réduire les appels API payants
- Choisir le plan adapté à l'usage réel
- Mutualiser les services entre projets si possible

## Coûts fixes vs variables
| Type | Exemple | Impact |
|------|---------|--------|
| Fixe | Domaine, hébergement fixe | Prévisible |
| Variable | BDD serverless, API calls | À surveiller |
| Usage | Bandwidth, storage | Scalable |

À enrichir après chaque projet.
