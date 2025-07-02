# 🔍 Mémo - Différences entre Tests Unitaires et d'Intégration

## 🎯 Objectif Principal

**Différencier test d'intégration et test unitaire** : Comprendre les rôles distincts et complémentaires de ces deux types de tests essentiels.

---

## 🧩 Test Unitaire

### 📋 **Définition**

Le rôle des tests unitaires est de vérifier le fonctionnement de chaque fonction ou méthode de manière isolée pour s'assurer qu'elles produisent le résultat attendu, sans influence extérieure.

### 🎯 **Caractéristiques Clés**

- ✅ **Isolation totale** : Teste un composant individuel
- ✅ **Logique précise** : Cible une fonction/méthode spécifique
- ✅ **Indépendance** : Chaque test est autonome
- ✅ **Rapidité** : Exécution très rapide

### 💡 **Exemple Concret**

**Fonction** : `CalculerPrixCafe(decimal prixBase, List<string> supplements)`

```csharp
🧪 Tests unitaires (C#) :
[Test]
public void CalculerPrixCafe_SansSupplements_RetournePrixBase()
{
    // Arrange
    decimal prixBase = 2.0m;
    var supplements = new List<string>();

    // Act
    decimal resultat = CalculerPrixCafe(prixBase, supplements);

    // Assert
    Assert.AreEqual(2.0m, resultat);
}

[Test]
public void CalculerPrixCafe_AvecNoisette_AjoutePrix()
{
    // Arrange
    decimal prixBase = 2.0m;
    var supplements = new List<string> { "noisette" };

    // Act
    decimal resultat = CalculerPrixCafe(prixBase, supplements);

    // Assert
    Assert.AreEqual(2.5m, resultat);
}
```

---

## 🔗 Test d'Intégration

### 📋 **Définition**

Le rôle des tests d'intégration est de valider l'interaction entre plusieurs modules ou composants d'une application pour s'assurer qu'ils fonctionnent bien ensemble.

### 🎯 **Caractéristiques Clés**

- 🔄 **Interactions** : Teste la communication entre modules
- 🌐 **Coordination** : Vérifie la compatibilité des composants
- 📊 **État partagé** : Contrôle les variables globales
- 🎪 **Complexité** : Plus complexe que les tests unitaires

### 💡 **Exemple Concret**

**Fonction** : `CommanderBoissons(List<Boisson> boissons)` qui utilise :

- `CalculerPrix()` (méthode)
- `Stock` (propriété)

```csharp
🧪 Test d'intégration (C#) :
[Test]
public void CommanderBoissons_DeuxCafes_CalculePrixEtReduceStock()
{
    // Arrange
    var boissons = new List<Boisson>
    {
        new Boisson { Base = 2.0m },
        new Boisson { Base = 2.0m, Supplements = new[] { "noisette", "chantilly" } }
    };
    var stockInitial = 5;

    // Act
    var montant = CommanderBoissons(boissons);

    // Assert
    Assert.AreEqual(5.5m, montant);
    Assert.AreEqual(3, Stock); // Stock réduit de 2
}
```

---

## ⚖️ Comparaison Détaillée

| Critère           | 🧩 Test Unitaire | 🔗 Test d'Intégration     |
| ----------------- | ---------------- | ------------------------- |
| **🎯 Focus**      | Composant isolé  | Interaction entre modules |
| **🔬 Portée**     | Fonction/Méthode | Plusieurs composants      |
| **⚡ Vitesse**    | Très rapide      | Rapide à moyenne          |
| **🛠️ Complexité** | Simple           | Moyenne                   |
| **🎭 Isolation**  | Totale           | Partielle                 |
| **📊 Réalisme**   | Bas              | Moyen                     |
| **🐛 Détection**  | Erreurs logiques | Erreurs de coordination   |

---

## 🛠️ Outils Communs

### 🧪 **Frameworks de Tests**

- **Jest** (JavaScript)
- **Vitest** (JavaScript/TypeScript)
- **Mocha** (JavaScript)
- **JUnit** (Java)
- **PHPUnit** (PHP)

> 💡 **Note** : Les mêmes frameworks peuvent souvent gérer les deux types de tests !

---

## 🚀 Stratégie de Test Optimale en C#

### 🏗️ **Architecture Recommandée**

```csharp
🧩 Tests Unitaires (Base) - xUnit/NUnit
    ↓
🔗 Tests d'Intégration (Interactions) - TestServer/WebApplicationFactory
    ↓
🌐 Tests E2E (Parcours complets) - Selenium/Playwright
```

### 📈 **Structure de Projet C#**

```
MonProjet.Tests/
├── UnitTests/
│   ├── Services/
│   └── Models/
├── IntegrationTests/
│   ├── Controllers/
│   └── Repositories/
└── E2ETests/
    └── Scenarios/
```

### 📈 **Règle des Proportions**

- **70%** Tests unitaires (rapides, nombreux)
- **20%** Tests d'intégration (moyens, ciblés)
- **10%** Tests E2E (lents, critiques)

---

## ✅ Points Clés à Retenir

### 🧩 **Tests Unitaires**

- 🎯 **Quand ?** Pour valider la logique interne des méthodes
- 🚀 **Avantage** : Feedback rapide, debugging facile
- 🎪 **Limite** : Ne détecte pas les problèmes d'intégration
- 🔧 **En C#** : Utilisez `[Test]` avec NUnit ou `[Fact]` avec xUnit

### 🔗 **Tests d'Intégration**

- 🎯 **Quand ?** Pour valider les interactions entre composants
- 🚀 **Avantage** : Détecte les erreurs de coordination
- 🎪 **Limite** : Plus complexe à mettre en place
- 🔧 **En C#** : Utilisez `WebApplicationFactory` pour ASP.NET Core

---

## 🏆 Conclusion

### 🤝 **Complémentarité**

Les tests unitaires et d'intégration sont **complémentaires**, pas concurrents :

- **Tests Unitaires** → Solidité des fondations 🏗️
- **Tests d'Intégration** → Cohérence de l'assemblage 🔗

### 💡 **Recommandation**

Utilisez les **deux types** pour une couverture optimale :

1. Commencez par les tests unitaires (fondations)
2. Ajoutez les tests d'intégration (interactions critiques)
3. Complétez avec quelques tests E2E (parcours clés)

---

_📝 Source : [La Console - Différences entre Test Unitaire, d'Intégration et E2E](https://laconsole.dev/blog/differences-test-unitaire-integration-e2e)_
