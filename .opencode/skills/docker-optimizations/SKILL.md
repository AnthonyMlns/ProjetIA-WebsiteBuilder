---
name: docker-optimizations
description: Optimisations Docker — multi-stage, cache, image size, security
---
## Multi-stage build (recommandé)

```dockerfile
# Stage 1: Build
FROM node:22-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
RUN npm run build

# Stage 2: Production
FROM node:22-alpine AS runner
WORKDIR /app
RUN addgroup --system --gid 1001 nodejs && adduser --system --uid 1001 nextjs
COPY --from=builder /app/public ./public
COPY --from=builder --chown=nextjs:nodejs /app/.next/standalone ./
COPY --from=builder --chown=nextjs:nodejs /app/.next/static ./.next/static
USER nextjs
EXPOSE 3000
ENV NODE_ENV=production
CMD ["node", "server.js"]
```

## Dockerfile rules
- `.dockerignore` obligatoire : `node_modules`, `.git`, `.next`, `*.md`, `tests/`
- Toujours utiliser Alpine (ou distroless)
- Ne pas run en root → créer un user
- Utiliser `COPY --chown` pour les permissions
- Layer caching : copier `package*.json` avant le code
- Éviter `RUN npm install` → préférer `npm ci` (reproductible)

## Healthcheck
```dockerfile
HEALTHCHECK --interval=30s --timeout=3s --start-period=5s --retries=3 CMD wget --no-verbose --tries=1 --spider http://localhost:3000/api/health || exit 1
```

## Security
```dockerfile
# Scan
docker scout quick <image>
```

## Image size targets
- Node.js app < 200MB
- Static site (Nginx) < 50MB
- Go binary < 20MB

À enrichir après chaque projet.
