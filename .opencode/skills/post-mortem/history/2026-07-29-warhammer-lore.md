# Post-mortem : warhammer-lore.com

**Date :** 2026-07-29
**Projet :** warhammer-lore.com

---

## 1. Resume du projet

Blog sur le lore de Warhammer 40k avec 8 fiches factions, 3 articles, glossaire, section ludique et newsletter. Stack : Next.js 16 + Tailwind CSS v4. Deploiement prevu sur Vercel.

---

## 2. Ce qui a bien marche

- **Proposition proactive** : le client etant vague ("Fais un truc"), le fait de proposer une architecture complete a permis d'avancer rapidement.
- **Build zero erreur** : le site compile depuis la premiere tentative, toutes les pages SSG generees sans accroc.
- **Documentation exhaustive** : tous les documents (proposition, architecture, design tokens, wireframes, specs composants, ADR) ont ete crees et archives dans `decisions/`.
- **Separation claire** : le pipeline en 7 etapes a structure le travail, meme en l'absence d'agents specialises.
- **Skill privacy-module** : cree en reponse a un besoin identifie en cours de projet.

---

## 3. Ce qui n'a pas marche

- **Indisponibilite des agents specialises** : les sous-agents (analyst, architect, designer, dev-frontend) n'ont pas pu etre invoques (modele `opencode-go/deepseek-v4-flash` non trouve). Tout le travail a ete fait manuellement par l'orchestrator. Cela a ralenti le processus car chaque etape a du etre executee en sequentiel sans parallelisation.
- **Emojis dans le code** : j'ai utilise des emojis comme icones dans les composants (Header, Footer, navigation, titres de sections). Le client a trouve cela "AI SLOP" et a demande leur retrait. Correction faite, mais cela a ajoute une etape de refactoring non prevue.
- **Pas de QA ni de deploiement** : le pipeline s'est arrete avant les etapes QA et DevOps. Le site n'a pas ete teste en environnement de production ni deploye.

---

## 4. Surprises

- Le modele d'agent specifie dans le systeme (`opencode/deepseek-v4-flash`) n'etait pas disponible, mais le modele `deepseek-v4-flash-free` existait. Les tasks d'agents echouaient silencieusement.
- Le client a accepte la proposition initiale sans modification majeure, ce qui a valide mes choix par defaut (stack, structure, design).

---

## 5. Apprentissages et actions

### Pour les prochains projets

| Lecon | Action |
|-------|--------|
| Ne pas utiliser d'emojis dans le code des sites web (icones SVG ou texte seulement) | Ajouter cette regle dans le prompt systeme de l'orchestrator |
| Si les agents specialises ne sont pas disponibles, tout faire manuellement mais en etre conscient des le depart | Verifier la disponibilite des agents en debut de pipeline |
| Proposer une solution complete quand le client est vague est une bonne strategie | Continuer cette approche |
| Le skill privacy-module est necessaire sur tous les sites collectant des donnees | L'ajouter systematiquement apres la QA |

### Skills a mettre a jour

1. **privacy-module** — cree. A referencer dans la checklist de livrables.
2. **questionnaire-template** — ajouter une section "Questions pour les vagues" : quand le client dit "Fais un truc", proposer des choix par defaut.
3. **deliverable-checklist** — ajouter une ligne : verification qu'aucun emoji n'est utilise dans le code UI (icones en SVG/texte uniquement).
4. **post-mortem** — ce document sert d'exemple.

---

## 6. Statistiques du projet

| Metrique | Valeur |
|----------|--------|
| Pages generees | 25 |
| Fichiers sources crees | ~35 |
| Documents de decision | 8 |
| Skills crees | 1 (privacy-module) |
| Taux d'emojis initial dans le code | ~30 occurrences |
| Emojis apres nettoyage | 0 |
| Builds reussis | 2/2 |

---

## 7. Conclusion

Le projet warhammer-lore.com est fonctionnel, compile et pret pour la QA et le deploiement. Le pipeline a ete suivi dans l'ordre, meme si chaque etape a du etre executee manuellement. Le principal enseignement est de ne pas utiliser d'emojis dans le code UI et de verifier la disponibilite des agents en amont.
