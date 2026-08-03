---
name: component-states
description: Définition des états que chaque composant UI doit gérer
---
## États universels

| État | Description | Visuel |
|------|-------------|--------|
| **Default** | Affichage normal | Style normal |
| **Hover** | Survol souris | Changement couleur, scale subtil |
| **Focus** | Focus clavier (Tab) | Outline visible, respecte reduced-motion |
| **Active** | Clic / pression | Enfoncement visuel |
| **Disabled** | Composant désactivé | Opacité réduite, curseur not-allowed |
| **Loading / Skeleton** | En cours de chargement | Skeleton, spinner, shimmer |
| **Empty** | Aucune donnée à afficher | Message + illustration + CTA |
| **Error** | Erreur de chargement | Message d'erreur + retry |
| **Success** | Action réussie | Feedback visuel (check, toast) |

## Par composant

### Button
- Default, Hover, Focus, Active, Disabled, Loading
- Variants : primary, secondary, ghost, danger, outline
- Sizes : sm, md, lg

### Input
- Default, Focus, Disabled, Error, Success
- Avec ou sans label, helper text, character count
- État error avec message validation

### Modal / Dialog
- Open (avec backdrop animé)
- Close (avec animation)
- Focus trap activé
- Escape pour fermer

### Table
- Chargement (skeleton rows)
- Vide (empty state avec CTA)
- Lignes sélectionnables
- Tri actif sur colonne
- Pagination

### Toast / Notification
- Success, Error, Warning, Info
- Auto-dismiss + animation sortie
- Stack de notifications

### Card
- Default, Hover (subtle elevation)
- Loading (skeleton)
- Image failed → fallback

À enrichir après chaque projet avec les nouveaux composants créés.
