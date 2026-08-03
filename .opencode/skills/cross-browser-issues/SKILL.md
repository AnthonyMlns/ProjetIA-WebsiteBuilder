---
name: cross-browser-issues
description: Problèmes cross-browser rencontrés et solutions documentées
---
## Problèmes récurrents

### Chrome / Edge (Chromium)
| Problème | Solution |
|----------|----------|
| Auto-fill styles impossibles à override | `:-webkit-autofill` + box-shadow inset |
| Scrollbar styling limité | `::-webkit-scrollbar` |
| `100vh` inclut la barre d'outils mobile | `100dvh` |

### Firefox
| Problème | Solution |
|----------|----------|
| `scrollbar-width: thin` différent | Accepter la différence |
| Quelques propriétés CSS non supportées | Vérifier sur caniuse.com |
| `:focus-visible` bien géré | Normal, aucune action |

### Safari (iOS + macOS)
| Problème | Solution |
|----------|----------|
| `100vh` = viewport + toolbar (bounce scroll) | `100dvh` ou `-webkit-fill-available` |
| Pas de `sticky` sur `position: sticky` dans table | Éviter, ou JavaScript |
| Safari mobile zoom sur input focus | `font-size: 16px` minimum |
| `date` input non supporté | Input text + pattern |

### Edge Legacy (pre-Chromium)
- Ne plus supporter

## Checklist
- [ ] Testé sur Chrome, Firefox, Safari (desktop)
- [ ] Testé sur Safari iOS + Chrome Android (mobile)
- [ ] Les polices web s'affichent correctement
- [ ] Les formulaires sont utilisables partout
- [ ] Les animations fonctionnent (graceful degradation)

À enrichir après chaque projet.
