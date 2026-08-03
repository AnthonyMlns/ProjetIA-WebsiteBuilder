---
name: security-checklist
description: Checklist de sécurité à appliquer sur chaque projet
---
## Checklist obligatoire (tous projets)
- [ ] HTTPS (SSL auto via hébergeur ou Let's Encrypt)
- [ ] Headers de sécurité : CSP, X-Frame-Options, X-Content-Type-Options
- [ ] Rate limiting sur les endpoints sensibles (login, API)
- [ ] Validation et sanitization de toutes les entrées utilisateur
- [ ] ORM/query builder (pas de raw SQL concaténé)
- [ ] Mots de passe hashés (bcrypt / argon2)
- [ ] JWT signés, expiration courte, refresh tokens
- [ ] CORS configuré (pas `Access-Control-Allow-Origin: *`)
- [ ] Dépendances auditées (`npm audit`, `snyk`)
- [ ] Variables d'environnement, pas de secrets dans le code

## Checklist recommandé
- [ ] 2FA pour les comptes admin
- [ ] Logs de sécurité (tentatives échouées, actions sensibles)
- [ ] Session timeout automatique
- [ ] CSRF tokens pour les forms
- [ ] File upload : taille max, types autorisés, antivirus
- [ ] Email : SPF, DKIM, DMARC
- [ ] Backup automatisé et testé
- [ ] Rate limiting global (DDOS mitigation basique)
- [ ] Audit de sécurité avant mise en production

## Vulnérabilités OWASP Top 10
1. Broken Access Control
2. Cryptographic Failures
3. Injection (SQL, XSS, NoSQL)
4. Insecure Design
5. Security Misconfiguration
6. Vulnerable Components
7. Auth Failures
8. Data Integrity Failures
9. Logging & Monitoring
10. SSRF

À vérifier pour chaque endpoint et chaque page.
