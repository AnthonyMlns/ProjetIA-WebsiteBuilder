---
name: mock-patterns
description: Patterns de mocking pour les tests — MSW, date, modules
---
## MSW (recommandé API mock)

```ts
// src/mocks/handlers.ts
export const handlers = [
  http.get('*/api/posts', () => {
    return HttpResponse.json([{ id: 1, title: 'Mock Post' }])
  }),
  http.post('*/api/posts', async ({ request }) => {
    const body = await request.json()
    return HttpResponse.json({ id: 2, ...body }, { status: 201 })
  }),
  http.get('*/api/posts/:id', ({ params }) => {
    return HttpResponse.json({ id: Number(params.id), title: `Post ${params.id}` })
  }),
  http.get('*/api/error', () => {
    return HttpResponse.json({ error: { code: 'INTERNAL_ERROR', message: 'Server error' } }, { status: 500 })
  }),
]
```

## Date mocking

```ts
// Vitest
beforeEach(() => { vi.useFakeTimers() })
afterEach(() => { vi.useRealTimers() })

test('formate date', () => {
  vi.setSystemTime(new Date('2024-06-15T10:00:00Z'))
  expect(formatDate(new Date())).toBe('15 juin 2024')
})
```

## Module mocking

```ts
vi.mock('@/lib/api', () => ({
  fetchPosts: vi.fn().mockResolvedValue([{ id: 1, title: 'Mock' }]),
}))

vi.mock('next/navigation', () => ({
  useRouter: () => ({ push: vi.fn(), replace: vi.fn() }),
  useSearchParams: () => new URLSearchParams(),
}))
```

## Network mocking en E2E (Playwright)
```ts
await page.route('**/api/posts', async route => {
  await route.fulfill({ json: [{ id: 1, title: 'E2E Mock' }] })
})
```

À enrichir après chaque projet.
