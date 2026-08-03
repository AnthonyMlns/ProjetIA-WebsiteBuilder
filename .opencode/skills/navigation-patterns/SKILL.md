---
name: navigation-patterns
description: Patterns de navigation, quand utiliser quoi
---
## Types de navigation

### Top nav horizontale
**Quand :** Sites vitrine, landing, blogs, < 6 liens
**Mobile :** Hamburger menu ou bottom nav

### Sidebar latérale
**Quand :** Dashboard, SaaS, apps avec nombreuses sections
**Mobile :** Drawer overlay, toggle hamburger

### Bottom navigation
**Quand :** Apps mobiles, 3-5 sections principales
**Desktop :** Pas adapté, utiliser top/sidebar

### Breadcrumbs
**Quand :** Sites hiérarchiques (e-commerce, docs, SaaS)
**Utile :** Navigation, SEO, contexte

### Tabs
**Quand :** Contenu organisé en catégories au sein d'une même page
**Mobile :** Scrollable tabs

### Pagination vs Infinite scroll

| Critère | Pagination | Infinite scroll |
|---------|------------|-----------------|
| Contenu homogène | Non | Oui (social, feed) |
| Besoin footer | Oui | Non |
| SEO | Oui | Non (sauf si pagination sous-jacente) |
| Performance | Charge par page | Charge au scroll (memoire) |
| Retrouver un élément | Facile (numéro page) | Difficile |
| E-commerce | Oui | Non recommandé |

### Search
- Barre de recherche accessible partout
- Résultats avec filtres
- Raccourci clavier (Ctrl+K ou /)
- Recherche instantanée avec debounce (300ms)
- "Aucun résultat" avec suggestions

À enrichir après chaque projet.
