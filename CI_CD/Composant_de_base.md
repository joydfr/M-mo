# 🧱 Composants de base de GitHub Actions

Chaque automatisation GitHub Actions repose sur 5 briques fondamentales. Voici un guide progressif pour comprendre et expérimenter rapidement.

---

## 📋 1. Workflow – Le scénario global

**Définition :**  
Un _workflow_ est un fichier `.yml` qui décrit un processus d’automatisation (CI, build, déploiement…).

**Emplacement :**  
`.github/workflows/mon_workflow.yml`

**Contenu minimal :**

- nom du workflow
- un ou plusieurs jobs
- événement(s) déclencheur(s)

**Exemple :**

```yaml
name: 🚀 CI Frontend
on: [push, pull_request]
jobs:
  build: ...
```

---

## 🔧 2. Job – Un bloc de travail autonome

**Définition :**  
Un _job_ est une série d’instructions exécutées sur une même machine (_runner_), isolée des autres jobs.

**Exemple :**

```yaml
jobs:
  build-frontend:
    runs-on: ubuntu-latest
    steps: ...
  test-backend:
    runs-on: ubuntu-latest
    steps: ...
```

_Deux jobs exécutés en parallèle._

**Paramètres courants :**

- `runs-on`: système d’exécution (Ubuntu, Windows, macOS)
- `needs`: dépendance entre jobs

---

## 🪜 3. Step – Une action concrète

**Définition :**  
Une _step_ est une instruction exécutée dans l’ordre à l’intérieur d’un job.

**Types :**

- Commande shell (`run:`)
- Action réutilisable (`uses:`)

**Exemple :**

```yaml
steps:
    - name: Cloner le dépôt
        uses: actions/checkout@v3

    - name: Installer les dépendances
        run: npm install

    - name: Lancer les tests
        run: npm test
```

_Chaque step partage l’environnement du job._

---

## ⚙️ 4. Action – Un module réutilisable

**Définition :**  
Une _action_ est une tâche encapsulée, fournie par GitHub ou la communauté, réutilisable dans les steps.

| Action                   | Description                    |
| ------------------------ | ------------------------------ |
| actions/checkout@v3      | Clone le dépôt                 |
| actions/setup-node@v4    | Configure Node.js              |
| docker/build-push-action | Build et push une image Docker |
| github/codeql-action     | Analyse de sécurité CodeQL     |

**Exemple :**

```yaml
- name: Setup Node.js
    uses: actions/setup-node@v4
    with:
        node-version: 18
```

_Tu peux aussi créer tes propres actions._

---

## 🖥️ 5. Runner – L’environnement d’exécution

**Définition :**  
Un _runner_ est la machine sur laquelle GitHub exécute ton workflow.

| Type                   | Description                               |
| ---------------------- | ----------------------------------------- |
| 🧑‍💻 Runner hébergé      | Fourni par GitHub (Linux, Windows, macOS) |
| 🏠 Runner auto-hébergé | Sur ta propre machine ou serveur dédié    |

**Exemple :**

```yaml
runs-on: ubuntu-latest
```

_Exécute le job sur une VM Ubuntu._

---

## 🔁 Résumé visuel

```
Workflow
└── Job(s)
        └── Step(s)
                ├── run: commande shell
                └── uses: action réutilisable
```

_Tout s’exécute sur un runner._
