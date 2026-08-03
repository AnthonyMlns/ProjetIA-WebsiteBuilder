---
name: folder-structure
description: Conventions de structure de dossiers par framework, testées et validées
---
## Next.js (App Router)
```
src/
  app/            # Pages et routes (App Router)
    (marketing)/
    (dashboard)/
    api/
  components/
    ui/           # Primitives (Button, Input, Modal...)
    features/     # Composants métier (ProductCard, CheckoutForm)
    layouts/      # Layouts (Sidebar, Header, Footer)
  lib/            # Fonctions utilitaires, clients API
  hooks/          # Custom hooks (useAuth, useDebounce...)
  stores/         # État global (Zustand, Context)
  types/          # Types TypeScript partagés
  utils/          # Fonctions pures (formatDate, cn...)
  i18n/           # Traductions (si multilingue)
public/
  images/
  fonts/
```

## React SPA (Vite)
```
src/
  assets/         # Images, styles globaux
  components/
    ui/
    features/
  hooks/
  lib/
  pages/          # Pages (une par route)
  layouts/
  stores/
  types/
  utils/
  routes/         # Config de routage
  services/       # API clients, appels serveur
```

## API Backend
```
src/
  routes/         # Définition des routes / endpoints
  controllers/    # Logique des endpoints
  services/       # Logique métier
  middleware/     # Auth, validation, error, rate-limit
  models/         # Modèles de données / ORM
  validators/     # Schémas de validation (Zod)
  utils/          # Utilitaires
  config/         # Configuration (env, DB, auth)
  types/          # Types partagés
tests/
  unit/
  integration/
```

À enrichir après chaque projet avec les améliorations.
