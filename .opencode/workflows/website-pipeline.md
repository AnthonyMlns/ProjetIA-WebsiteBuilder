# Pipeline de création de site web

## Déclenchement

```bash
opencode --agent orchestrator "Nouveau projet: [description]"
```

Ou depuis l'interface : sélectionner l'agent **Orchestrator** et décrire le projet.

## Déroulement

### Phase 1 : Analyse (agent: @analyst)
- Recueil du besoin via questionnaire
- Rédaction du cahier des charges
- Priorisation MVP (MoSCoW)
- **Livrable :** `projects/<nom>/specs/`

### Phase 2 : Architecture (agent: @architect)
- Choix du stack technique
- Data model
- API design
- Architecture Decision Records
- **Livrable :** `projects/<nom>/architecture/`

### Phase 3 : Design (agent: @designer) [parallélisable avec Phase 4]
- Design tokens
- Wireframes
- Spécifications composants
- Parcours utilisateur
- **Livrable :** `projects/<nom>/design/`

### Phase 4 : Développement Frontend (agent: @dev-frontend) [parallélisable avec Phase 3]
- Setup du projet
- Composants UI
- Pages et routage
- Connexion API
- **Livrable :** Code frontend + tests

### Phase 5 : Développement Backend (agent: @dev-backend) [si nécessaire]
- Setup serveur / BDD
- Modèles et migrations
- API endpoints
- Auth
- **Livrable :** Code backend + tests

### Phase 6 : QA (agent: @qa)
- Tests unitaires, intégration, E2E
- Audit accessibilité
- Tests cross-browser
- **Livrable :** `projects/<nom>/qa/`

### Phase 7 : DevOps (agent: @devops)
- Docker / CI/CD
- Déploiement
- Monitoring
- **Livrable :** `projects/<nom>/devops/`

### Phase 8 : Post-mortem
- Collecte des retours de chaque agent
- Mise à jour des skills
- Commit des apprentissages

## Notes
- Les phases 3 et 4 peuvent être parallélisées si le designer produit les tokens avant les wireframes
- Le post-mortem est obligatoire (c'est ce qui fait grandir le pipeline)
- Tout bug critique découvert en QA bloque le déploiement
- L'orchestrator peut itérer sur une phase si le résultat n'est pas satisfaisant
