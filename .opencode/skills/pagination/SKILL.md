---
name: pagination
description: Patterns de pagination — cursor vs offset, filtering, sorting
---
## Offset pagination

```ts
// Requête
GET /api/posts?page=1&perPage=20&sort=createdAt&order=desc

// Réponse
{ data: [...], meta: { page: 1, perPage: 20, total: 142, totalPages: 8 } }

// SQL
SELECT * FROM posts ORDER BY created_at DESC LIMIT 20 OFFSET 0
```

**Quand :** Pages de résultats, back-office, tableaux
**Limite :** OFFSET devient lent sur grosses tables (scan de toutes les lignes sautées)

## Cursor pagination

```ts
// Requête
GET /api/posts?cursor=eyJpZCI6IDUsICJjcmVhdGVkQXQiOiAiMjAyNC0wMS0wMVQwMDowMDowMFoifQ==&limit=20

// Réponse
{ data: [...], nextCursor: "...", hasMore: true }

// SQL
SELECT * FROM posts WHERE (created_at < $cursorDate OR (created_at = $cursorDate AND id < $cursorId)) ORDER BY created_at DESC, id DESC LIMIT 20
```

**Quand :** Flux infini, real-time, gros volumes, mobile
**Avantage :** Performant quelle que soit la profondeur

## Filtres

```ts
// Pattern standard
GET /api/posts?search=...&status=published&tags=react,typescript&dateFrom=2024-01-01&dateTo=2024-12-31
```

À enrichir après chaque projet.
