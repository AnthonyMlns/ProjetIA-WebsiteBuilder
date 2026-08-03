---
name: form-patterns
description: Patterns de formulaires validés — React Hook Form, validation, UX
---
## Stack recommandé
- **React Hook Form** pour la gestion des formulaires
- **Zod** pour la validation (schémas partagés client/serveur)
- **shadcn/ui** ou composants custom pour l'UI

## Structure type

```ts
// 1. Schéma Zod
const contactSchema = z.object({
  name: z.string().min(2, 'Nom trop court'),
  email: z.string().email('Email invalide'),
  message: z.string().min(10).max(1000),
})
type ContactForm = z.infer<typeof contactSchema>

// 2. Hook form
const form = useForm<ContactForm>({
  resolver: zodResolver(contactSchema),
  defaultValues: { name: '', email: '', message: '' },
})

// 3. Submission
async function onSubmit(data: ContactForm) {
  try { await api.contact(data); form.reset(); toast.success('Message envoyé') }
  catch { toast.error('Erreur réseau') }
}
```

## UX patterns

### Validation timing
- `onBlur` : valider en quittant le champ
- `onChange` : corriger en temps réel (après première erreur)
- `onSubmit` : valider tout à la fin

### Messages d'erreur
- Spécifiques : "L'email n'est pas valide" (pas "Erreur")
- Liés au champ avec `aria-describedby`
- Apparaissent sous le champ, pas à côté

### Formulaires longs
- Multi-step avec progression
- Sauvegarder le brouillon (localStorage)
- Résumé avant soumission finale

À enrichir après chaque projet.
