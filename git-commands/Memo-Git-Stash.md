# Mémo complet sur Git Stash

## Définition et utilité

`git stash` est une commande qui permet de mettre temporairement de côté des modifications non commitées pour pouvoir travailler sur autre chose, puis revenir à ces modifications plus tard.

## Cas d'utilisation courants

- Passage rapide à une tâche urgente
- Changement de branche avec des modifications en cours
- Expérimentation sans risquer de perdre son travail
- Résolution de conflits lors d'un pull
- Nettoyage temporaire de l'espace de travail

## Commandes de base

### Sauvegarder des modifications

```bash
# Stash basique
git stash

# Stash avec message descriptif (recommandé)
git stash save "Description de mes modifications"

# Stash interactif (sélection des modifications)
git stash -p
```

### Lister les stashs

```bash
git stash list
```

Exemple de résultat :
```
stash@{0}: WIP on feature-branch: abc1234 Dernier commit
stash@{1}: On master: Corrections de bug
```

### Appliquer un stash

```bash
# Appliquer le dernier stash sans le supprimer
git stash apply

# Appliquer un stash spécifique
git stash apply stash@{2}

# Appliquer et supprimer le dernier stash
git stash pop
```

### Supprimer un stash

```bash
# Supprimer un stash spécifique
git stash drop stash@{1}

# Supprimer tous les stashs
git stash clear
```

### Visualiser un stash

```bash
# Afficher un résumé des fichiers modifiés
git stash show stash@{0}

# Afficher les modifications détaillées
git stash show -p stash@{0}
```

## Fonctionnalités avancées

### Git stash branch

```bash
git stash branch nouvelle-branche [stash@{n}]
```

**Fonctionnement** :
1. Crée une nouvelle branche basée sur le commit où le stash a été créé
2. Applique le stash sur cette nouvelle branche
3. Supprime automatiquement le stash si l'application réussit

**Pourquoi la suppression automatique** :
- Évite les duplications de modifications
- Simplifie le workflow en combinant plusieurs opérations
- Les modifications sont déjà en sécurité dans la nouvelle branche

**Alternative pour conserver le stash** :
```bash
git checkout -b nouvelle-branche
git stash apply
```

### Stash partiel

```bash
git stash -p
```

Permet de sélectionner interactivement les modifications à stasher, hunks par hunks.

## Fonctionnement interne

Quand vous exécutez `git stash`, Git :
1. Crée un commit temporaire pour votre répertoire de travail
2. Crée un autre commit temporaire pour l'index (staged area)
3. Stocke ces commits dans la référence `refs/stash`
4. Réinitialise votre branche à l'état du dernier commit

## Exemples de workflows

### Passage rapide sur une autre branche

```bash
git stash
git checkout autre-branche
# travail sur l'autre branche
git checkout branche-initiale
git stash pop
```

### Résolution d'un conflit de merge

```bash
git stash
git pull
git stash pop
# résolution des conflits potentiels
```

### Créer une branche pour des modifications stashées

```bash
# Situation : vous travaillez sur master, mais devez corriger un bug urgent
git stash save "Fonctionnalité en cours"
# Correction du bug sur master
git commit -m "Correction bug urgent"

# Plus tard, pour reprendre la fonctionnalité sans conflits :
git stash branch feature-branch
# Vous êtes maintenant sur une nouvelle branche avec vos modifications
# Le stash a été supprimé automatiquement
```

## Résumé en une phrase

`git stash` permet de mettre temporairement de côté vos modifications non commitées pour travailler sur autre chose, puis les récupérer facilement quand vous êtes prêt à y revenir.
