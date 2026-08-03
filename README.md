# Pipeline Agents IA — Création de sites web

Pipeline de 7 agents spécialisés + 1 orchestrateur pour créer des sites web de A à Z.

## Architecture

```
.orchestrator (primary)
├── @analyst         → Recueil du besoin
├── @architect       → Architecture technique
├── @designer        → UI/UX Design
├── @dev-frontend    → Frontend
├── @dev-backend     → Backend
├── @qa              → Tests & Validation
└── @devops          → Déploiement
```

## Utilisation

```bash
# Lancer le pipeline
opencode --agent orchestrator
# Puis décrire le projet

# Ou lancer un agent spécifique
opencode --agent analyst "Analyse ce besoin: ..."
```

## Skills

Chaque agent dispose de skills spécialisés qui s'enrichissent à chaque projet :

| Agent | Skills |
|-------|--------|
| Analyst | 7 skills (questionnaire, estimation, red-flags...) |
| Architect | 7 skills (stack, ADR, BDD, auth, security...) |
| Designer | 8 skills (tokens, états, responsive, a11y...) |
| Dev-Frontend | 9 skills (composants, perf, tests, i18n...) |
| Dev-Backend | 9 skills (API, validation, pagination, search...) |
| QA | 8 skills (coverage, edge-cases, a11y, load...) |
| DevOps | 8 skills (Docker, CI/CD, monitoring, backup...) |

Total : **56 skills** évolutifs.

## Projets

Les projets sont stockés dans `projects/<nom-projet>/` avec la structure :

```
projects/<nom>/
  specs/           # Cahier des charges, user stories
  architecture/    # Stack, data model, ADR
  design/          # Tokens, wireframes, composants
  frontend/        # Code frontend
  backend/         # Code backend
  qa/              # Tests, rapports, bugs
  devops/          # Déploiement, monitoring
  decisions/       # Décisions clés archivées
```

## Cycle de vie

1. Analyser
2. Architecturer
3. Designer + Coder (parallèle)
4. Tester
5. Déployer
6. Apprendre (post-mortem → skills++)
