# 🧪 Mémo : Comparaison entre xUnit et NUnit

## 🧩 Présentation générale

| Caractéristique                | xUnit                                        | NUnit                                     |
| ------------------------------ | -------------------------------------------- | ----------------------------------------- |
| Créé par                       | Auteurs de NUnit & MSTest                    | Projet open source indépendant            |
| Type de framework              | Moderne, minimaliste                         | Classique, riche en fonctionnalités       |
| Attributs de test              | `[Fact]`, `[Theory]`, `[InlineData]`         | `[Test]`, `[TestCase]`                    |
| Setup/Teardown                 | Constructeur, `IDisposable`, `IClassFixture` | `[SetUp]`, `[TearDown]`, `[OneTimeSetUp]` |
| Tests paramétrés               | `[Theory]` + `[InlineData(...)]`             | `[TestCase(...)]`                         |
| Intégration avec `dotnet test` | Oui (via `xunit.runner.visualstudio`)        | Oui (via `NUnit3TestAdapter`)             |
| Style                          | Favorise DI et composition                   | Style proche de JUnit                     |
| Usage courant                  | Projets .NET 6+, ASP.NET Core                | Projets plus anciens ou complexes         |

---

## 🔁 Exemple comparatif de tests

### ✅ 1. Test simple sans paramètre

**xUnit**

```csharp
[Fact]
public void NouveauCompte_SansParametre_SoldeEstZero()
{
    var compte = new CompteBancaire();
    Assert.Equal(0, compte.Solde);
}
```

**NUnit**

```csharp
[Test]
public void NouveauCompte_SansParametre_SoldeEstZero()
{
    var compte = new CompteBancaire();
    Assert.AreEqual(0, compte.Solde);
}
```

---

### ✅ 2. Test avec paramètres

**xUnit**

```csharp
[Theory]
[InlineData(100, 50, 150)]
[InlineData(200, 0, 200)]
public void Deposer_AugmenteSolde(decimal initial, decimal depot, decimal attendu)
{
    var compte = new CompteBancaire(initial);
    compte.Deposer(depot);
    Assert.Equal(attendu, compte.Solde);
}
```

**NUnit**

```csharp
[TestCase(100, 50, 150)]
[TestCase(200, 0, 200)]
public void Deposer_AugmenteSolde(decimal initial, decimal depot, decimal attendu)
{
    var compte = new CompteBancaire(initial);
    compte.Deposer(depot);
    Assert.AreEqual(attendu, compte.Solde);
}
```

---

### ✅ 3. Test d’exception

**xUnit**

```csharp
[Fact]
public void Deposer_MontantNegatif_LanceException()
{
    var compte = new CompteBancaire(100);
    Assert.Throws<ArgumentException>(() => compte.Deposer(-50));
}
```

**NUnit**

```csharp
[Test]
public void Deposer_MontantNegatif_LanceException()
{
    var compte = new CompteBancaire(100);
    Assert.Throws<ArgumentException>(() => compte.Deposer(-50));
}
```

---

## 📌 Remarques pratiques

- En xUnit, pas besoin d’attribut `[TestFixture]` : les classes de tests sont détectées automatiquement.
- xUnit gère la configuration globale via les fixtures (`IClassFixture`, `CollectionFixture`) au lieu de `[OneTimeSetUp]`.
- NUnit est parfois plus expressif ou flexible pour certains types de tests (ex. paramétrage complexe).
