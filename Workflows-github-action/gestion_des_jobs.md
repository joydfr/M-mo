# 🧱 Gestion des Jobs GitHub Actions

---

## 🖥️ 1. Définition des runners

### 🧠 Qu’est-ce qu’un runner ?

C’est la machine virtuelle (VM) qui exécute un job.

| Type                 | Description                        |
| -------------------- | ---------------------------------- |
| ubuntu-latest        | Linux (recommandé par défaut)      |
| windows-latest       | Pour tests/app Windows             |
| macos-latest         | Pour apps Apple                    |
| Custom (self-hosted) | Runner hébergé sur ta propre infra |

**Exemple :**

```yaml
jobs:
  build:
    runs-on: ubuntu-latest
```

✅ Par défaut, chaque job tourne sur une machine fraîche à chaque exécution.

---

## 🧪 2. Configuration de l’environnement

Tu peux ajouter des variables d’environnement, configurer des shells ou injecter des secrets.

**Exemple simple :**

```yaml
jobs:
    test:
        runs-on: ubuntu-latest
        env:
            NODE_ENV: test
            API_KEY: ${{ secrets.API_KEY }}
        steps:
            - run: echo "Env: $NODE_ENV"
```

**Bonnes pratiques :**

- Préfère les secrets pour les données sensibles.
- Utilise `env:` au niveau job pour éviter les répétitions.

---

## 🔗 3. Dépendances entre jobs (`needs`)

### 🧠 Par défaut :

Tous les jobs sont exécutés en parallèle.

### 🪜 Pour définir un ordre :

Utilise `needs:` pour indiquer qu’un job dépend d’un autre.

**Exemple :**

```yaml
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - run: npm run build

  test:
    runs-on: ubuntu-latest
    needs: build
    steps:
      - run: npm test

  deploy:
    runs-on: ubuntu-latest
    needs: [test]
    steps:
      - run: ./deploy.sh
```

➡️ Ordre : **build → test → deploy**

---

## ⚙️ 4. Conditions d’exécution (`if`)

Tu peux contrôler si un job ou une étape doit s’exécuter.

### 📌 Condition sur un job :

```yaml
jobs:
  deploy:
    runs-on: ubuntu-latest
    if: github.ref == 'refs/heads/main'
```

➡️ Le job `deploy` ne se lance que sur la branche `main`.

### 📌 Condition sur une étape :

```yaml
- name: Envoyer notification
    if: ${{ failure() }}
    run: echo "Le job a échoué"
```

➡️ Cette étape ne s’exécute que si le job a échoué.

---

## 🔄 Résumé visuel

```yaml
jobs:
  job1:
    runs-on: ubuntu-latest

  job2:
    needs: job1
    if: github.event_name == 'push'
    env:
      MY_VAR: value
```

---

## 🧠 Astuces supplémentaires

- ✅ `matrix:` permet d’exécuter plusieurs variantes d’un job (ex. différentes versions de Node).
- ✅ Le job `needs:` n’hérite pas automatiquement de l’environnement ou des artefacts — tu dois les transmettre manuellement si nécessaire.

---
