---
name: error-boundaries
description: Pattern Error Boundary pour React, fallback UI et logging
---
## Implementation React

```tsx
class ErrorBoundary extends React.Component<
  { fallback: ReactNode; children: ReactNode },
  { hasError: boolean; error?: Error }
> {
  state = { hasError: false }

  static getDerivedStateFromError(error: Error) {
    return { hasError: true, error }
  }

  componentDidCatch(error: Error, info: React.ErrorInfo) {
    // Log to Sentry / monitoring
    console.error('ErrorBoundary caught:', error, info)
  }

  render() {
    if (this.state.hasError) {
      return this.props.fallback
    }
    return this.props.children
  }
}
```

## Usage

```tsx
<ErrorBoundary fallback={<ErrorState message="Erreur de chargement" onRetry={() => window.location.reload()} />}>
  <ExpensiveComponent />
</ErrorBoundary>
```

## Où placer les Error Boundaries
- Par feature / page (pas un seul global)
- Autour des composants qui chargent des données
- Autour de chaque route/page dans le router
- Ne pas wrapper le layout entier (la navigation doit survivre)

## Niveaux de fallback

| Localisation | Fallback |
|-------------|----------|
| Composant | Message discret, retry |
| Page | Page d'erreur avec retry |
| Global | 500 page (Next.js error.tsx) |
| App entière | "Quelque chose s'est mal passé, rechargez" |

À enrichir après chaque projet.
