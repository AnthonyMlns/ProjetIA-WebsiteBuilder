---
name: scaling-limits
description: À partir de quel volume chaque solution commence à montrer ses limites
---
## Frontend

| Techno | Limite | Symptôme | Solution |
|--------|--------|----------|----------|
| Next.js (SSR) | 10k pages | Build time long | ISR, incremental build |
| React SPA | 500k composants | Mémoire | Virtualisation (react-window) |
| Images non optimisées | 100 images | LCP > 4s | next/image, CDN, WebP/AVIF |
| Bundle JS | > 500KB | FCP > 3s | Dynamic imports, code splitting |

## Backend

| Techno | Limite | Symptôme | Solution |
|--------|--------|----------|----------|
| SQLite | 100 utilisateurs concurrents | Write lock | Migrer vers PostgreSQL |
| PostgreSQL | 1000 req/s sur instance simple | CPU 100% | Connection pooling, read replicas |
| API REST | 100 endpoints | Maintenance | GraphQL, tRPC, modularisation |
| JWT non refresh | 1h | Reconnexion | Refresh token rotation |

## BDD

| BDD | Limite | Symptôme |
|-----|--------|----------|
| SQLite | 1 write à la fois | Lock errors |
| PostgreSQL sans index | 100k lignes | Requêtes lentes |
| Tables non partitionnées | 10M lignes | Maintenance lourde |
| Sans cache | 500 req/s | CPU BDD saturée |

## Règles
- Noter les goulots d'étranglement rencontrés après chaque projet
- Projeter la croissance estimée du projet
- Prévoir le scaling avant qu'il ne devienne critique
