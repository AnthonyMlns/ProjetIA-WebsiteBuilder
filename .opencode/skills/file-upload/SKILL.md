---
name: file-upload
description: Patterns d'upload de fichiers — validation, stockage, optimisations
---
## Validation
```ts
const uploadSchema = z.object({
  file: z.instanceof(File).refine(f => f.size <= 5 * 1024 * 1024, 'Max 5MB').refine(f => ['image/jpeg', 'image/png', 'image/webp', 'application/pdf'].includes(f.type), 'Format non supporté'),
})
```

## Stratégies de stockage

| Solution | Pour | Contre |
|----------|------|--------|
| **Local filesystem** | Dev, protos | Pas scalable |
| **S3 / R2 / MinIO** | Production, scale | Setup plus complexe |
| **Supabase Storage** | Supabase projets | Vendor lock |
| **Uploadthing / Uploadcare** | Prêt à l'emploi | Payant, vendor lock |
| **Base64 en BDD** | Jamais! | BDD gonflée, lent |

## Pattern S3 (presigned URL)

```ts
// 1. Client demande une presigned URL
const { url, fields } = await api.getUploadUrl({ fileName, contentType })
// 2. Client upload direct vers S3
await fetch(url, { method: 'PUT', body: file, headers: { 'Content-Type': file.type } })
// 3. Client notifie le serveur
await api.confirmUpload({ key: fields.key })
```

## Optimisations
- Images : redimensionner côté client avant upload (canvas)
- Générer thumbnail (200x200) côté serveur
- CDN pour les fichiers statiques
- Cache-Control sur les fichiers

À enrichir après chaque projet.
