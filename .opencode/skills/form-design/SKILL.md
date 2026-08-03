---
name: form-design
description: Patterns de conception de formulaires validés par l'expérience
---
## Structure standard d'un formulaire

```html
<form aria-label="..." novalidate>
  <fieldset>
    <legend>Titre de la section</legend>

    <label for="email">Email</label>
    <input id="email" type="email" required aria-describedby="email-error" />
    <span id="email-error" role="alert"></span>
  </fieldset>

  <button type="submit">Envoyer</button>
</form>
```

## Patterns

### Validation
- Côté client : validation on blur + on submit
- Côté serveur : toujours revalider
- Messages d'erreur : spécifiques (pas "Erreur" mais "L'email est invalide")
- Erreur en haut du form + focus sur premier champ en erreur

### Multi-step
- Barre de progression
- Boutons "Suivant" / "Précédent"
- Sauvegarde des données en cours
- Validation par étape avant de passer à la suivante

### Types de champs
| Type | Usage |
|------|-------|
| input text | Texte court |
| textarea | Texte long |
| email | Avec validation format |
| tel | Format international ? |
| select | < 5 options |
| radio | 2-5 options exclusives |
| checkbox | Options multiples |
| switch | Binaire (on/off) |
| date | Datepicker accessible |
| file | Upload avec preview |
| password | Avec show/hide toggle |

### États de soumission

| État | UX |
|------|-----|
| Idle | Formulaire prêt |
| Submitting | Bouton désactivé, spinner |
| Success | Message succès, reset ou confirmation |
| Error | Messages d'erreur, scroll to error |
| Network error | Toast "Erreur réseau, réessayer" |

À enrichir après chaque projet avec les patterns qui ont bien fonctionné.
