---
name: red-flags
description: Signaux d'alerte à détecter pendant l'analyse du besoin pour éviter les pièges
---
## Red flags client
- "C'est simple, juste une petite modification" → scope creep
- "Je veux exactement comme X, mais en mieux" → attentes irréalistes
- "On verra les détails plus tard" → flou dangereux
- "Je n'ai pas de budget, mais..." → pas de priorisation
- Le client ne sait pas qui valide → décisions bloquées
- "Il faut que ce soit prêt pour [date irréaliste]" → qualité sacrifiée
- Changement d'avis fréquent sur les mêmes sujets

## Red flags technique
- Stack imposé sans justification
- Pas de contrôle sur l'hébergement / le domaine
- Base de code existante non documentée
- Dépendances non maintenues ou vulnérables
- Pas de stratégie de test
- "On fera la sécurité après"

## Red flags projet
- Pas de cahier des charges écrit
- Plus de 3 interlocuteurs sans décideur clair
- Réunions sans compte-rendu
- "On a déjà commencé avec quelqu'un d'autre" → reprise complexe
- Contrat flou sur la propriété du code

## Actions recommandées
- Red flag détecté → documenter et partager avec l'orchestrator
- Red flag critique → demander une clarification avant de continuer
- Red flag ignoré → revenir dans le post-mortem
