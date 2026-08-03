---
name: edge-cases-db
description: Base de cas limites récurrents à tester sur tous les projets
---
## Edge cases universels

### Input vide
- [ ] Champ texte vide soumis
- [ ] Liste vide affichée (empty state)
- [ ] Recherche sans résultat
- [ ] Upload sans fichier sélectionné
- [ ] Formulaire avec tous les champs vides

### Caractères spéciaux
- [ ] Caractères Unicode (émoji, accents, japonais, arabe)
- [ ] Script injection (`<script>`, `{{...}}`)
- [ ] SQL injection dans les champs texte
- [ ] Nombres négatifs
- [ ] Très longs textes (1000+ caractères)
- [ ] Espaces insécables, caractères invisibles

### États limites
- [ ] Double clic sur bouton submit
- [ ] Refresh pendant une sauvegarde
- [ ] Retour arrière navigateur après soumission
- [ ] Connexion perdue pendant requête
- [ ] Session expirée pendant utilisation
- [ ] Onglet laissé ouvert longtemps, session expirée

### Concurrent
- [ ] Deux utilisateurs modifient la même ressource
- [ ] Suppression d'une ressource pendant qu'elle est affichée ailleurs
- [ ] Upload de l'image pendant que le formulaire est soumis

### Temps
- [ ] Minuit / changement de jour
- [ ] Passage à l'heure d'été/hiver
- [ ] Dates dans le futur très lointain
- [ ] Timezone différentes (client vs serveur)

### Réseau
- [ ] Réponse API lente (> 10s)
- [ ] Timeout API
- [ ] Erreur 500, 502, 503
- [ ] Réseau coupé pendant upload
- [ ] Rate limit atteint (429)

À enrichir après chaque projet avec les bugs trouvés.
