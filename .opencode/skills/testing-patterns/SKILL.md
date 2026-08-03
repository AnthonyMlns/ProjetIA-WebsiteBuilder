---
name: testing-patterns
description: Patterns de tests frontend validés — Vitest, Testing Library, MSW, Playwright
---
## Stack recommandé
- **Vitest** — unit tests
- **Testing Library** — component tests (user-centric)
- **MSW** — API mocking
- **Playwright** — E2E

## Structure

```
tests/
  unit/           # Fonctions pures, hooks
  components/     # Component tests (Testing Library)
  integration/    # Pages, flux complets
  e2e/            # Playwright (user flows)
```

## Patterns

### Component test (user-centric)
```tsx
// On teste le comportement, pas l'implémentation
test('affiche erreur quand email invalide', async () => {
  render(<ContactForm />)
  await user.click(screen.getByRole('button', { name: 'Envoyer' }))
  expect(screen.getByText('Email invalide')).toBeVisible()
})
```

### MSW handler
```ts
export const handlers = [
  http.get('/api/posts', () => {
    return HttpResponse.json([{ id: 1, title: 'Test Post' }])
  }),
]
```

### Hook test
```ts
test('useCounter increment', () => {
  const { result } = renderHook(() => useCounter())
  act(() => result.current.increment())
  expect(result.current.count).toBe(1)
})
```

### Playwright E2E
```ts
test('complete purchase flow', async ({ page }) => {
  await page.goto('/product/1')
  await page.click('text=Ajouter au panier')
  await page.click('text=Commander')
  await expect(page.locator('text=Merci pour votre commande')).toBeVisible()
})
```

À enrichir après chaque projet.
