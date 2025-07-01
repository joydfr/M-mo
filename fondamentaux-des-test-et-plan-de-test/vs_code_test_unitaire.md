# Création d’une solution .NET avec projet principal et tests unitaires

## 📦 1. Créer le projet principal (déjà fait)

```bash
dotnet new sln -n NomFichier
```

```bash
dotnet new classlib -n App
```

_Crée une bibliothèque de classes `App` pour la logique métier._

---

## 🧪 2. Créer le projet de tests

```bash
dotnet new xunit -n App.Tests
```

_Crée un projet de tests unitaires avec xUnit._

---

## 🗂️ 3. Créer la solution

```bash
dotnet new sln -n GestionException
```

_Crée une solution pour regrouper les projets._

---

## ➕ 4. Ajouter les projets à la solution

```bash
dotnet sln add App/App.csproj
dotnet sln add App.Tests/App.Tests.csproj
```

---

## 🔗 5. Lier le projet de test au projet principal

```bash
dotnet add App.Tests/App.Tests.csproj reference App/App.csproj
```

---

## ▶️ 6. Lancer les tests

```bash
dotnet test
```

---

## 📝 7. Exemple de classe et de test

**App/Calculator.cs**

```csharp
namespace App
{
    public class Calculator
    {
        public int Add(int a, int b) => a + b;
    }
}
```

**App.Tests/CalculatorTests.cs**

```csharp
using Xunit;
using App;

namespace App.Tests
{
    public class CalculatorTests
    {
        [Fact]
        public void Add_With2And3_Returns5()
        {
            var calc = new Calculator();
            var result = calc.Add(2, 3);
            Assert.Equal(5, result);
        }
    }
}
```

---

> Besoin d’aide pour structurer tout ça automatiquement ou pour ajouter un test d’exception spécifique à “GestionException” ?  
> _Dis-le-moi !_
