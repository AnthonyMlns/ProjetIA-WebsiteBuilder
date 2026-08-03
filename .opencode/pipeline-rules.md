---
description: Règles globales du pipeline de création de sites web
---
# Règles du pipeline

## Règles générales
1. **Ordre** : Analyst → Architect → Designer/Dev-Frontend → Dev-Backend → QA → DevOps → Post-mortem
2. **Validation** : Chaque phase doit être validée avant de passer à la suivante
3. **Skills** : Chaque agent charge les skills pertinents au début de son travail
4. **Stockage** : Tous les livrables dans `projects/<nom-projet>/<phase>/`
5. **Parallélisation** : Designer et Dev-Frontend peuvent travailler en parallèle (design tokens d'abord)
6. **Itération** : L'orchestrator peut demander une révision d'une phase

## Règles de qualité
1. **Tests** : Tout code doit avoir des tests
2. **Accessibilité** : WCAG 2.1 AA minimum
3. **Sécurité** : Checklist de sécurité appliquée sur chaque projet
4. **Performance** : Lighthouse score > 85 sur mobile, > 90 sur desktop
5. **Documentation** : Chaque composant a sa spécification

## Règles d'évolution
1. **Skills** : Mis à jour après chaque projet (post-mortem)
2. **ADR** : Créé pour chaque décision architecturale significative
3. **Estimation** : Comparée au réel après chaque projet
4. **Risques** : Registre mis à jour après chaque projet
