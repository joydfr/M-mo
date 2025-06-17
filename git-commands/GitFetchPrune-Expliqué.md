## 🧹 Git Fetch --prune – Nettoyage automatique

| Élément             | Description                                                                                 |
| ------------------- | ------------------------------------------------------------------------------------------- |
| `git fetch --prune` | Fait un `git fetch` **et** supprime les références locales de branches distantes supprimées |
| Effet principal     | Synchronise votre dépôt local avec l’état actuel du serveur distant                         |
| Utilité             | Évite les branches "fantômes" dans `git branch -r`                                          |
| Sécurité            | ✅ Ne supprime **pas** vos branches locales ou vos modifications non committées             |
| Mnémotechnique      | "**--prune fait le ménage de printemps dans vos branches**"                                 |

## ✅ Cas d’utilisation recommandés

| Situation                                                        | Pourquoi utiliser `--prune`                           |
| ---------------------------------------------------------------- | ----------------------------------------------------- |
| Plusieurs branches ont été supprimées récemment                  | Supprimer automatiquement leurs traces locales        |
| Vous nettoyez un projet ou préparez une release                  | Garde votre arborescence de branches claire et à jour |
| Vous voyez des branches distantes qui n’existent plus réellement | Synchronise avec l’état réel du dépôt distant         |
| Pratique courante pour garder un dépôt propre                    | À faire régulièrement (ex. une fois par semaine)      |

## ⚙️ Exemple avant/après

```bash
# Avant nettoyage :
$ git branch -r
  origin/feature-A
  origin/feature-B
  origin/feature-C   # Supprimée sur le serveur, toujours visible ici

# Après git fetch --prune :
$ git branch -r
  origin/feature-A
  origin/feature-B   # feature-C a été retirée de la liste
```

## 🔧 Rendre –prune automatique

```bash
git config --global fetch.prune true
```

Cela active automatiquement le nettoyage à chaque git fetch.

## 📝 À retenir

## ✅ Ce que fait `git fetch --prune` vs ❌ Ce qu’il ne fait pas

| ✅ Ce que ça fait                                        | ❌ Ce que ça ne fait pas                               |
| -------------------------------------------------------- | ------------------------------------------------------ |
| Supprime les références de branches distantes supprimées | Ne supprime pas vos branches locales                   |
| Synchronise avec l’état du dépôt distant                 | Ne modifie pas votre code ou vos modifications locales |
| Opération sûre et recommandée régulièrement              | N'entraîne **aucune perte de travail**                 |
