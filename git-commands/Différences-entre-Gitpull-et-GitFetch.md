## 🔄 Git Pull vs Git Fetch – Comparaison

| Commande    | Description                                        | Effet sur le code local        | Risques/Avantages                                    |
| ----------- | -------------------------------------------------- | ------------------------------ | ---------------------------------------------------- |
| `git fetch` | Récupère les branches distantes sans les fusionner | ❌ Ne modifie pas votre code   | ✅ Sûr – permet de voir les changements sans impact  |
| `git pull`  | Fait `fetch` + `merge` automatiquement             | ✅ Fusionne dans votre branche | ⚠️ Risque de conflits – agit directement sur le code |

## 🧠 Phrase mnémotechnique

> **"FETCH regarde, PULL ramène"**  
> _(Fetch = observer sans toucher, Pull = tirer vers soi)_

## ✅ Cas d’utilisation recommandés

| Situation                                     | Commande conseillée | Pourquoi                                                  |
| --------------------------------------------- | ------------------- | --------------------------------------------------------- |
| Vous voulez inspecter les changements d’abord | `git fetch`         | Plus de contrôle, aucun impact immédiat                   |
| Environnement de production                   | `git fetch`         | Évite les surprises, pas de risque de modifier en direct  |
| Mise à jour rapide sur un projet perso        | `git pull`          | Simple et rapide si vous êtes le seul à travailler dessus |
| Collaboration sans conflit récent             | `git pull`          | Pratique si tout est bien synchronisé                     |
