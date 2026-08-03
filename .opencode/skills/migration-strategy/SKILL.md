---
name: migration-strategy
description: Stratégie de migration de base de données — Prisma, rollback, seed
---
## Prisma (recommandé)

### Workflow
```bash
npx prisma migrate dev --name add_post_status   # Dev : créer migration
npx prisma migrate deploy                        # Prod : appliquer
npx prisma db push                                # Proto rapide (pas prod)
```

### Règles
1. Une migration par changement
2. Toujours tester la migration DESC (rollback) avant de l'appliquer en prod
3. Les migrations sont commit dans git
4. Ne jamais éditer une migration déjà commitée
5. Si erreur en prod : `npx prisma migrate resolve --rolled-back`

### Seed
```ts
// prisma/seed.ts
async function main() {
  await prisma.user.create({ data: { email: 'admin@test.com', role: 'admin' } })
}
main().catch(e => { console.error(e); process.exit(1) }).finally(() => prisma.$disconnect())
```

## Rollback
```bash
npx prisma migrate resolve --rolled-back "<migration_name>"   # Marquer comme rolled back
npx prisma migrate deploy                                      # Revenir à la précédente
```

## Conventions
- Nommer les migrations avec préfixe : `add_`, `remove_`, `rename_`, `modify_`
- Ne pas supprimer de colonne sans s'assurer qu'elle n'est plus utilisée en production

À enrichir après chaque projet (problèmes de migration rencontrés).
