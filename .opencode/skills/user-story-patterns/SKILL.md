---
name: user-story-patterns
description: Templates de user stories validés par l'expérience, organisés par domaine
---
## Templates génériques

### Authentification
```
En tant que <visiteur>, je veux <créer un compte / me connecter> afin d'<accéder aux fonctionnalités réservées>.
CR: [ ] Validation email obligatoire
CR: [ ] Mot de passe > 8 car., 1 maj, 1 chiffre
CR: [ ] Rate limiting sur login
```

### CRUD
```
En tant que <rôle>, je veux <lister/consulter/ajouter/modifier/supprimer> <une ressource> afin de <objectif métier>.
CR: [ ] Pagination sur la liste
CR: [ ] Confirmation avant suppression
CR: [ ] Validation des champs obligatoires
```

### Recherche
```
En tant que <visiteur>, je veux <rechercher> <des ressources> par <critères> afin de <trouver rapidement ce que je cherche>.
CR: [ ] Recherche full-text
CR: [ ] Filtres combinables
CR: [ ] Résultats avec surbrillance des termes
CR: [ ] État "aucun résultat" avec suggestion
```

## Patterns par domaine (à enrichir)

### E-commerce
- Consulter le catalogue
- Filtrer par catégorie / prix / note
- Ajouter au panier
- Passer commande
- Suivre commande
- Laisser un avis

### SaaS
- S'inscrire / se connecter
- Configurer son profil / workspace
- Créer / gérer des ressources
- Visualiser un dashboard
- Inviter des collaborateurs
- Exporter des données

### Blog / CMS
- Créer / éditer / publier un article
- Gérer les catégories et tags
- Modérer les commentaires
- Programmer une publication
- Gérer les médias

## Notes post-projet
- Stories trop vagues ou trop détaillées ?
- Stories qui ont causé des incompréhensions ?
- Stories manquantes identifiées en cours de dev ?
