---
name: questionnaire-template
description: Modèle de questions à poser au client selon le type de projet (landing, SaaS, e-commerce, blog, app)
---
## Questions génériques
- Quel est l'objectif principal du site ?
- Qui est le public cible ?
- Quel est le budget et le délai ?
- Y a-t-il des contraintes techniques imposées ?

## Par type de projet
### Landing page
- Quel est l'argument principal (unique value proposition) ?
- Combien de sections ? (hero, features, témoignages, CTA, footer)
- Formulaire de capture ? (email, demo, newsletter)
- SEO : mots-clés principaux ?

### SaaS / Web app
- Quelles sont les fonctionnalités MVP vs v2/v3 ?
- Y a-t-il besoin d'authentification ? (email/password, SSO, OAuth)
- Quel modèle de pricing ? (freemium, subscription, one-time)
- Tableau de bord ? Quelles métriques ?
- Multi-tenant ? Espaces de travail ?

### E-commerce
- Catalogue : combien de produits ? catégories ? variations ?
- Paiement : Stripe, PayPal, virement ? Abonnement ?
- Gestion des stocks ? Inventaire temps réel ?
- Avis clients, notes, commentaires ?
- Expédition : zones, tarifs, tracking ?

### Blog / CMS
- Qui publie le contenu ? (auteurs, admins, invités)
- Catégories, tags, recherche ?
- Newsletter / RSS ?
- Commentaires ? modération ?
- Multilingue ?

### Vitrine / Portfolio
- Nombre de pages ?
- Galerie d'images / vidéos ?
- Formulaire de contact ?
- Intégration réseaux sociaux ?

## Client vague ("Fais un truc")
Quand le client ne donne pas de direction claire :
- Proposer une solution complete par defaut (stack, structure, design)
- Prendre des decisions arbitraires mais documentees (ADR)
- Demander validation bloc par bloc ("On garde X ou on change ?")
- Ne pas rester bloque a attendre des reponses

## À mettre à jour après chaque projet
- Questions qui ont révélé des informations cruciales
- Questions que le client n'a pas comprises et comment les reformuler
- Questions oubliées lors du projet
