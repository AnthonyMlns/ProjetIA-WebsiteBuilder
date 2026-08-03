---
name: risk-registry
description: Registre des risques récurrents, leur probabilité, impact et mitigation
---
## Risques identifiés

| Risque | Probabilité | Impact | Mitigation | Occurrences |
|--------|-------------|--------|------------|-------------|
| Scope creep | Élevée | Élevé | Cadrer strictement le MVP, tout hors scope = nouveau projet | - |
| Client non disponible | Moyenne | Moyen | Caler des points réguliers fixes, validation asynchrone | - |
| Technologie inconnue | Moyenne | Élevé | POC technique avant engagement, temps d'apprentissage | - |
| Dépendances externes (API) | Moyenne | Élevé | Mock en parallèle, fallback planning | - |
| Performance BDD | Faible | Moyen | Indexation, pagination, cache dès le départ | - |
| Sécurité (données client) | Faible | Critique | Checklist sécurité, audit, jamais stocker en clair | - |
| Turnover équipe | Faible | Élevé | Documentation continue, code review | - |
| Stack non maintenu | Faible | Moyen | Vérifier maintenance, popularité, communauté | - |

## À faire
- Mettre à jour les occurrences après chaque projet
- Ajouter les nouveaux risques identifiés
- Supprimer les risques devenus obsolètes

## Seuils d'alerte
- 3+ occurrences d'un même risque → mitigation obligatoire sur le prochain projet
- Impact critique + proba élevée → escalation orchestrator
