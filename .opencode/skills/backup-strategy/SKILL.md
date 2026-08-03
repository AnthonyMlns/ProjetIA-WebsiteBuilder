---
name: backup-strategy
description: Stratégie de backup — BDD, fichiers, plan de restauration
---
## Backup BDD

### PostgreSQL (pg_dump)
```bash
# Backup daily
pg_dump --no-owner --no-acl -Fc dbname > backup/$(date +%Y-%m-%d).dump

# Restore
pg_restore --no-owner --dbname=dbname backup.dump
```

### PostgreSQL (WAL-G — recommandé prod)
```bash
# Continuous archiving + point-in-time recovery
wal-g backup-push $PGDATA
wal-g backup-fetch /restore LATEST
```

## Backup fichiers
```bash
# S3 sync
aws s3 sync /data s3://bucket/backups/$(date +%Y-%m-%d)
```

## Rétention
| Type | Rétention |
|------|-----------|
| Backup quotidien | 7 jours |
| Backup hebdomadaire | 4 semaines |
| Backup mensuel | 12 mois |
| WAL archives | 30 jours (PITR) |

## Tests de restauration
- Tester la restauration 1x par mois
- Automatiser le test dans un environnement staging
- Documenter la procédure dans le runbook

## Procédure d'urgence
```bash
# 1. Arrêter l'app
docker compose down
# 2. Restaurer la BDD
pg_restore --clean --dbname=$DATABASE_URL latest.dump
# 3. Restaurer les fichiers
aws s3 sync s3://bucket/backup/latest /data
# 4. Redémarrer
docker compose up -d
```

À enrichir après chaque projet.
