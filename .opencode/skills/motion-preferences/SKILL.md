---
name: motion-preferences
description: Patterns d'animations, transitions et respect des préférences utilisateur
---
## Principes
- Les animations doivent servir un but (feedback, orientation, delight)
- Pas d'animations gratuites ou purement décoratives
- Toujours respecter `prefers-reduced-motion`

## CSS `prefers-reduced-motion`

```css
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
    scroll-behavior: auto !important;
  }
}
```

## Animations fonctionnelles

| Usage | Animation | Durée |
|-------|-----------|-------|
| Page transition | Fade in | 300ms |
| Modal open | Scale + fade backdrop | 200ms |
| Modal close | Fade out | 150ms |
| Toast entrée | Slide in right | 250ms |
| Toast sortie | Fade + slide out | 200ms |
| Button hover | Background transition | 150ms |
| Skeleton loading | Pulse / shimmer | 1.5s loop |
| Accordion | Height expand | 250ms ease |
| Tab switch | Fade content | 150ms |
| Notification badge | Scale pulse | 300ms |

## Easing functions
```css
--ease-out: cubic-bezier(0.16, 1, 0.3, 1);
--ease-in-out: cubic-bezier(0.65, 0, 0.35, 1);
--ease-bounce: cubic-bezier(0.34, 1.56, 0.64, 1);
```

À enrichir après chaque projet avec les animations créées.
