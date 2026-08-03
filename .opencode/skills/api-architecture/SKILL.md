---
name: api-architecture
description: Conventions d'architecture API — REST, versioning, format de réponse
---
## REST naming

```
GET    /api/v1/posts              # Lister
POST   /api/v1/posts              # Créer
GET    /api/v1/posts/:id          # Lire un
PUT    /api/v1/posts/:id          # Remplacer
PATCH  /api/v1/posts/:id          # Modifier partiellement
DELETE /api/v1/posts/:id          # Supprimer
GET    /api/v1/posts/:id/comments # Relations
POST   /api/v1/posts/:id/comments
```

Règles :
- Noms au pluriel (`/posts` pas `/post`)
- Pas de verbes dans l'URL (`/create-post` → POST `/posts`)
- Versioning dans l'URL (v1, v2)

## Format de réponse standard

### Succès
```json
{ "data": { ... }, "meta": { "page": 1, "total": 42, "perPage": 20 } }
```

### Erreur
```json
{ "error": { "code": "VALIDATION_ERROR", "message": "L'email est invalide", "details": [{ "field": "email", "message": "Format invalide" }] } }
```

## Codes HTTP
- `200` — OK
- `201` — Créé
- `204` — Pas de contenu (DELETE)
- `400` — Bad Request (validation)
- `401` — Non authentifié
- `403` — Interdit
- `404` — Introuvable
- `409` — Conflit (doublon)
- `422` — Unprocessable Entity
- `429` — Trop de requêtes
- `500` — Erreur serveur

À enrichir après chaque projet.
