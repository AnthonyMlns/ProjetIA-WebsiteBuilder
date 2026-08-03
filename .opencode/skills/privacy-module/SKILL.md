# Skill: privacy-module

Module de politique de confidentialité / RGPD à intégrer sur les sites web après validation QA.

## Contenu du module

### 1. Page de politique de confidentialité

Template de page à créer dans le projet :

```tsx
// app/confidentialite/page.tsx
export default function PrivacyPage() {
  return (
    <article>
      <h1>Politique de confidentialité</h1>

      <h2>1. Collecte des données</h2>
      <p>
        Nous collectons les données suivantes via le formulaire newsletter :
        nom (optionnel), adresse email, consentement explicite.
      </p>

      <h2>2. Utilisation des données</h2>
      <ul>
        <li>Envoi de la newsletter (base légale : consentement)</li>
        <li>Amélioration du site (base légale : intérêt légitime)</li>
      </ul>

      <h2>3. Durée de conservation</h2>
      <p>
        Les données sont conservées jusqu'à désinscription ou 3 ans
        après le dernier contact.
      </p>

      <h2>4. Vos droits</h2>
      <ul>
        <li>Droit d'accès, de rectification, d'effacement</li>
        <li>Droit à la limitation du traitement</li>
        <li>Droit d'opposition et de portabilité</li>
        <li>Droit de retirer votre consentement à tout moment</li>
      </ul>

      <h2>5. Contact</h2>
      <p>Email de contact pour exercer vos droits : [email]</p>
    </article>
  )
}
```

### 2. Bannière de consentement cookies

Composant à ajouter dans le layout racine :

```tsx
// components/features/CookieBanner.tsx
'use client'

import { useState, useEffect } from 'react'

export default function CookieBanner() {
  const [visible, setVisible] = useState(false)

  useEffect(() => {
    const consent = localStorage.getItem('cookie-consent')
    if (!consent) setVisible(true)
  }, [])

  const acceptAll = () => {
    localStorage.setItem('cookie-consent', 'all')
    setVisible(false)
  }

  const refuse = () => {
    localStorage.setItem('cookie-consent', 'none')
    setVisible(false)
  }

  if (!visible) return null

  return (
    <div className="fixed bottom-0 left-0 right-0 z-50 bg-[#141414] border-t border-[#2a2a2a] p-4">
      <div className="max-w-4xl mx-auto flex flex-col sm:flex-row items-center gap-3">
        <p className="text-sm text-[#a0a0a0] flex-1">
          Ce site utilise des cookies pour améliorer votre expérience.
        </p>
        <div className="flex gap-2">
          <button onClick={refuse} className="px-4 py-2 text-sm border border-[#2a2a2a] rounded hover:bg-[#1a1a1a]">
            Refuser
          </button>
          <button onClick={acceptAll} className="px-4 py-2 text-sm bg-[#d4a843] text-[#0a0a0a] rounded hover:bg-[#e6b84d] font-semibold">
            Accepter
          </button>
        </div>
      </div>
    </div>
  )
}
```

### 3. Checkbox consentement RGPD

Dans tout formulaire collectant des données personnelles, ajouter :

```tsx
<label className="flex items-start gap-2 cursor-pointer">
  <input
    type="checkbox"
    required
    className="mt-0.5"
  />
  <span className="text-xs leading-relaxed">
    J&apos;accepte la{' '}
    <a href="/confidentialite" target="_blank" className="underline">
      politique de confidentialité
    </a>
    {' '}et autorise le traitement de mes données.
  </span>
</label>
```

### 4. Mentions légales

Page obligatoire avec :
- Identité de l'éditeur (nom, email, adresse)
- Directeur de publication
- Hébergeur (nom, adresse)
- Propriété intellectuelle

```tsx
// app/mentions-legales/page.tsx
```

### 5. Checklist RGPD

Avant déploiement final, vérifier :

- [ ] Page `/confidentialite` créée et accessible depuis le footer
- [ ] Page `/mentions-legales` créée et accessible depuis le footer
- [ ] Bannière cookies présente au premier visite
- [ ] Consentement explicite sur tous les formulaires
- [ ] Lien vers politique de confidentialité dans le formulaire newsletter
- [ ] localStorage pour le suivi du consentement
- [ ] Données personnelles : savoir où elles sont stockées et comment les exporter/supprimer
- [ ] Si utilisation d'analytics (Google Analytics, Plausible, etc.) : mention dans la politique

## Quand ajouter ce module

Ce module s'ajoute **après la validation QA** (étape 6 du pipeline), juste avant le déploiement.

## Ressources

- [CNIL — RGPD](https://www.cnil.fr/fr/reglement-europeen-protection-donnees)
- [Générateur de mentions légales](https://www.service-public.fr/)
