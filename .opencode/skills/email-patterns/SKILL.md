---
name: email-patterns
description: Patterns d'envoi d'emails — transactionnels, templates, providers
---
## Providers

| Provider | Gratuit | Pour | Limite gratuite |
|----------|---------|------|-----------------|
| **Resend** | Oui | React Email, excellent DX, API simple | 100/jour |
| **SendGrid** | Oui | Fiable, mature | 100/jour |
| **Postmark** | Non | Rapide, templates | - |
| **Mailgun** | Oui | Flexible | 5k/mois |
| **SES** | Oui | Pas cher (0.01$/1000) | 62k/mois (EC2) |
| **Brevo** | Oui | Newsletter + transactionnels | 300/jour |
| **Nodemailer** | Gratuit | Self-hosted | Infini (SMTP) |

## React Email (recommandé)
```tsx
// emails/welcome.tsx
export function WelcomeEmail({ name }: { name: string }) {
  return (
    <Html>
      <Head />
      <Preview>Bienvenue {name} !</Preview>
      <Body style={main}>
        <Heading>Bienvenue sur notre plateforme</Heading>
        <Text>Bonjour {name}, merci de votre inscription.</Text>
        <Button href="https://example.com">Commencer</Button>
      </Body>
    </Html>
  )
}
```

## Types d'emails
- Welcome / onboarding
- Reset password
- Confirmation (commande, inscription, email)
- Notification (alerte, rappel)
- Newsletter / campagne
- Facture / reçu

À enrichir après chaque projet.
