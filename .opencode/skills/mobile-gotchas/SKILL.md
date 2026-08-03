---
name: mobile-gotchas
description: Pièges mobiles fréquents et solutions documentées
---
## Problèmes courants

### Viewport
```html
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
```
- `100vh` ≠ hauteur réelle sur mobile → utiliser `100dvh`
- Safe areas (iPhone X+) : `env(safe-area-inset-top)`, `padding-bottom: env(safe-area-inset-bottom)`
- Keyboard overlay : utiliser `visualViewport` API

### Touch
- `:hover` reste actif après tap → utiliser `@media (hover: hover)`
- Ghost clicks : prévenir avec `touch-action: manipulation`
- Swipe gestures : éviter de conflit avec le scroll natif
- `touchstart` delay 300ms : `touch-action: manipulation` ou FastClick (plus nécessaire)

### Input zoom
```css
input, textarea, select { font-size: 16px; } /* Empêche le zoom automatique */
```

### Safe areas
```css
body { padding-top: env(safe-area-inset-top); padding-bottom: env(safe-area-inset-bottom); padding-left: env(safe-area-inset-left); padding-right: env(safe-area-inset-right); }
```

### Bottom nav
- Éviter `position: fixed` bottom si clavier ouvert → utiliser `visualViewport` height
- Ajouter un padding-bottom pour la home indicator

### Performance mobile
- Images : WebP/AVIF, responsive avec `srcset`
- Éviter les animations CSS coûteuses (box-shadow)
- Bundle < 200KB (critical path)
- Lazy loading hors écran

À enrichir après chaque projet.
