---
name: error-handling
description: Gestion d'erreurs backend — classes d'erreur, handler global, logging
---
## Classes d'erreur

```ts
export class AppError extends Error {
  constructor(public statusCode: number, public code: string, message: string, public details?: Record<string, unknown>) {
    super(message)
  }
}

export class NotFoundError extends AppError {
  constructor(resource: string) { super(404, 'NOT_FOUND', `${resource} introuvable`) }
}

export class ValidationError extends AppError {
  constructor(message: string, details?: Record<string, unknown>) { super(400, 'VALIDATION_ERROR', message, details) }
}

export class UnauthorizedError extends AppError {
  constructor() { super(401, 'UNAUTHORIZED', 'Authentification requise') }
}

export class ForbiddenError extends AppError {
  constructor() { super(403, 'FORBIDDEN', 'Accès refusé') }
}
```

## Handler global (Express / Hono)

```ts
app.onError((err, c) => {
  if (err instanceof AppError) {
    return c.json({ error: { code: err.code, message: err.message, details: err.details } }, err.statusCode)
  }
  // Erreur inattendue → log + 500
  console.error('Unhandled error:', err)
  return c.json({ error: { code: 'INTERNAL_ERROR', message: 'Erreur interne' } }, 500)
})
```

## Logging
```json
{ "level": "error", "message": "...", "stack": "...", "requestId": "...", "userId": "...", "timestamp": "..." }
```

À enrichir après chaque projet.
