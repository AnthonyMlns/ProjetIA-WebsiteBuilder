---
name: stack-decisions
description: Base de connaissances des stacks techniques utilisés, leurs avantages et retours d'expérience
---
## Frontend

### Next.js (App Router)
- **Pour :** SSR, SEO, full-stack possible, excellent DX
- **Contre :** Bundle size si mal configuré, complexité du routing App vs Pages
- **Idéal pour :** SaaS, e-commerce, blogs
- **Retour :** *À compléter*

### Astro
- **Pour :** Zero JS by default, islands architecture, performances
- **Contre :** Pas idéal pour apps très interactives
- **Idéal pour :** Landing pages, blogs, sites vitrine
- **Retour :** *À compléter*

### Vite + React / Vue
- **Pour :** Léger, flexible, excellent HMR
- **Contre :** SSR nécessite configuration supplémentaire
- **Idéal pour :** SPA, dashboards
- **Retour :** *À compléter*

## Backend

### Hono / Elysia (Bun)
- **Pour :** Ultra rapide, TypeScript natif, middleware simple
- **Contre :** Écosystème plus récent
- **Retour :** *À compléter*

### Fastify / Express (Node)
- **Pour :** Écosystème mature, plugins
- **Contre :** Express non maintenu activement
- **Retour :** *À compléter*

## ORM / BDD

| ORM | BDD | Pour | Contre |
|-----|-----|------|--------|
| Prisma | PostgreSQL | DX excellent, migrations, studio | Performances sur requêtes complexes |
| Drizzle | PostgreSQL / SQLite | Léger, SQL-like, performances | Moins de fonctionnalités que Prisma |
| SQLite (Turso/libsql) | Edge | Zéro config, réplication | Pas pour gros volume |

## CSS

| Solution | Pour | Contre |
|----------|------|--------|
| Tailwind CSS | Rapide, consistent, bundle petit | HTML verbeux, courbe d'apprentissage |
| CSS Modules | Isolation, vanilla CSS | Pas de design tokens natifs |
| Panda CSS / Vanilla Extract | Type-safe, tokens, build-time | Setup plus complexe |
| shadcn/ui | Copiable, customisable, accessible | Dépend de Tailwind |

À enrichir après chaque nouveau projet.
