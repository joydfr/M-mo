# 📝 Mémo Tests Unitaires - Guide Complet

## 🎯 Objectif Principal

**Un test unitaire teste la plus petite partie de code de manière isolée**

✅ **Une fonction** | ✅ **Une méthode** | ✅ **Une classe**

---

## 🧱 Les 3 Piliers Fondamentaux

### 1. 🎯 **ISOLATION COMPLÈTE**

- [ ] ✅ **Comprendre l'objectif** : Tester une unité indépendamment du reste
- Chaque test se concentre sur **UNE SEULE** unité de code
- Aucune dépendance aux autres parties de l'application

### 2. 🎭 **MOCKING DES DÉPENDANCES**

- [ ] ✅ **Savoir "mocker"** les dépendances externes pour garantir l'isolation
- 🗄️ **Base de données** → Mock/Stub
- 🌐 **API externes** → Mock/Stub
- 📁 **Fichiers** → Mock/Stub
- 🔧 **Services** → Mock/Stub

### 3. ✔️ **ASSERTIONS PERTINENTES**

- [ ] ✅ **Écrire des assertions** pour valider le comportement attendu
- Vérifier que le résultat correspond exactement à l'attendu
- Tester tous les cas possibles (nominal, limite, erreur)

---

## 🏗️ Structure AAA (Arrange-Act-Assert)

```javascript
test("Test de la fonction addition", () => {
  // 🔧 ARRANGE : Mise en place
  const a = 5;
  const b = 10;

  // ⚡ ACT : Exécution
  const resultat = addition(a, b);

  // ✅ ASSERT : Vérification
  expect(resultat).toBe(15);
});
```

---

## 🚀 Caractéristiques d'un Bon Test Unitaire

| 🎯 Critère           | 📋 Description                       |
| -------------------- | ------------------------------------ |
| 🤖 **Automatisé**    | Exécution sans intervention manuelle |
| ⚡ **Rapide**        | Exécution en millisecondes           |
| 🔄 **Reproductible** | Même résultat à chaque fois          |
| 🏝️ **Isolé**         | Indépendant des autres tests         |
| 📦 **Unitaire**      | Teste une seule unité                |
| 🔍 **Boîte blanche** | Connaissance interne du code         |

---

## 💡 Avantages Clés

### 🛡️ **Sécurité & Confiance**

- Détection précoce des bugs
- Prévention des régressions
- Confiance lors des refactorings

### 📚 **Documentation Vivante**

- Les tests servent de spécifications
- Exemples d'utilisation du code
- Facilite la maintenance

### 🔧 **Qualité du Code**

- Encourage la modularité
- Favorise la réutilisabilité
- Améliore la conception

---

## ⚠️ Défis & Solutions

### 🔗 **Dépendances Externes**

**Problème** : Tests lents et peu fiables  
**Solution** : Utiliser des mocks/stubs

### 📈 **Complexité Croissante**

**Problème** : Tests difficiles à maintenir  
**Solution** : Conception modulaire + DDD

### ⏱️ **Temps d'Exécution**

**Problème** : Tests trop lents  
**Solution** : Parallélisation + optimisation

---

## 🛠️ Outils Recommandés

### Frontend 🎨

- **Jest** pour JavaScript
- Tests sur utilitaires réutilisables
- Validation d'expressions régulières

### Backend ⚙️

- **PHPSpec** pour PHP
- Tests exhaustifs de la logique métier
- Architecture DDD

---

## 📊 Checklist de Validation

- [ ] ✅ **Comprendre l'objectif** : Tester la plus petite partie de code de manière isolée
- [ ] ✅ **Savoir mocker** : Simuler les dépendances externes (BDD, API, etc.)
- [ ] ✅ **Écrire des assertions** : Valider le comportement attendu

---

## 🎯 Règle d'Or

> **"Un test unitaire = Une unité + Isolation + Assertion"**

💡 **Conseil** : Commencez par les parties critiques de votre code et étendez progressivement la couverture !

---
