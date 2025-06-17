# 🧠 Mémo Git – L’essentiel

## 🧩 Concepts clés

| Terme            | Définition                              |
| ---------------- | --------------------------------------- |
| **Repository**   | Projet avec historique Git              |
| **Working Dir.** | Dossier local avec les fichiers actuels |
| **Staging Area** | Zone intermédiaire avant le commit      |
| **Commit**       | Snapshot de l’état des fichiers         |
| **Branch**       | Ligne parallèle de développement        |
| **Remote**       | Version distante (ex. GitHub)           |

---

## ⚙️ Configuration

```bash
git config --global user.name "Votre Nom"
git config --global user.email "votre@email.com"
```

⸻

## 🚀 Démarrer un projet

```bash
git init                      # Nouveau dépôt local
git clone [url]               # Cloner un dépôt distant
```

⸻

## 🔍 Voir l’état & l’historique

```bash
git status                    # État des fichiers
git log                       # Historique des commits
git log --oneline             # Historique condensé
git diff                      # Diff des changements non stagés
git diff --staged             # Diff des fichiers en staging
```

⸻

## ✅ Staging & Commit

```bash
git add [fichier]             # Ajouter au staging
git add .                     # Tout ajouter
git reset [fichier]           # Retirer du staging
git commit -m "message"       # Commit simple
git commit -am "message"      # add + commit (fichiers déjà suivis)
git commit --amend            # Modifier le dernier commit
```

### ⚠️ En cas d’amend sur commit déjà poussé : utiliser git push --force-with-lease

⸻

## 🌱 Branches

```bash
git branch                    # Lister les branches
git branch [nom]              # Créer une branche
git checkout [nom]            # Changer de branche
git checkout -b [nom]         # Créer + basculer
git merge [branche]           # Fusionner dans la branche actuelle
git branch -d [nom]           # Supprimer une branche
```

⸻

## 🧪 Rebase & Historique

```bash
git rebase -i HEAD~[n]        # Rebase interactif sur les n derniers commits
git rebase -i [commit-hash]   # Rebase depuis un commit spécifique
git push --force-with-lease   # Push sécurisé après rebase
```

⸻

## 🌐 Dépôts distants

```bash
git remote -v                 # Voir les remotes
git remote add [nom] [url]    # Ajouter un remote
git fetch [remote]            # Récupérer sans fusion
git pull [remote] [branche]   # Récupérer + fusionner
git push [remote] [branche]   # Envoyer au dépôt distant
```

⸻

## ♻️ Annuler des changements

```bash
git restore [fichier]             # Annuler modif locale
git restore --staged [fichier]    # Retirer du staging
git revert [commit]               # Commit inverse d’un commit
git reset --hard [commit]         # Réinitialisation totale (⚠️ destructif)
```

⸻

## 💾 Stash (sauvegarde temporaire)

```bash
git stash                    # Sauvegarder modifications
git stash list               # Voir les stashes
git stash apply              # Appliquer sans supprimer
git stash pop                # Appliquer et supprimer
```

⸻

## 🏷️ Tags

```bash
git tag                      # Lister les tags
git tag -a v1.0 -m "v1.0"    # Créer un tag annoté
git push --tags              # Envoyer les tags au remote
```

⸻

## 🧬 Rebase interactif – options

### Commandes dans git rebase -i :

- pick => garder tel quel
- reword => modifier message
- edit => modifier le commit
- squash => fusionner avec le précédent
- fixup => squash sans message
- drop => supprimer le commit

⸻

### 🚦 Workflow standard

- 1. git pull
- 2. Modifications des fichiers
- 3. git status
- 4. git add .
- 5. git commit -m "message"
- 6. git push

⸻

### ✅ Bonnes pratiques

- Committez souvent avec des messages clairs
- Faites pull avant un push
- Travaillez sur des branches
- Vérifiez avec git status et git diff avant commit
- Évitez de modifier l’historique déjà poussé
- Prévenez en cas de rebase partagé

⸻

## 🌍 Dépôts Git – Terminologie

## 🌍 Dépôts Git – Terminologie

| Terme       | Définition                                                             |
| ----------- | ---------------------------------------------------------------------- |
| Local       | Votre copie sur votre machine                                          |
| Origin      | Dépôt distant d’origine (ex. votre fork GitHub)                        |
| Upstream    | Projet source (utile si vous contribuez à un projet open source)       |
| Fork        | Copie personnelle d’un dépôt distant pour y apporter des modifications |
| Remote      | Dépôt distant auquel vous pouvez pousser ou tirer des modifications    |
| Branches    | Lignes de développement parallèles dans le dépôt                       |
| Tags        | Points fixes dans l’historique, souvent pour des versions stables      |
| Commit      | Instantané de l’état des fichiers à un moment donné                    |
| Stash       | Sauvegarde temporaire des modifications non commitées                  |
| Reflog      | Journal des actions récentes, utile pour retrouver des commits perdus  |
| Rebase      | Réécriture de l’historique pour intégrer des modifications             |
| Merge       | Fusion de deux branches pour combiner leurs modifications              |
| Cherry-pick | Appliquer un commit spécifique d’une branche à une autre               |
| Squash      | Fusionner plusieurs commits en un seul pour simplifier l’historique    |
| Bisect      | Outil pour trouver un commit défectueux en divisant l’historique       |
