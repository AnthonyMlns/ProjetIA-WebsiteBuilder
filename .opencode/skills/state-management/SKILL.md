---
name: state-management
description: Patterns de gestion d'état selon le besoin
---
## Recommandations

| Type d'état | Solution | Quand |
|-------------|----------|-------|
| Server state (API) | TanStack Query (React Query) / tRPC | Données venant du serveur |
| Global UI state | Zustand | State partagé (theme, sidebar, modals) |
| Form state | React Hook Form | Formulaires complexes |
| URL state | next/navigation (useSearchParams) | Filtres, pagination, recherche |
| Local state | useState / useReducer | State local à un composant |
| Auth state | NextAuth / Clerk context | Session utilisateur |
| Cache BDD | TanStack Query (stale time) | Données fréquentes |

## Patterns

### TanStack Query
```ts
// Toujours typer
const { data, isLoading, error } = useQuery<ResponseType>({
  queryKey: ['resource', id],
  queryFn: () => fetchResource(id),
  staleTime: 5 * 60 * 1000, // 5 min
})

// Mutations avec invalidation
const mutation = useMutation({
  mutationFn: updateResource,
  onSuccess: () => queryClient.invalidate({ queryKey: ['resource'] }),
})
```

### Zustand
```ts
// Store simple, pas de boilerplate
const useStore = create<StoreType>((set) => ({
  count: 0,
  increment: () => set((state) => ({ count: state.count + 1 })),
}))
```

### React Hook Form + Zod
```ts
const schema = z.object({ email: z.string().email() })
const form = useForm<z.infer<typeof schema>>({ resolver: zodResolver(schema) })
```

À enrichir après chaque projet.
