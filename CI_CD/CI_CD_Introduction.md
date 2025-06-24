# 🚀 Introduction aux fondamentaux de la CI/CD

## 🧩 Qu’est-ce que la CI/CD ?

CI/CD signifie **Continuous Integration** (intégration continue) et **Continuous Deployment/Delivery** (déploiement/livraison continue).  
👉 Ce sont des pratiques DevOps qui automatisent le cycle de vie du code, de la validation au déploiement en production.

---

## 🔄 1. Comprendre les principes de l’Intégration Continue (CI)

### 🧠 Définition

L’intégration continue consiste à valider automatiquement chaque modification du code dès qu’elle est poussée dans le dépôt (GitHub, GitLab…).

### ⚙️ Que se passe-t-il en CI ?

1. 🧪 Exécution des tests automatiques (unitaires, linting…)
2. 🏗️ Build de l’application (compilation, transpilation, etc.)
3. 🚨 Détection précoce des erreurs

### ✅ Objectif

- Garder le code propre et stable à tout moment
- Collaborer efficacement même à plusieurs développeurs

### 🧰 Exemple

```yaml
# GitHub Actions - .github/workflows/ci.yml
name: CI
on: [push]
jobs:
  build-and-test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - run: npm install
      - run: npm run test
```

---

## 🚀 2. Comprendre les principes du Déploiement Continu (CD)

### 📦 Définition

Le déploiement continu consiste à automatiser la mise en production ou en préproduction après validation de la CI.

Il y a deux variantes :

- 📬 **Delivery** : déploiement déclenché manuellement (avec validation humaine)
- 🛰️ **Deployment** : déploiement totalement automatisé jusqu’à la prod

### ⚙️ Que se passe-t-il en CD ?

1. 📁 Génération d’un artefact (build final, image Docker…)
2. 🚀 Déploiement sur un serveur (cloud, VM, cluster…)
3. 🧪 Tests de non-régression, smoke tests, etc.

### ✅ Objectif

- Réduire les délais de mise en production
- Fiabilité + Rapidité + Répétabilité

---

## 🎯 3. Identifier les avantages de la CI/CD

| 🟢 Avantage                     | 📘 Détail                                            |
| ------------------------------- | ---------------------------------------------------- |
| 🔍 Détection rapide des erreurs | Grâce aux tests automatisés à chaque commit          |
| ⚡ Déploiement plus rapide      | Pas besoin de tout faire à la main                   |
| 🔁 Processus reproductibles     | Plus de “ça marche sur ma machine”                   |
| 🤝 Collaboration facilitée      | Tout le monde s’aligne sur une base propre et testée |
| 📦 Livraison continue de valeur | Moins de bugs, plus de feedback utilisateur          |

---

## 🛠️ 4. Découvrir les principaux outils du marché

### 🔧 Plateformes CI/CD

| Outil                  | Description                                                   |
| ---------------------- | ------------------------------------------------------------- |
| GitHub Actions         | Intégré à GitHub, très populaire pour les projets open source |
| GitLab CI/CD           | Très puissant, intégré à GitLab, avec pipeline YAML           |
| Jenkins                | Vétéran du secteur, très configurable, mais complexe          |
| CircleCI               | Rapide, orienté cloud                                         |
| Azure DevOps Pipelines | Solution Microsoft complète, idéale pour les projets .NET     |
| Travis CI              | Anciennement populaire, moins utilisé aujourd’hui             |

### 🌐 Cibles de déploiement

- 🔹 Docker Hub (images conteneurisées)
- 🔹 Heroku / Vercel / Netlify (déploiement simplifié d’apps web)
- 🔹 AWS / GCP / Azure (infrastructures cloud professionnelles)
- 🔹 Kubernetes (déploiement à l’échelle)
