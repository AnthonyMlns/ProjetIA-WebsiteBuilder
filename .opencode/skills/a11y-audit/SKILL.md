---
name: a11y-audit
description: Audit d'accessibilité — outils, checklist, patterns
---
## Outils
- **axe DevTools** — navigateur, CI
- **Lighthouse** — rapport automatisé
- **WAVE** — visualisation des problèmes
- **NVDA** (Windows) / **VoiceOver** (macOS) — screen readers
- **Pa11y CI** — CI/CD integration

## Checklist rapide

### Clavier
- [ ] Tous les éléments interactifs sont accessibles au Tab
- [ ] L'ordre de tabulation est logique
- [ ] Les modals / menus ont un focus trap
- [ ] Escape ferme les overlays
- [ ] `:focus-visible` est stylé

### Contraste
- [ ] Texte normal : ratio ≥ 4.5:1
- [ ] Texte large (≥ 18px bold / ≥ 24px regular) : ratio ≥ 3:1
- [ ] Composants UI : ratio ≥ 3:1
- [ ] Pas d'information transmise uniquement par la couleur

### Screen reader
- [ ] Images : `alt` text pertinent ou `alt=""` si décorative
- [ ] Icônes : `role="img"` + `aria-label`
- [ ] Formulaires : chaque champ a un `<label>` lié
- [ ] Messages d'erreur : `aria-describedby`
- [ ] Mises à jour dynamiques : `aria-live`
- [ ] Régions : `<nav>`, `<main>`, `<aside>` avec `aria-label`
- [ ] Têtes de tableau : `<th scope="col/row">`

### Sémantique
- [ ] Hiérarchie de titres logique (h1 → h2 → h3)
- [ ] Landmarks HTML5 utilisés
- [ ] Listes avec `<ul>` / `<ol>`
- [ ] Tableaux avec `<caption>`

### Motion
- [ ] `prefers-reduced-motion` respecté
- [ ] Aucune animation flashante (> 3 flashs/sec)

À enrichir après chaque audit.
