---
name: rollback-procedure
description: Procédures de rollback pour chaque type de déploiement
---
## Vercel

```bash
# Rollback via CLI
npx vercel rollback <deployment-id>

# Ou via dashboard : Deployments → ... → Rollback
```

## Docker

```bash
# Rollback vers version précédente
docker compose stop
docker compose rm -f
TAG=previous-version docker compose up -d

# Avec backup BDD
pg_restore --clean --dbname=$DATABASE_URL backup-before-deploy.dump
```

## Database rollback (Prisma)

```bash
# 1. Identifier la migration à rollback
npx prisma migrate status

# 2. Rollback
npx prisma migrate resolve --rolled-back "migration_name"

# 3. Réappliquer la précédente
npx prisma migrate deploy
```

## Feature flags

```ts
// Rollback sans déploiement
if (await featureFlags.isEnabled('new-checkout')) {
  // Nouveau checkout
} else {
  // Ancien checkout
}
```

## Procédure standard

```yaml
1. Détecter l'incident
2. Alerter l'équipe
3. Décider : rollback ou fix forward ?
4. Si rollback :
   a. Rollback code (git revert / deploiement précédent)
   b. Rollback BDD si breaking change
   c. Vérifier que l'ancienne version fonctionne
   d. Communiquer le statut
5. Post-mortem : analyser la cause
```

À enrichir après chaque incident.
