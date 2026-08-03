---
name: api-client
description: Patterns de communication client-serveur, cache et mutations
---
## Approches

| Approche | Quand | Pour |
|----------|-------|------|
| **tRPC** | Full-stack TypeScript | Types partagés, auto-complétion, DX |
| **TanStack Query + fetch/axios** | API REST standard | Cache, mutations, invalidation |
| **GraphQL (urql/Apollo)** | API flexible, sur-fetching | Équipe dédiée back |
| **SWR** | Next.js, simple | Cache + revalidation |
| **Plain fetch** | Très petit projet | Pas de dépendance |

## Pattern TanStack Query (recommandé REST)

```ts
// Client
const api = {
  base: (path: string) => `/api/v1${path}`,
  get: <T>(path: string) => fetch(api.base(path)).then(r => r.json() as T),
  post: <T>(path: string, body: unknown) => fetch(api.base(path), { method: 'POST', body: JSON.stringify(body), headers: {'Content-Type': 'application/json'} }).then(r => r.json() as T),
}

// Query hook
function usePosts() {
  return useQuery({
    queryKey: ['posts'],
    queryFn: () => api.get<Post[]>('/posts'),
    staleTime: 60_000,
  })
}

// Mutation hook
function useCreatePost() {
  const queryClient = useQueryClient()
  return useMutation({
    mutationFn: (data: CreatePost) => api.post('/posts', data),
    onSuccess: () => queryClient.invalidate({ queryKey: ['posts'] }),
  })
}
```

## Optimistic updates
```ts
useMutation({
  mutationFn: updateTodo,
  onMutate: async (newTodo) => {
    await queryClient.cancelQueries({ queryKey: ['todos'] })
    const previous = queryClient.getQueryData(['todos'])
    queryClient.setQueryData(['todos'], (old) => old.map(t => t.id === newTodo.id ? { ...t, ...newTodo } : t))
    return { previous }
  },
  onError: (err, newTodo, context) => {
    queryClient.setQueryData(['todos'], context?.previous)
  },
})
```

À enrichir après chaque projet.
