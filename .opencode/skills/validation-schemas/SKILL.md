---
name: validation-schemas
description: Schémas de validation réutilisables (Zod), patterns et conventions
---
## Stack
- **Zod** côté client et serveur
- Schémas partagés dans un package `shared/` ou dossier `types/`
- Résolver Zod pour React Hook Form

## Schémas réutilisables

```ts
// shared/schemas/common.ts
export const email = z.string().email('Email invalide').min(1, 'Requis')
export const password = z.string().min(8, '8 caractères minimum').max(128).regex(/[A-Z]/, '1 majuscule').regex(/[0-9]/, '1 chiffre')
export const uuid = z.string().uuid()
export const url = z.string().url()
export const phone = z.string().regex(/^\+?[\d\s-]{8,15}$/)
```

## Patterns

### Schema → Type
```ts
const postSchema = z.object({
  title: z.string().min(3).max(100),
  content: z.string().min(10).max(10000),
  published: z.boolean().default(false),
  tags: z.array(z.string()).max(5).default([]),
})
type PostInput = z.infer<typeof postSchema>
type PostOutput = z.output<typeof postSchema>
```

### Transform
```ts
const dateString = z.string().transform(d => new Date(d))
```

### Coerce (formulaires → nombres)
```ts
const formSchema = z.object({
  age: z.coerce.number().min(0).max(150),
})
```

### Refinement (validation croisée)
```ts
z.object({ password, confirmPassword }).refine(d => d.password === d.confirmPassword, { message: 'Les mots de passe ne correspondent pas', path: ['confirmPassword'] })
```

À enrichir après chaque projet avec les patterns de validation complexes rencontrés.
