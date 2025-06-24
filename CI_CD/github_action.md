# 🚀 Découverte de GitHub Actions

## 🧠 1. Comprendre ce qu’est GitHub Actions

**Définition :**  
GitHub Actions est une fonctionnalité intégrée à GitHub permettant d’automatiser des tâches en réponse à des événements dans ton dépôt.

> 💡 **En résumé :**  
> C’est un outil CI/CD intégré à GitHub pour lancer des scripts, tester du code, builder ton app, publier une image Docker ou déployer automatiquement ton projet.

---

### ⚙️ Comment ça marche ?

GitHub Actions fonctionne avec des _workflows_ définis dans des fichiers `.yml` dans le dossier :

```
.github/workflows/
```

Un workflow est déclenché par un événement (push, pull request, etc.), et contient des _jobs_, eux-mêmes composés de _steps_.

---

#### Exemple simple

```yaml
# .github/workflows/ci.yml
name: CI
on: [push]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - run: echo "Hello Jody 👋"
```

---

## 🛠️ 2. Identifier les cas d’usage

| Cas d’usage       | Description                                                        |
| ----------------- | ------------------------------------------------------------------ |
| 🧪 CI             | Lancer les tests automatiques à chaque push                        |
| 🧼 Lint / format  | Vérifier que le code suit les conventions (ex. ESLint, Prettier)   |
| 📦 Build          | Compiler ton app ou builder une image Docker                       |
| 🚀 Déploiement    | Déployer automatiquement sur Docker Hub, Vercel, Render, Azure...  |
| 🔁 Automatisation | Mettre à jour des dépendances, synchroniser des branches, releases |
| 📝 Documentation  | Générer automatiquement de la doc à partir du code                 |

---

## 🧭 3. Explorer l’interface GitHub Actions

**Où la trouver ?**

1. Clique sur l’onglet **“Actions”** en haut du dépôt.
2. Tu verras la liste des workflows, leur statut, et les logs détaillés.

**Ce que tu peux faire :**

- 📈 Voir quels workflows ont réussi ou échoué
- 🔍 Accéder aux logs complets de chaque étape
- ▶️ Relancer manuellement un workflow
- ✏️ Modifier le code YAML directement dans GitHub

---

## 💸 4. Comprendre la facturation et les limites

### 📦 Quota gratuit (au 24 juin 2025) :

| Type de compte      | Minutes gratuites/mois | Stockage d’artefacts |
| ------------------- | ---------------------- | -------------------- |
| Free (public/privé) | 2 000                  | 500 Mo               |
| GitHub Pro          | 3 000                  | 1 Go                 |
| Team / Enterprise   | jusqu’à 50 000         | selon abonnement     |

### 💻 Tarifs par OS :

| OS runner | Coût (au-delà du quota) |
| --------- | ----------------------- |
| Linux     | 0,008 $ / min           |
| macOS     | 0,08 $ / min            |
| Windows   | 0,016 $ / min           |

**Astuces pour économiser :**

- 🐧 Utiliser Linux (moins cher)
- 💤 Arrêter les workflows inutiles (`if`, `concurrency`)
- 🎯 Cibler les branches (`on: [push]` sur `main` uniquement)
