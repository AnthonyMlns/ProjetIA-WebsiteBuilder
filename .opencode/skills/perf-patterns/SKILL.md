---
name: perf-patterns
description: Patterns de performance frontend validés
---
## Core Web Vitals

| Métrique | Cible | Pire |
|----------|-------|------|
| LCP | < 2.5s | > 4s |
| FID / INP | < 100ms | > 300ms |
| CLS | < 0.1 | > 0.25 |

## Patterns

### Images
```tsx
// Next.js : always use Image component
<Image src={src} alt="" width={800} height={600} priority={isHero} loading={isHero ? undefined : "lazy"} />

// Avec srcset généré automatiquement
// Toujours spécifier width/height pour éviter CLS
```

### Bundle
```tsx
// Dynamic imports (lazy loading)
const HeavyChart = dynamic(() => import('@/components/HeavyChart'), { ssr: false, loading: () => <Skeleton /> })

// Route splitting (automatique avec Next.js App Router / pages)
```

### Rendu
```tsx
// Memoization
const ExpensiveList = memo(function ExpensiveList({ items }: { items: Item[] }) {
  return items.map(item => <ExpensiveItem key={item.id} item={item} />)
})

// useMemo / useCallback (seulement si nécessaire)
const sorted = useMemo(() => items.sort(), [items])
const handleClick = useCallback(() => setOpen(false), [])
```

### Virtualisation (longues listes)
```tsx
import { FixedSizeList } from 'react-window'
<FixedSizeList height={400} itemCount={items.length} itemSize={50}>
  {({ index, style }) => <div style={style}>{items[index]}</div>}
</FixedSizeList>
```

### CSS
- Tailwind purge CSS (automatique)
- Éviter les animations coûteuses (box-shadow, filter, width)
- Préférer transform/opacity pour les animations
- `content-visibility: auto` sur les sections hors-écran

À enrichir après chaque projet (bottlenecks rencontrés).
