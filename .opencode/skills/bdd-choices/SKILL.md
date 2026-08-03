---
name: bdd-choices
description: Comparatif des bases de données avec contexte d'utilisation et retours d'expérience
---
## Choix par cas d'usage

| Cas d'usage | BDD recommandée | Pourquoi |
|-------------|-----------------|----------|
| App standard relationnelle | PostgreSQL | Mature, fiable, extensions (pgvector, postgis) |
| App multirégion / edge | Turso (libsql) | Réplication, faible latence |
| Cache / sessions | Redis | Ultra rapide, TTL, pub/sub |
| Recherche full-text | PostgreSQL (pg_trgm) ou Meilisearch | Selon volume |
| Analytics / logs | ClickHouse / SQLite | OLAP vs léger |
| Fichiers / médias | S3 (R2 / MinIO) | Scalable, pas de BDD |
| Queue / jobs | Redis Bull / RabbitMQ | Selon complexité |
| BDD embarquée / offline | SQLite | Zéro config, mobile |

## Comparaison détaillée

| Critère | PostgreSQL | SQLite | MySQL | Turso |
|---------|-----------|--------|-------|-------|
| Setup | Moyen | Facile | Moyen | Facile |
| Perf écriture | Haute | Basse (mono-writer) | Haute | Haute |
| Concurrency | Excellente | Limitée | Bonne | Bonne |
| Extensions | Très riche | Limité | Riche | Limité |
| Hosting | Supabase, Neon, Railway, AWS | Intégré | PlanetScale, AWS | Turso Cloud |
| Prix | Gratuit - $$ | Gratuit | Gratuit - $$$ | Gratuit - $$ |

À enrichir après chaque projet.
