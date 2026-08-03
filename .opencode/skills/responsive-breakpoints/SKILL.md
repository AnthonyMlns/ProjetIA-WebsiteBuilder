---
name: responsive-breakpoints
description: Breakpoints et patterns responsive validés par projet
---
## Breakpoints standards

```css
/* Mobile first */
/* < 640px : mobile (par défaut) */
@media (min-width: 640px) { /* sm : tablet portrait */ }
@media (min-width: 768px) { /* md : tablet landscape */ }
@media (min-width: 1024px) { /* lg : desktop */ }
@media (min-width: 1280px) { /* xl : desktop large */ }
@media (min-width: 1536px) { /* 2xl : wide */ }
```

## Patterns responsive

### Navigation
| Écran | Navigation |
|-------|-----------|
| Mobile (<768px) | Hamburger menu, sidebar overlay |
| Desktop | Top nav horizontale ou sidebar fixe |

### Layout
| Écran | Grille |
|-------|--------|
| Mobile | 1 colonne |
| Tablet | 2 colonnes |
| Desktop | 3-4 colonnes |

### Tableaux
| Écran | Comportement |
|-------|-------------|
| Desktop | Tableau normal |
| Mobile | Card view ou scroll horizontal |

### Images
```css
img { max-width: 100%; height: auto; }
```

### Typographie responsive
```css
h1 { font-size: clamp(1.75rem, 4vw, 2.5rem); }
```

À enrichir après chaque projet avec les breakpoints custom utilisés.
