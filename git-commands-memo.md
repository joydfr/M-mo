# Mémo des Commandes Git

## Concepts fondamentaux
- **Repository (dépôt)** : Espace de stockage pour un projet et son historique
- **Working Directory** : Votre espace de travail local avec les fichiers actuels
- **Staging Area** : Zone intermédiaire où préparer les modifications avant commit
- **Commit** : Instantané (snapshot) de votre projet à un moment précis
- **Branch** : Ligne de développement parallèle au sein d'un projet
- **Remote** : Version distante du dépôt, généralement sur un serveur

## Commandes de base

### Configuration initiale
```bash
git config --global user.name "Votre Nom"
git config --global user.email "votre@email.com"
```

### Démarrer un projet
```bash
git init                          # Initialise un nouveau dépôt
git clone [url]                   # Clone un dépôt distant
```

### Voir l'état et l'historique
```bash
git status                        # Affiche l'état des fichiers
git log                           # Affiche l'historique des commits
git log --oneline                 # Historique compact, une ligne par commit
git diff                          # Affiche les modifications non stagées
git diff --staged                 # Affiche les modifications en staging
```

### Staging et commits
```bash
git add [fichier]                 # Ajoute un fichier au staging
git add .                         # Ajoute tous les fichiers modifiés au staging
git reset [fichier]               # Retire un fichier du staging
git commit -m "message"           # Crée un commit avec les fichiers en staging
git commit -am "message"          # Add + commit en une seule commande (fichiers déjà suivis)
```

### Branches
```bash
git branch                        # Liste les branches locales
git branch [nom-branche]          # Crée une nouvelle branche
git checkout [nom-branche]        # Bascule vers une branche existante
git checkout -b [nom-branche]     # Crée et bascule vers une nouvelle branche
git merge [nom-branche]           # Fusionne une branche dans la branche actuelle
git branch -d [nom-branche]       # Supprime une branche
```

### Rebase et modification de l'historique
```bash
git rebase -i HEAD~[nombre]       # Rebase interactif pour modifier les [nombre] derniers commits
git rebase -i [commit-hash]       # Rebase interactif depuis un commit spécifique
git push --force-with-lease       # Push après un rebase (modifie l'historique, à utiliser avec précaution)
```

### Travail avec des dépôts distants
```bash
git remote -v                     # Liste les dépôts distants
git remote add [nom] [url]        # Ajoute un dépôt distant
git pull [remote] [branche]       # Récupère et fusionne les changements distants
git push [remote] [branche]       # Envoie les commits locaux vers le dépôt distant
git fetch [remote]                # Récupère les changements sans fusionner
```

### Annuler des changements
```bash
git restore [fichier]             # Annule les modifications dans le working directory
git restore --staged [fichier]    # Retire un fichier du staging (équivalent à git reset)
git revert [commit]               # Crée un nouveau commit qui annule les changements du commit spécifié
git reset --hard [commit]         # Réinitialise tout au commit spécifié (DANGER: perte de travail)
```

### Sauvegarde temporaire
```bash
git stash                         # Met de côté les modifications actuelles
git stash list                    # Liste les stashes
git stash apply                   # Applique le dernier stash sans le supprimer
git stash pop                     # Applique le dernier stash et le supprime
```

### Tags (versions)
```bash
git tag                           # Liste les tags
git tag -a v1.0 -m "Version 1.0"  # Crée un tag annoté
git push --tags                   # Envoie les tags vers le dépôt distant
```

## Rebase interactif détaillé

Le rebase interactif (`git rebase -i`) est un outil puissant qui permet de modifier l'historique des commits. Il vous donne plusieurs options pour chaque commit :

```bash
# Commandes disponibles dans le rebase interactif :
# p, pick = utiliser le commit
# r, reword = utiliser le commit, mais modifier le message
# e, edit = utiliser le commit, mais s'arrêter pour le modifier
# s, squash = utiliser le commit, mais le fusionner avec le précédent
# f, fixup = comme "squash", mais en supprimant le message de commit
# d, drop = supprimer le commit
```

### Cas d'utilisation courants du rebase interactif :

1. **Modifier le message d'un commit** : Utilisez `reword`
2. **Combiner plusieurs commits** : Utilisez `squash` ou `fixup`
3. **Réordonner des commits** : Changez l'ordre des lignes
4. **Supprimer des commits** : Utilisez `drop` ou supprimez la ligne
5. **Diviser un commit** : Utilisez `edit`, puis `git reset HEAD^` pour défaire le commit tout en gardant les modifications, puis faites plusieurs nouveaux commits

### Après un rebase qui modifie l'historique déjà poussé :
```bash
git push --force-with-lease origin [branche]  # Option recommandée, plus sécurisée
# OU
git push --force origin [branche]             # À utiliser avec précaution, peut écraser le travail d'autres personnes
```


## Flux de travail typique

1. `git pull` - Récupérer les derniers changements
2. Modifier les fichiers...
3. `git status` - Vérifier quels fichiers ont été modifiés
4. `git add .` - Ajouter les modifications au staging
5. `git commit -m "Description des changements"` - Créer un commit
6. `git push` - Envoyer les changements au dépôt distant

## Bonnes pratiques

- Committer souvent, avec des messages clairs et descriptifs
- Tirer (pull) avant de pousser (push) pour éviter les conflits
- Utiliser des branches pour développer de nouvelles fonctionnalités
- Vérifier l'état (`git status`) et les différences (`git diff`) avant de committer
- Éviter de modifier l'historique public (commits déjà poussés)
- Quand vous utilisez `rebase -i` sur des commits déjà poussés, informez vos collaborateurs

## Termes Git "origin", "Local", "Upstream"
**Local**: C'est votre copie du dépôt sur votre ordinateur. C'est là où vous travaillez directement, où vous faites vos modifications et où vous créez vos commits.

**Origin** : C'est généralement le dépôt distant à partir duquel vous avez cloné votre dépôt local. Par défaut, quand vous clonez un dépôt, Git nomme automatiquement cette source distante "origin". Lorsque vous effectuez un "git push", vous envoyez par défaut vos modifications à "origin".

**Upstream**: Ce terme désigne le dépôt original à partir duquel vous avez fait un fork (une copie). C'est souvent utilisé dans le contexte des contributions open source. Par exemple :

- Vous faites un fork d'un projet sur GitHub (ce fork devient votre "origin")
- Vous clonez ce fork sur votre machine (votre dépôt "local")
- Le dépôt original dont vous avez fait le fork est alors appelé "upstream"

**En résumé** :

**Local** : Votre copie sur votre ordinateur
**Origin** : Le dépôt distant à partir duquel vous avez cloné (souvent votre fork sur GitHub)
**Upstream** : Le dépôt original dont vous avez fait un fork (quand vous contribuez à d'autres projets)
