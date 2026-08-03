---
name: a11y-patterns
description: Patterns d'accessibilité validés — WCAG 2.1 AA
---
## Règles générales
- Tout est navigable au clavier (Tab, Shift+Tab, Enter, Escape)
- Tout contenu non textuel a un `alt` text pertinent
- Contraste minimum 4.5:1 pour le texte, 3:1 pour les gros titres
- Les animations respectent `prefers-reduced-motion`

## Patterns validés

### Skip to content
```html
<a href="#main-content" class="skip-link">Aller au contenu</a>
```

### Focus management
- Modals : focus trap, retour au déclencheur à la fermeture
- SPA : focus sur le titre de la nouvelle page
- Menu mobile : focus dans le menu ouvert
- `aria-live` pour les mises à jour dynamiques

### Formulaires
- Champs avec `label` explicite (pas de placeholder comme label)
- Messages d'erreur liés via `aria-describedby`
- Validation en temps réel annoncée via `aria-live="polite"`
- `fieldset` + `legend` pour les groupes de radios/checkboxes

### Images et médias
- Images décoratives : `alt=""`
- Images informatives : `alt` descriptif
- Icônes : `role="img"` + `aria-label` ou texte caché
- Vidéos : sous-titres, transcription

### Couleurs
- Ne pas utiliser la couleur comme seule information
- Liens soulignés (pas seulement colorés)
- Dark mode avec contraste suffisant

### Navigation
- `aria-current="page"` sur le lien actif
- Breadcrumbs avec `aria-label="Breadcrumb"` et `aria-current="page"`
- Menu avec `role="navigation"` et `aria-label`
- Recherche : `role="search"`

### Annonces dynamiques
- Toast : `role="alert"` ou `aria-live="assertive"`
- Loading : `aria-busy="true"`
- Compteur : `aria-live="polite"` pour les mises à jour

## Checklist projet
- [ ] Parcours clavier complet
- [ ] Contraste validé (axe DevTools)
- [ ] Screen reader test (NVDA / VoiceOver)
- [ ] Tous les formulaires ont des labels
- [ ] Modals / menus accessibles
- [ ] `prefers-reduced-motion` respecté

À enrichir après chaque audit a11y.
