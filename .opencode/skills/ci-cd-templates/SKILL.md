---
name: ci-cd-templates
description: Templates CI/CD prêts à l'emploi — GitHub Actions, GitLab CI
---
## GitHub Actions (Node.js + Next.js)

```yaml
# .github/workflows/ci.yml
name: CI
on: [push, pull_request]
jobs:
  validate:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with: { node-version: 22 }
      - run: npm ci
      - run: npm run lint
      - run: npm run typecheck
      - run: npm run test -- --coverage
      - run: npm run build
```

## GitHub Actions (Déploiement)

```yaml
name: Deploy
on: { push: { branches: [main] } }
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - run: npm ci && npm run build
      - name: Deploy to Vercel
        uses: amondnet/vercel-action@v25
        with:
          vercel-token: ${{ secrets.VERCEL_TOKEN }}
          vercel-org-id: ${{ secrets.VERCEL_ORG_ID }}
          vercel-project-id: ${{ secrets.VERCEL_PROJECT_ID }}
          vercel-args: '--prod'
```

## GitLab CI

```yaml
# .gitlab-ci.yml
stages: [lint, test, build, deploy]
lint: { script: npm run lint }
test: { script: npm run test -- --coverage }
build: { script: npm run build }
deploy: { script: npm run deploy, only: [main] }
```

## GitHub Actions (Docker)

```yaml
- name: Build and push Docker image
  uses: docker/build-push-action@v5
  with:
    push: true
    tags: ghcr.io/${{ github.repository }}:${{ github.sha }}
```

## Conventions
- CI sur chaque push/PR
- Déploiement auto sur main (avec possibilité de rollback)
- Secrets dans GitHub Secrets / GitLab CI variables, jamais dans le code
- Notifications en cas d'échec (Slack, Discord, email)

À enrichir après chaque projet.
