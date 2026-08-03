---
name: middleware-chain
description: Middleware backend — ordre, configuration et patterns
---
## Ordre standard (Express / Hono)

```ts
app
  // 1. Security
  .use(cors({ origin: env.CORS_ORIGIN }))
  .use(helmet())

  // 2. Request parsing
  .use(rateLimiter)
  .use(bodyParser)

  // 3. Auth
  .use(session)
  .use(authMiddleware)

  // 4. Request ID + Logging
  .use(requestId)
  .use(requestLogger)

  // 5. Routes
  .route('/api/v1/posts', postsRouter)

  // 6. Error handler (last!)
  .onError(errorHandler)
```

## Middlewares prêts

### Rate limiting
```ts
const rateLimiter = rateLimit({ windowMs: 60_000, max: 100, standardHeaders: true, legacyHeaders: false })
```

### CORS
```ts
cors({ origin: ['https://example.com'], credentials: true, methods: ['GET', 'POST', 'PUT', 'PATCH', 'DELETE'] })
```

### Request ID
```ts
const requestId = (c, next) => { c.set('requestId', crypto.randomUUID()); return next() }
```

### Logger structuré
```ts
const requestLogger = (c, next) => { console.log(`${c.get('requestId')} ${c.req.method} ${c.req.url}`); return next() }
```

À enrichir après chaque projet.
