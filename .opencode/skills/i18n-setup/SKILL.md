---
name: i18n-setup
description: Configuration d'internationalisation, outils et patterns
---
## Solutions

| Solution | Pour | Contre |
|----------|------|--------|
| **next-intl** | Next.js App Router | Intégration naturelle, DX | Pas pour SPA |
| **react-i18next** | React universel | Très complet, large écosystème | Configuration verbose |
| **Lingui** | React, extraction auto | Messages extraction, build-time | Moins connu |
| **Intl native** | Très petit projet | Pas de dépendance | Pas de traductions, que des formats |

## next-intl setup (recommandé Next.js)

```
messages/
  en.json
  fr.json
  es.json
```

```json
// messages/fr.json
{ "home": { "title": "Accueil", "welcome": "Bienvenue {name}" } }
```

## Patterns

### Namespacing des clés
```
navigation.home
navigation.about
home.hero.title
home.features.item
common.save
common.cancel
errors.notFound
```

### Raccourci clavier
- Pas de nested deep (> 3 niveaux)
- Grouper par page/feature
- Préfixer `common.` pour les traductions partagées

### SEO multilingue
```tsx
// Next.js : hreflang dans metadata
export const metadata = {
  alternates: {
    languages: { 'en': '/en', 'fr': '/fr' },
  },
}
```

À enrichir après chaque projet.
