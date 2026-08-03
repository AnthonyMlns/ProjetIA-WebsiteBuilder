---
name: env-management
description: Gestion des variables d'environnement — validation, conventions, secrets
---
## Structure

```env
# .env.example — commit dans git
NODE_ENV=development
DATABASE_URL=postgres://user:pass@localhost:5432/db
SESSION_SECRET=change-me
NEXT_PUBLIC_SITE_URL=http://localhost:3000

# .env.local — PAS commit (gitignoré)
DATABASE_URL=postgres://user:realpassword@localhost:5432/db
SESSION_SECRET=super-secret-key-12345

# .env.production — PAS commit, stocké dans vault
```

## Validation au startup

```ts
// src/env.ts (Zod validation)
import { z } from 'zod'

const envSchema = z.object({
  NODE_ENV: z.enum(['development', 'production', 'test']),
  DATABASE_URL: z.string().url(),
  SESSION_SECRET: z.string().min(32),
  NEXT_PUBLIC_SITE_URL: z.string().url(),
})

export const env = envSchema.parse(process.env)
// Si validation échoue → l'app ne démarre pas
```

## Conventions
- `NEXT_PUBLIC_` préfixe pour les variables exposées au client (Next.js)
- `NUXT_` pour Nuxt
- `VITE_` pour Vite
- `REACT_APP_` pour CRA (déprécié)
- Jamais de secrets dans les variables `PUBLIC_`
- Préfixer par projet : `MYAPP_DB_URL`

## Où stocker les secrets
- Dev : `.env.local` gitignoré
- CI/CD : GitHub Secrets / GitLab CI variables
- Prod : Vault, AWS Secrets Manager, 1Password CLI, hébergeur (Vercel env)

À enrichir après chaque projet.
