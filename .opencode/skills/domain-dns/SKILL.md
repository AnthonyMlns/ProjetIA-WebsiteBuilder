---
name: domain-dns
description: Configuration domaine, DNS, SSL, email
---
## Processus

```mermaid
1. Acheter domaine (Cloudflare, Namecheap, Gandi)
2. Configurer DNS
3. Configurer SSL (automatique avec Vercel/Netlify/Cloudflare)
4. Configurer email (MX, SPF, DKIM, DMARC)
```

## DNS records typiques

```
Type  Nom            Valeur
A     @              76.76.21.21          (Vercel)
CNAME www            myapp.vercel.app     (Vercel)
CNAME api            myapp.railway.app    (API)
MX    @              10 mx1.example.com   (Email)
TXT   @               v=spf1 include:_spf.example.com ~all
TXT   _dmarc          v=DMARC1; p=quarantine;
```

## Registrars

| Registrar | DNS gratuit | SSL | Pour |
|-----------|-------------|-----|------|
| Cloudflare | Oui, très rapide | Oui (Universal) | Meilleur DNS, protection DDOS |
| Namecheap | Oui | Oui (PositiveSSL) | Prix, interface |
| Gandi | Oui | Oui | Ethique, Privacy incluse |
| OVH | Oui | Oui | Européen |
| AWS Route53 | Non (payant) | Oui | AWS intégration |

## SSL
- Let's Encrypt (certbot) — gratuit, auto-renouvellement
- Cloudflare Universal SSL — gratuit, automatique
- Vercel / Netlify — SSL automatique
- Renouvellement automatique à configurer

## Email
- **Resend** — transactionnel, DNS facile
- **SendGrid** — fiable
- **Zoho / Google Workspace** — email pro
- SPF, DKIM, DMARC obligatoires pour deliverability

À enrichir après chaque projet.
