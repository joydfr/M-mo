# ⏱️ Configuration des déclencheurs GitHub Actions

---

## ⚡ 1. Événements `push` et `pull_request`

### ✅ `push` – À chaque envoi sur une branche

Lance le workflow dès qu’un commit est poussé sur une branche :

```yaml
on:
  push:
    branches:
      - main
      - dev
```

➡️ Cela évite de lancer le workflow sur toutes les branches.

### ✅ `pull_request` – À chaque PR ouverte, synchronisée ou mise à jour

```yaml
on:
  pull_request:
    branches:
      - main
```

➡️ Idéal pour valider automatiquement les PR avant merge.

---

## 📆 2. Événements planifiés (`schedule`)

Lancer automatiquement un workflow à une heure précise, même sans push :

```yaml
on:
  schedule:
    - cron: "0 6 * * *"
```

Ce cron signifie : tous les jours à 6h00 UTC.

#### 🕰️ Syntaxe cron

```
# ┌──────── minute (0 - 59)
# │ ┌────── hour (0 - 23)
# │ │ ┌──── day of month (1 - 31)
# │ │ │ ┌── month (1 - 12)
# │ │ │ │ ┌─ day of week (0 - 6) (Sunday=0)
# │ │ │ │ │
# * * * * *
```

➡️ Utilise ce type de déclencheur pour :

- des tests de non-régression nocturnes
- un check d’intégrité
- une mise à jour automatique de dépendances

---

## 👆 3. Déclencheurs manuels (`workflow_dispatch`)

Permet à un·e développeur·se de lancer manuellement un workflow depuis l’interface GitHub.

```yaml
on:
  workflow_dispatch:
```

### ✍️ Avec paramètres

```yaml
on:
  workflow_dispatch:
    inputs:
      environment:
        description: "Environnement"
        required: true
        default: "staging"
```

➡️ Tu pourras choisir `staging` ou `production` depuis GitHub → Actions → Run workflow.

---

## 🎯 4. Filtres de branches et de tags

### 🔹 Filtres de branches

Cibler uniquement certaines branches pour éviter de tout déclencher :

```yaml
on:
  push:
    branches:
      - main
      - "release/*"
```

➡️ Ne s’exécute que sur `main` ou toute branche `release/x`.

### 🔹 Filtres de tags

Pratique pour les workflows de publication (Docker, Release GitHub, etc.) :

```yaml
on:
  push:
    tags:
      - "v*.*.*"
```

➡️ Ne s’exécute que lors d’un push sur un tag comme `v1.0.0`.

---

## 🧠 Résumé visuel

| Déclencheur         | Description           | Exemple                              |
| ------------------- | --------------------- | ------------------------------------ |
| `push`              | À chaque commit       | `on: push: branches: [main]`         |
| `pull_request`      | Lors d’une PR         | `on: pull_request: branches: [main]` |
| `schedule`          | Programmation horaire | `on: schedule: cron: '0 6 * * *'`    |
| `workflow_dispatch` | Manuel depuis l’UI    | `on: workflow_dispatch:`             |
| `tags`              | Push d’un tag git     | `on: push: tags: ['v*.*.*']`         |

---
