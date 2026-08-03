---
name: auth-patterns
description: Patterns d'authentification et d'autorisation, comparaison et retours
---
## Solutions d'auth

| Solution | Pour | Contre | Idéal pour |
|----------|------|--------|------------|
| **NextAuth / Auth.js** | Next.js natif, nombreux providers | Documentation parfois confuse | Projets Next.js |
| **Clerk** | Excellente DX, prébuild UI | Payant, vendor lock-in | SaaS rapidité |
| **Lucia** | Léger, contrôle total | Setup manuel plus long | Projets custom |
| **Supabase Auth** | Gratuit, RBAC, Row Level Security | Dépendant Supabase | App avec Supabase |
| **Firebase Auth** | Gratuit, simple, providers | Vendor lock-in Google | Prototypes |
| **JWT custom** | Contrôle total, pas de dépendance | À faire soi-même, erreurs possibles | Petits projets |
| **OAuth / OIDC** | Standard, SSO | Complexe à configurer | Entreprise |

## Patterns d'autorisation

| Pattern | Description | Quand |
|---------|-------------|-------|
| **RBAC** (Role Based) | Rôles : admin, user, editor | La plupart des apps |
| **Permission flags** | `can_create_posts`, `can_delete_users` | Apps complexes |
| **ABAC** (Attribute Based) | Règles : "owner peut éditer sa ressource" | Multi-tenant |
| **Row Level Security** | Au niveau BDD (PostgreSQL RLS) | Supabase, données sensibles |

## Checklist sécurité auth
- [ ] Rate limiting sur login (5 tentatives/min)
- [ ] Bcrypt/Argon2 pour mots de passe (jamais SHA/MD5)
- [ ] Refresh tokens stockés sécurisé (httpOnly cookie)
- [ ] Session expire après X temps
- [ ] 2FA optionnel
- [ ] Logs des tentatives de connexion
- [ ] OAuth state parameter (CSRF)
- [ ] Pas d'info sensible dans les JWT

À enrichir après chaque projet.
