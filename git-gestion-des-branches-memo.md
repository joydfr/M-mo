# 📌 Mémo Git : Gestion des Branches

## 📂 Création et navigation entre branches

### ➕ **Créer une branche**
```sh
git branch nom-branche
```

### 🔄 **Changer de branche**
```sh
git switch nom-branche  # Nouvelle syntaxe
git checkout nom-branche  # Ancienne syntaxe
```

### 🚀 **Créer et basculer en même temps**
```sh
git switch -c nom-branche  # Nouvelle syntaxe
git checkout -b nom-branche  # Ancienne syntaxe
```

### 📜 **Lister les branches locales**
```sh
git branch
```

### 📜 **Lister les branches distantes**
```sh
git branch -r
```

---

## 🔀 Fusion et Rebase

### 🔗 **Fusionner une branche dans `main`**
```sh
git switch main
git merge nom-branche
```

### 🎭 **Rebase pour un historique linéaire**
```sh
git switch nom-branche
git rebase main
```

### 🚀 **Fusion Fast-Forward**
Un *fast-forward* se produit lorsque la branche cible n'a pas avancé depuis la création de la branche source. Git déplace simplement le pointeur de `main` vers la branche fusionnée, sans créer de commit de fusion.

```sh
git merge --ff-only nom-branche
```

Si vous voulez forcer un commit de fusion, même en fast-forward :
```sh
git merge --no-ff nom-branche
```

### 🔀 **Commit Normal vs Merge Commit**

#### ✅ **Commit Normal**
Un commit classique est un enregistrement des modifications effectuées dans le projet. Il contient :  
- Une référence au commit précédent  
- Un message décrivant les changements  
- Les modifications apportées aux fichiers  

Exemple :  
```sh
git commit -m "Ajout d'une nouvelle fonctionnalité"
```
Cela ajoute les changements à l’historique de la branche actuelle.

#### 🔀 **Merge Commit**
Un merge commit est créé lorsqu'on fusionne une branche dans une autre **sans fast-forward**. Il a **deux parents** au lieu d'un seul, ce qui signifie qu'il représente la jonction de deux branches distinctes.  

Exemple de fusion avec un commit de merge :  
```sh
git switch main
git merge --no-ff feature/nouvelle-fonction
```
Git crée alors un **commit spécial** qui indique la fusion de `feature/nouvelle-fonction` dans `main`. Ce commit contient les modifications de la branche fusionnée **sans réécrire l’historique**.

#### 🔹 **Différence principale**
- Un **commit normal** a un seul parent et enregistre des modifications linéaires.  
- Un **merge commit** a **deux parents** et sert à fusionner deux branches, conservant l’historique des divergences.  

Tu peux visualiser ces différences avec :  
```sh
git log --graph --oneline --decorate --all
```

### 🛑 **Annuler un rebase en cours**
```sh
git rebase --abort
```

---

## 🗑️ Suppression de branches

### ❌ **Supprimer une branche locale**
```sh
git branch -d nom-branche  # Suppression normale
git branch -D nom-branche  # Suppression forcée
```

### ❌ **Supprimer une branche distante**
```sh
git push origin --delete nom-branche
```

---

## 🌍 Travailler avec un dépôt distant

### 📤 **Envoyer une branche sur le dépôt distant**
```sh
git push origin nom-branche
```

### 📥 **Récupérer les branches distantes**
```sh
git fetch origin
```

### 🔄 **Créer une branche locale à partir d’une branche distante**
```sh
git switch --track origin/nom-branche
```

### 🔄 **Mettre à jour une branche locale avec les changements distants**
```sh
git pull origin nom-branche
```

---

## 🔹 Conventions des branches Git

### 📌 **Branches principales**
- **`main`** : Branche stable contenant la dernière version de production.
- **`develop`** : Branche de développement où les nouvelles fonctionnalités sont intégrées avant d’être fusionnées dans `main`.

### 🔀 **Branches secondaires**
- **`feature/nom-fonctionnalité`** : Branches utilisées pour développer de nouvelles fonctionnalités.
- **`fix/nom-bug`** : Branches dédiées aux corrections de bugs.
- **`hotfix/nom-correction`** : Corrections urgentes directement appliquées sur `main`.
- **`release/nom-version`** : Préparation d'une nouvelle version avant fusion dans `main`.

---

## 🚨 Bonnes pratiques
✅ Utiliser des noms de branches explicites (`feature/nouvelle-fonction`, `fix/correction-bug`)
✅ Toujours synchroniser (`git fetch`, `git pull`) avant de commencer une nouvelle tâche
✅ Faire des commits clairs et descriptifs
✅ Nettoyer les branches obsolètes (`git branch -d`)

---

📌 **Ce mémo couvre les bases de la gestion des branches avec Git.** Besoin d'un approfondissement ? Consulte la documentation officielle : https://git-scm.com/doc


