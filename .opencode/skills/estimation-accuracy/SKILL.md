---
name: estimation-accuracy
description: Suivi de la précision des estimations pour améliorer les projections futures
---
## History

| Projet | Estimé (jours) | Réel (jours) | Écart % | Raison écart |
|--------|----------------|--------------|---------|--------------|
| - | - | - | - | - |

## Facteurs de sous-estimation récurrents
1. *À compléter après chaque projet*
2. Configuration initiale (outillage, CI, déploiement)
3. Bugs inattendus d'intégration
4. Contournements pour limitations techniques
5. Allers-retours de validation client

## Facteurs de surestimation
1. Réutilisation de composants existants
2. Templates et générateurs
3. IA-assisted coding

## Coefficients correctifs
- Type "landing page" : appliquer un facteur x1.2 sur l'estimation initiale
- Type "SaaS with auth" : x1.5
- Type "e-commerce" : x1.8
- Type "avec équipe existante" : x0.9
- Type "from scratch" : x1.3

## Règle
Toucher ce skill seulement à la fin du projet, pendant le post-mortem.
