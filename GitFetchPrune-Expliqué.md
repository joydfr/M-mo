# Git Fetch --prune : Le nettoyeur de références

## Qu'est-ce que git fetch --prune ?
`git fetch --prune` (ou `git fetch -p`) est une commande qui combine deux actions :
- Télécharge les nouvelles données du dépôt distant (comme un fetch classique)
- Supprime les références locales vers les branches distantes qui n'existent plus sur le serveur distant

## Comment ça fonctionne ?

### Sans --prune
- Si une branche est supprimée sur le dépôt distant
- Votre dépôt local garde une référence vers cette branche
- Ces références "fantômes" restent dans votre liste de branches distantes
- Crée de la confusion et du désordre dans votre repository

### Avec --prune
- Synchronise parfaitement votre vue locale avec l'état du dépôt distant
- Supprime automatiquement les références vers les branches qui n'existent plus
- Garde votre repository propre et à jour
- Évite d'avoir des branches "fantômes" qui n'existent plus

## Phrase mnémotechnique
"--prune fait le ménage de printemps dans vos branches"

## Cas d'utilisation courants

### Quand utiliser git fetch --prune ?
- Après une période où plusieurs branches ont été fusionnées et supprimées
- Lors du nettoyage d'un projet
- Quand vous voyez des branches distantes qui ne devraient plus exister
- En routine hebdomadaire pour maintenir un repository propre

### Exemple concret
```bash
# Situation initiale
$ git branch -r
  origin/feature-A
  origin/feature-B
  origin/feature-C   # Cette branche a été supprimée sur le serveur distant

# Après git fetch --prune
$ git branch -r
  origin/feature-A
  origin/feature-B   # feature-C a disparu car elle n'existe plus sur le distant
```

## Configuration permanente
Si vous souhaitez que git fetch fasse toujours un prune automatiquement :
```bash
git config --global fetch.prune true
```

## Points importants à retenir
- Ne supprime que les références vers les branches distantes
- Ne touche pas à vos branches locales
- Ne supprime pas vos modifications non committées
- Est considéré comme une opération sûre
