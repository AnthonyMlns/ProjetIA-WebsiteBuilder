---
name: search-patterns
description: Patterns de recherche — full-text, typo-tolerance, filtrage
---
## Solutions

| Solution | Quand | Setup |
|----------|-------|-------|
| **PostgreSQL pg_trgm** | Volume modéré, pas de nouvelle infra | Extension Postgres |
| **PostgreSQL full-text** | Recherche française / stemming | tsvector + index GIN |
| **Meilisearch** | Super DX, typo-tolerance, facettes | Serveur dédié, facile |
| **Algolia** | SaaS, très performant | Payant, vendor lock |
| **Typesense** | Open source, rapide | Serveur dédié |
| **Sonic** | Léger, overkill simple | Binaire Go |

## PostgreSQL pg_trgm (recommandé pour petit/moyen)

```sql
CREATE EXTENSION IF NOT EXISTS pg_trgm;
CREATE INDEX idx_posts_title_trgm ON posts USING GIN (title gin_trgm_ops);
CREATE INDEX idx_posts_content_trgm ON posts USING GIN (content gin_trgm_ops);

SELECT *, similarity(title, 'recherche') AS sim
FROM posts
WHERE title % 'recherche' OR content % 'recherche'
ORDER BY sim DESC
LIMIT 20;
```

## Meilisearch (recommandé pour moyen/gros)

```json
// Search params
{ "q": "requête", "limit": 20, "attributesToHighlight": ["*"], "filter": "status = published AND price > 10" }
```

À enrichir après chaque projet.
