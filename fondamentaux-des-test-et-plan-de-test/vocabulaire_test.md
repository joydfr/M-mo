# 📚 Vocabulaire Essentiel des Tests en C#

## 🎯 Introduction

Maîtriser le vocabulaire des tests est essentiel pour comprendre et communiquer efficacement dans le monde du testing en C# ! Voici tous les termes que vous devez connaître avec des exemples adaptés à l'écosystème .NET.

---

## 🧪 Les Concepts de Base

### 📝 **Test Case (Cas de Test)**

**💡 Définition :** Un scénario spécifique qui vérifie un comportement attendu

**🏗️ Structure d'un Test Case :**

```
📋 Test Case : "Connexion avec email valide"
├─ 📥 Input     : email="user@test.com", password="123456"
├─ 🎯 Action    : Cliquer sur "Se connecter"
├─ ✅ Expected  : Redirection vers tableau de bord
└─ 🔍 Assertion : Vérifier présence du message "Bienvenue"
```

**📝 Exemple concret :**

```csharp
// ✅ Un Test Case avec NUnit
[Test]
public void DevraitConnecterUtilisateurAvecIdentifiantsValides()
{
    // Given - Données d'entrée
    var email = "user@test.com";
    var password = "123456";

    // When - Action
    var result = _authService.Login(email, password);

    // Then - Vérification
    Assert.That(result.Success, Is.True);
    Assert.That(result.Message, Is.EqualTo("Connexion réussie"));
}

// ✅ Même test avec xUnit
[Fact]
public void DevraitConnecterUtilisateurAvecIdentifiantsValides_xUnit()
{
    // Given
    var email = "user@test.com";
    var password = "123456";

    // When
    var result = _authService.Login(email, password);

    // Then
    Assert.True(result.Success);
    Assert.Equal("Connexion réussie", result.Message);
}

// ✅ Même test avec MSTest
[TestMethod]
public void DevraitConnecterUtilisateurAvecIdentifiantsValides_MSTest()
{
    // Given
    var email = "user@test.com";
    var password = "123456";

    // When
    var result = _authService.Login(email, password);

    // Then
    Assert.IsTrue(result.Success);
    Assert.AreEqual("Connexion réussie", result.Message);
}
```

---

### 📦 **Test Suite (Suite de Tests)**

**💡 Définition :** Un **groupe de Test Cases** liés qui testent une fonctionnalité

**🎯 Organisation logique :** Tests regroupés par thème, module ou fonctionnalité

**📝 Exemple de structure :**

```
📦 Test Suite : "Authentification"
├─ 🧪 Test Case : Connexion réussie
├─ 🧪 Test Case : Mot de passe incorrect
├─ 🧪 Test Case : Email inexistant
├─ 🧪 Test Case : Champs vides
└─ 🧪 Test Case : Déconnexion
```

**💻 En code C# :**

```csharp
// 📦 Test Suite avec NUnit
[TestFixture]
public class AuthentificationTests
{
    private AuthService _authService;

    [SetUp]
    public void Setup()
    {
        _authService = new AuthService();
    }

    [Test]
    public void ConnexionReussie()
    {
        // Test implementation
    }

    [Test]
    public void MotDePasseIncorrect()
    {
        // Test implementation
    }

    [Test]
    public void EmailInexistant()
    {
        // Test implementation
    }

    [Test]
    public void ChampsVides()
    {
        // Test implementation
    }

    [Test]
    public void Deconnexion()
    {
        // Test implementation
    }
}

// 📦 Test Suite avec xUnit
public class AuthentificationTests_xUnit
{
    private readonly AuthService _authService;

    public AuthentificationTests_xUnit()
    {
        _authService = new AuthService();
    }

    [Fact]
    public void ConnexionReussie() { /* ... */ }

    [Fact]
    public void MotDePasseIncorrect() { /* ... */ }

    [Fact]
    public void EmailInexistant() { /* ... */ }
}
```

---

### 🏃 **Test Runner (Lanceur de Tests)**

**💡 Définition :** L'outil qui **exécute vos tests** et génère les rapports

**🔧 Fonctionnalités :**

- **▶️ Exécution** automatique des tests
- **📊 Rapports** détaillés (succès/échecs)
- **⚡ Parallélisation** pour la vitesse
- **🔍 Filtrage** par nom, catégorie, etc.

**🛠️ Exemples populaires en C# :**

```
dotnet test    🟦 → CLI .NET intégré
NUnit Runner   🟨 → NUnit framework
xUnit Runner   🟪 → xUnit framework
MSTest Runner  🟩 → Microsoft Test framework
Rider          🟧 → JetBrains IDE
Visual Studio  🟦 → Microsoft IDE
```

**📊 Exemple de sortie :**

```
🏃 Test Runner Results (dotnet test):
✅ AuthentificationTests
  ✅ ConnexionReussie (12ms)
  ❌ MotDePasseIncorrect (8ms)
  ✅ EmailInexistant (15ms)

📊 Résumé: 2 passed, 1 failed, 3 total
Test Run Successful.
```

**💻 Commandes CLI :**

```bash
# Exécuter tous les tests
dotnet test

# Exécuter avec filtrage
dotnet test --filter "Name~Authentification"

# Exécuter avec couverture
dotnet test --collect:"XPlat Code Coverage"
```

---

## ✅ Les Assertions

### 🎯 **Assertion**

**💡 Définition :** Une **vérification** qui confirme qu'un résultat correspond à l'attendu

**🔍 Types d'assertions courantes :**

#### **⚖️ Égalité**

```csharp
// NUnit
Assert.That(result, Is.EqualTo(42));
Assert.That(user.Name, Is.EqualTo("John"));

// xUnit
Assert.Equal(42, result);
Assert.Equal("John", user.Name);

// MSTest
Assert.AreEqual(42, result);
Assert.AreEqual("John", user.Name);
```

#### **✅ Booléens**

```csharp
// NUnit
Assert.That(isValid, Is.True);
Assert.That(isEmpty, Is.False);

// xUnit
Assert.True(isValid);
Assert.False(isEmpty);

// MSTest
Assert.IsTrue(isValid);
Assert.IsFalse(isEmpty);
```

#### **📏 Comparaisons**

```csharp
// NUnit
Assert.That(age, Is.GreaterThan(18));
Assert.That(score, Is.LessThanOrEqualTo(100));

// xUnit
Assert.True(age > 18);
Assert.True(score <= 100);

// MSTest
Assert.IsTrue(age > 18);
Assert.IsTrue(score <= 100);
```

#### **📦 Collections**

```csharp
// NUnit
Assert.That(users, Has.Count.EqualTo(3));
Assert.That(fruits, Contains.Item("pomme"));
Assert.That(numbers, Is.EqualTo(new[] { 1, 2, 3 }));

// xUnit
Assert.Equal(3, users.Count);
Assert.Contains("pomme", fruits);
Assert.Equal(new[] { 1, 2, 3 }, numbers);

// MSTest
Assert.AreEqual(3, users.Count);
CollectionAssert.Contains(fruits.ToList(), "pomme");
CollectionAssert.AreEqual(new[] { 1, 2, 3 }, numbers.ToArray());
```

#### **❌ Exceptions**

```csharp
// NUnit
Assert.Throws<DivideByZeroException>(() => Diviser(10, 0));
Assert.That(() => Login(""), Throws.ArgumentException.With.Message.Contains("Email requis"));

// xUnit
Assert.Throws<DivideByZeroException>(() => Diviser(10, 0));
var exception = Assert.Throws<ArgumentException>(() => Login(""));
Assert.Contains("Email requis", exception.Message);

// MSTest
Assert.ThrowsException<DivideByZeroException>(() => Diviser(10, 0));
var exception = Assert.ThrowsException<ArgumentException>(() => Login(""));
Assert.IsTrue(exception.Message.Contains("Email requis"));
```

---

## 🧰 Les Outils de Test

### 🏗️ **Fixture**

**💡 Définition :** **Données ou état initial** préparé pour les tests

**🎯 Objectif :** Avoir un environnement **prévisible et reproductible**

**📝 Types de Fixtures :**

#### **📊 Données de test**

```csharp
// 🏗️ Fixture - Données utilisateur
public class UserFixture
{
    public static User GetValidUser() => new User
    {
        Id = 1,
        Name = "John Doe",
        Email = "john@test.com",
        Role = "Admin"
    };

    public static List<User> GetUserList() => new List<User>
    {
        new User { Id = 1, Name = "John", Email = "john@test.com" },
        new User { Id = 2, Name = "Jane", Email = "jane@test.com" }
    };
}

[Test]
public void DevraitAfficherNomUtilisateur()
{
    // 📊 Utilisation fixture
    var user = UserFixture.GetValidUser();

    var result = _userService.DisplayUserName(user);

    Assert.That(result, Is.EqualTo("John Doe"));
}
```

#### **🗄️ Base de données**

```csharp
// 🏗️ Fixture - Configuration BDD pour tests
[TestFixture]
public class UserRepositoryTests
{
    private TestDbContext _context;

    [SetUp]
    public void Setup()
    {
        // 🏗️ Setup base de données en mémoire
        var options = new DbContextOptionsBuilder<TestDbContext>()
            .UseInMemoryDatabase(databaseName: Guid.NewGuid().ToString())
            .Options;

        _context = new TestDbContext(options);

        // 🏗️ Seed des données de test
        _context.Users.AddRange(UserFixture.GetUserList());
        _context.SaveChanges();
    }

    [TearDown]
    public void TearDown()
    {
        _context.Dispose();
    }
}
```

#### **📁 Fichiers**

```csharp
// 🏗️ Fixture - Fichier JSON de test
public class ApiResponseFixture
{
    public static string GetApiResponseJson()
    {
        return File.ReadAllText("TestData/api_response.json");
    }

    public static ApiResponse GetApiResponse()
    {
        var json = GetApiResponseJson();
        return JsonSerializer.Deserialize<ApiResponse>(json);
    }
}
```

---

### 🎭 **Mock (Simulacre)**

**💡 Définition :** **Faux objet** qui imite le comportement d'un vrai composant

**🎯 Utilisation :** Isoler le code testé des dépendances externes

**📝 Exemples pratiques avec Moq :**

#### **🌐 Mock d'API**

```csharp
// 🎭 Mock d'un service externe avec Moq
[Test]
public async Task DevraitRecupererUtilisateur()
{
    // Arrange
    var mockApiService = new Mock<IApiService>();
    mockApiService
        .Setup(x => x.GetUserAsync(1))
        .ReturnsAsync(new User { Id = 1, Name = "John" });

    var userController = new UserController(mockApiService.Object);

    // Act
    var result = await userController.GetUser(1);

    // Assert
    mockApiService.Verify(x => x.GetUserAsync(1), Times.Once);
    Assert.That(result.Name, Is.EqualTo("John"));
}
```

#### **💾 Mock de repository**

```csharp
// 🎭 Mock du repository
[Test]
public async Task DevraitSauvegarderUtilisateur()
{
    // Arrange
    var mockRepository = new Mock<IUserRepository>();
    var mockEmailService = new Mock<IEmailService>();

    mockRepository
        .Setup(x => x.SaveAsync(It.IsAny<User>()))
        .ReturnsAsync(true);

    var userService = new UserService(mockRepository.Object, mockEmailService.Object);

    // Act
    var user = new User { Name = "John", Email = "john@test.com" };
    var result = await userService.CreateUserAsync(user);

    // Assert
    mockRepository.Verify(x => x.SaveAsync(It.Is<User>(u => u.Name == "John")), Times.Once);
    Assert.That(result, Is.True);
}
```

#### **📧 Mock de services**

```csharp
// 🎭 Mock service email
[Test]
public async Task DevraitEnvoyerEmailBienvenue()
{
    // Arrange
    var mockEmailService = new Mock<IEmailService>();
    mockEmailService
        .Setup(x => x.SendWelcomeEmailAsync(It.IsAny<string>()))
        .ReturnsAsync(new EmailResult { Sent = true });

    var userService = new UserService(null, mockEmailService.Object);

    // Act
    await userService.SendWelcomeEmailAsync("john@test.com");

    // Assert
    mockEmailService.Verify(
        x => x.SendWelcomeEmailAsync("john@test.com"),
        Times.Once
    );
}
```

---

### 🔌 **Stub (Bouchon)**

**💡 Définition :** Version **simplifiée** d'un composant qui retourne des réponses prédéfinies

**🔄 Différence avec Mock :** Stub = réponses fixes, Mock = comportement intelligent

**📝 Exemples :**

#### **⏰ Stub de date**

```csharp
// 🔌 Stub pour date fixe
public class DateTimeStub : IDateTimeProvider
{
    public DateTime Now => new DateTime(2024, 1, 15);
    public DateTime UtcNow => new DateTime(2024, 1, 15);
}

[Test]
public void DevraitCreerRapportAvecDateActuelle()
{
    // Arrange
    var dateStub = new DateTimeStub();
    var reportService = new ReportService(dateStub);

    // Act
    var report = reportService.CreateReport();

    // Assert
    Assert.That(report.Date, Is.EqualTo(new DateTime(2024, 1, 15)));
}
```

#### **🎲 Stub de random**

```csharp
// 🔌 Stub pour valeur aléatoire fixe
public class RandomStub : IRandom
{
    public int Next(int min, int max) => 50;
    public double NextDouble() => 0.5;
}

[Test]
public void DevraitGenererNombrePrevisible()
{
    // Arrange
    var randomStub = new RandomStub();
    var gameService = new GameService(randomStub);

    // Act
    var number = gameService.GenerateRandomNumber();

    // Assert
    Assert.That(number, Is.EqualTo(50));
}
```

#### **🌐 Stub de configuration**

```csharp
// 🔌 Stub de configuration
public class ConfigurationStub : IConfiguration
{
    private readonly Dictionary<string, string> _config = new()
    {
        ["ApiUrl"] = "https://test-api.com",
        ["Timeout"] = "5000",
        ["Retries"] = "3"
    };

    public string this[string key]
    {
        get => _config.TryGetValue(key, out var value) ? value : null;
        set => _config[key] = value;
    }

    // Autres méthodes IConfiguration...
}
```

---

## 🎯 System Under Test (SUT)

### 🔍 **System Under Test (SUT)**

**💡 Définition :** Le **composant ou système** que vous êtes en train de tester

**🎯 Objectif :** Identifier clairement **ce qui est testé** vs **ce qui est mocké**

**📝 Exemples par niveau :**

#### **⚡ Test Unitaire - SUT = Méthode**

```csharp
// 🎯 SUT : La méthode CalculateTotal
public class OrderCalculator
{
    public decimal CalculateTotal(List<OrderItem> items, decimal discount)
    {
        var subtotal = items.Sum(item => item.Price * item.Quantity);
        return subtotal * (1 - discount);
    }
}

[Test]
public void CalculateTotal_DevraitAppliquerRemise()
{
    // Arrange
    var calculator = new OrderCalculator();
    var items = new List<OrderItem>
    {
        new OrderItem { Price = 100, Quantity = 1 },
        new OrderItem { Price = 50, Quantity = 1 }
    };

    // Act - 🎯 SUT appelé ici
    var total = calculator.CalculateTotal(items, 0.1m);

    // Assert
    Assert.That(total, Is.EqualTo(135m)); // 150 - 10%
}
```

#### **🧩 Test Intégration - SUT = Service**

```csharp
// 🎯 SUT : Le service UserService
public class UserService
{
    private readonly IUserRepository _repository;
    private readonly IEmailService _emailService;

    public UserService(IUserRepository repository, IEmailService emailService)
    {
        _repository = repository;
        _emailService = emailService;
    }

    public async Task<User> CreateUserAsync(User userData)
    {
        var user = await _repository.SaveAsync(userData);
        await _emailService.SendWelcomeEmailAsync(user.Email);
        return user;
    }
}

[Test]
public async Task UserService_DevraitCreerUtilisateurEtEnvoyerEmail()
{
    // Arrange - 🎭 Mocks des dépendances
    var mockRepo = new Mock<IUserRepository>();
    var mockEmail = new Mock<IEmailService>();

    var userData = new User { Name = "John", Email = "john@test.com" };
    var savedUser = new User { Id = 1, Name = "John", Email = "john@test.com" };

    mockRepo.Setup(x => x.SaveAsync(userData)).ReturnsAsync(savedUser);
    mockEmail.Setup(x => x.SendWelcomeEmailAsync(userData.Email)).Returns(Task.CompletedTask);

    // 🎯 SUT : UserService
    var userService = new UserService(mockRepo.Object, mockEmail.Object);

    // Act
    var result = await userService.CreateUserAsync(userData);

    // Assert
    Assert.That(result, Is.Not.Null);
    Assert.That(result.Id, Is.EqualTo(1));
    mockEmail.Verify(x => x.SendWelcomeEmailAsync("john@test.com"), Times.Once);
}
```

#### **🔍 Test E2E - SUT = Application complète**

```csharp
// 🎯 SUT : Toute l'application web avec WebApplicationFactory
[Test]
public async Task UtilisateurPeutCommanderProduit()
{
    // Arrange - 🎯 SUT : Application web complète
    using var factory = new WebApplicationFactory<Program>();
    var client = factory.CreateClient();

    // Act & Assert - 🎯 Test de l'interface utilisateur complète
    var response = await client.GetAsync("/products");
    response.EnsureSuccessStatusCode();

    var content = await response.Content.ReadAsStringAsync();
    Assert.That(content, Does.Contain("Produits disponibles"));
}
```

---

## 🏗️ Architecture Typique d'un Test

### 📋 **Anatomie Complète**

```csharp
// 📦 Test Suite
[TestFixture]
public class UserServiceTests
{
    // 🏗️ Fixtures
    private User _userFixture;

    // 🎭 Mocks
    private Mock<IUserRepository> _mockRepository;
    private Mock<IEmailService> _mockEmailService;

    // 🎯 SUT
    private UserService _userService;

    // ⚙️ Setup avant chaque test
    [SetUp]
    public void Setup()
    {
        // 🏗️ Initialisation des fixtures
        _userFixture = new User
        {
            Name = "John Doe",
            Email = "john@test.com"
        };

        // 🎭 Initialisation des mocks
        _mockRepository = new Mock<IUserRepository>();
        _mockEmailService = new Mock<IEmailService>();

        // 🎯 Initialisation du SUT
        _userService = new UserService(_mockRepository.Object, _mockEmailService.Object);
    }

    // 🧪 Test Case
    [Test]
    public async Task DevraitCreerUtilisateurAvecSucces()
    {
        // Arrange - 🔌 Configuration des stubs
        var savedUser = new User { Id = 1, Name = _userFixture.Name, Email = _userFixture.Email };

        _mockRepository
            .Setup(x => x.SaveAsync(It.IsAny<User>()))
            .ReturnsAsync(savedUser);

        _mockEmailService
            .Setup(x => x.SendWelcomeEmailAsync(It.IsAny<string>()))
            .Returns(Task.CompletedTask);

        // Act - 🎯 Appel du SUT
        var result = await _userService.CreateUserAsync(_userFixture);

        // Assert - ✅ Assertions
        Assert.That(result.Id, Is.EqualTo(1));
        Assert.That(result.Name, Is.EqualTo("John Doe"));

        _mockRepository.Verify(x => x.SaveAsync(_userFixture), Times.Once);
        _mockEmailService.Verify(x => x.SendWelcomeEmailAsync(_userFixture.Email), Times.Once);
    }

    // 🧹 Cleanup après chaque test
    [TearDown]
    public void TearDown()
    {
        _userService?.Dispose();
    }
}
```

---

## 📊 Tableau Récapitulatif

| **Terme**       | **🎯 Rôle**            | **📝 Exemple C#**            | **🔧 Utilisation**       |
| --------------- | ---------------------- | ---------------------------- | ------------------------ |
| **Test Case**   | 🧪 Scénario spécifique | `[Test] public void Login()` | Vérifier un comportement |
| **Test Suite**  | 📦 Groupe de tests     | `[TestFixture] public class` | Organiser les tests      |
| **Test Runner** | 🏃 Exécuteur           | `dotnet test`, NUnit, xUnit  | Lancer et reporter       |
| **Assertion**   | ✅ Vérification        | `Assert.That().Is.EqualTo()` | Valider le résultat      |
| **Fixture**     | 🏗️ Données test        | `UserFixture.GetValidUser()` | État initial prévisible  |
| **Mock**        | 🎭 Faux intelligent    | `Mock<IService>().Setup()`   | Simuler dépendances      |
| **Stub**        | 🔌 Réponse fixe        | `DateTimeStub : IDateTime`   | Valeurs prédéfinies      |
| **SUT**         | 🎯 Code testé          | `userService.CreateAsync()`  | Ce qu'on teste vraiment  |

---

## 🛠️ Frameworks et Outils C#

### **📚 Frameworks de Test**

```csharp
// NUnit - Le plus populaire
[TestFixture]
public class MyTests
{
    [Test]
    public void MonTest() { }
}

// xUnit - Moderne et extensible
public class MyTests
{
    [Fact]
    public void MonTest() { }
}

// MSTest - Microsoft officiel
[TestClass]
public class MyTests
{
    [TestMethod]
    public void MonTest() { }
}
```

### **🎭 Outils de Mocking**

```csharp
// Moq - Le plus utilisé
var mock = new Mock<IService>();
mock.Setup(x => x.Method()).Returns(result);

// NSubstitute - Syntaxe fluide
var substitute = Substitute.For<IService>();
substitute.Method().Returns(result);

// FakeItEasy - Syntaxe naturelle
var fake = A.Fake<IService>();
A.CallTo(() => fake.Method()).Returns(result);
```

### **🗄️ Bases de Données de Test**

```csharp
// Entity Framework In-Memory
services.AddDbContext<TestDbContext>(options =>
    options.UseInMemoryDatabase("TestDb"));

// SQLite In-Memory
services.AddDbContext<TestDbContext>(options =>
    options.UseSqlite("DataSource=:memory:"));
```

---

## 💡 Conseils Pratiques

### ✅ **Bonnes Pratiques**

- **📛 Noms explicites** : `DevraitRetournerErreurQuandEmailInvalide`
- **🎯 Un concept par test** : Ne testez qu'une chose à la fois
- **🏗️ Setup propre** : Utilisez `[SetUp]` et `[TearDown]`
- **🎭 Mocks précis** : Ne moquez que les dépendances externes
- **🔍 SUT identifiable** : Clair sur ce qui est testé

### ❌ **Erreurs à Éviter**

- **🙅 Tests trop complexes** : Si c'est dur à comprendre, c'est mal conçu
- **🎭 Trop de mocks** : Vous testez les mocks, pas votre code
- **🔧 Tests fragiles** : Qui cassent pour rien
- **📝 Assertions multiples** : Difficile à déboguer quand ça échoue

### **🚀 Commandes Utiles**

```bash
# Créer un projet de test
dotnet new nunit -n MonProjet.Tests

# Ajouter les packages
dotnet add package NUnit
dotnet add package NUnit3TestAdapter
dotnet add package Moq

# Exécuter les tests
dotnet test

# Avec couverture de code
dotnet test --collect:"XPlat Code Coverage"
```

---

## 🚀 Étapes pour Maîtriser le Vocabulaire

1. **📚 Commencer** par écrire des Test Cases simples avec NUnit/xUnit
2. **📦 Organiser** en Test Suites avec `[TestFixture]`
3. **🏃 Utiliser** `dotnet test` comme Test Runner
4. **✅ Maîtriser** les assertions de votre framework
5. **🏗️ Créer** des fixtures réutilisables
6. **🎭 Apprendre** Moq pour les mocks
7. **🎯 Identifier** clairement votre SUT

---

> 💡 **Astuce** : La maîtrise du vocabulaire facilite la communication en équipe et la lecture de la documentation .NET !# 📚 Vocabulaire Essentiel des Tests en C#

## 🎯 Introduction

Maîtriser le vocabulaire des tests est essentiel pour comprendre et communiquer efficacement dans le monde du testing en C# ! Voici tous les termes que vous devez connaître avec des exemples adaptés à l'écosystème .NET.

---

## 🧪 Les Concepts de Base

### 📝 **Test Case (Cas de Test)**

**💡 Définition :** Un scénario spécifique qui vérifie un comportement attendu

**🏗️ Structure d'un Test Case :**

```
📋 Test Case : "Connexion avec email valide"
├─ 📥 Input     : email="user@test.com", password="123456"
├─ 🎯 Action    : Cliquer sur "Se connecter"
├─ ✅ Expected  : Redirection vers tableau de bord
└─ 🔍 Assertion : Vérifier présence du message "Bienvenue"
```

**📝 Exemple concret :**

```csharp
// ✅ Un Test Case avec NUnit
[Test]
public void DevraitConnecterUtilisateurAvecIdentifiantsValides()
{
    // Given - Données d'entrée
    var email = "user@test.com";
    var password = "123456";

    // When - Action
    var result = _authService.Login(email, password);

    // Then - Vérification
    Assert.That(result.Success, Is.True);
    Assert.That(result.Message, Is.EqualTo("Connexion réussie"));
}

// ✅ Même test avec xUnit
[Fact]
public void DevraitConnecterUtilisateurAvecIdentifiantsValides_xUnit()
{
    // Given
    var email = "user@test.com";
    var password = "123456";

    // When
    var result = _authService.Login(email, password);

    // Then
    Assert.True(result.Success);
    Assert.Equal("Connexion réussie", result.Message);
}

// ✅ Même test avec MSTest
[TestMethod]
public void DevraitConnecterUtilisateurAvecIdentifiantsValides_MSTest()
{
    // Given
    var email = "user@test.com";
    var password = "123456";

    // When
    var result = _authService.Login(email, password);

    // Then
    Assert.IsTrue(result.Success);
    Assert.AreEqual("Connexion réussie", result.Message);
}
```

---

### 📦 **Test Suite (Suite de Tests)**

**💡 Définition :** Un **groupe de Test Cases** liés qui testent une fonctionnalité

**🎯 Organisation logique :** Tests regroupés par thème, module ou fonctionnalité

**📝 Exemple de structure :**

```
📦 Test Suite : "Authentification"
├─ 🧪 Test Case : Connexion réussie
├─ 🧪 Test Case : Mot de passe incorrect
├─ 🧪 Test Case : Email inexistant
├─ 🧪 Test Case : Champs vides
└─ 🧪 Test Case : Déconnexion
```

**💻 En code C# :**

```csharp
// 📦 Test Suite avec NUnit
[TestFixture]
public class AuthentificationTests
{
    private AuthService _authService;

    [SetUp]
    public void Setup()
    {
        _authService = new AuthService();
    }

    [Test]
    public void ConnexionReussie()
    {
        // Test implementation
    }

    [Test]
    public void MotDePasseIncorrect()
    {
        // Test implementation
    }

    [Test]
    public void EmailInexistant()
    {
        // Test implementation
    }

    [Test]
    public void ChampsVides()
    {
        // Test implementation
    }

    [Test]
    public void Deconnexion()
    {
        // Test implementation
    }
}

// 📦 Test Suite avec xUnit
public class AuthentificationTests_xUnit
{
    private readonly AuthService _authService;

    public AuthentificationTests_xUnit()
    {
        _authService = new AuthService();
    }

    [Fact]
    public void ConnexionReussie() { /* ... */ }

    [Fact]
    public void MotDePasseIncorrect() { /* ... */ }

    [Fact]
    public void EmailInexistant() { /* ... */ }
}
```

---

### 🏃 **Test Runner (Lanceur de Tests)**

**💡 Définition :** L'outil qui **exécute vos tests** et génère les rapports

**🔧 Fonctionnalités :**

- **▶️ Exécution** automatique des tests
- **📊 Rapports** détaillés (succès/échecs)
- **⚡ Parallélisation** pour la vitesse
- **🔍 Filtrage** par nom, catégorie, etc.

**🛠️ Exemples populaires en C# :**

```
dotnet test    🟦 → CLI .NET intégré
NUnit Runner   🟨 → NUnit framework
xUnit Runner   🟪 → xUnit framework
MSTest Runner  🟩 → Microsoft Test framework
Rider          🟧 → JetBrains IDE
Visual Studio  🟦 → Microsoft IDE
```

**📊 Exemple de sortie :**

```
🏃 Test Runner Results (dotnet test):
✅ AuthentificationTests
  ✅ ConnexionReussie (12ms)
  ❌ MotDePasseIncorrect (8ms)
  ✅ EmailInexistant (15ms)

📊 Résumé: 2 passed, 1 failed, 3 total
Test Run Successful.
```

**💻 Commandes CLI :**

```bash
# Exécuter tous les tests
dotnet test

# Exécuter avec filtrage
dotnet test --filter "Name~Authentification"

# Exécuter avec couverture
dotnet test --collect:"XPlat Code Coverage"
```

---

## ✅ Les Assertions

### 🎯 **Assertion**

**💡 Définition :** Une **vérification** qui confirme qu'un résultat correspond à l'attendu

**🔍 Types d'assertions courantes :**

#### **⚖️ Égalité**

```csharp
// NUnit
Assert.That(result, Is.EqualTo(42));
Assert.That(user.Name, Is.EqualTo("John"));

// xUnit
Assert.Equal(42, result);
Assert.Equal("John", user.Name);

// MSTest
Assert.AreEqual(42, result);
Assert.AreEqual("John", user.Name);
```

#### **✅ Booléens**

```csharp
// NUnit
Assert.That(isValid, Is.True);
Assert.That(isEmpty, Is.False);

// xUnit
Assert.True(isValid);
Assert.False(isEmpty);

// MSTest
Assert.IsTrue(isValid);
Assert.IsFalse(isEmpty);
```

#### **📏 Comparaisons**

```csharp
// NUnit
Assert.That(age, Is.GreaterThan(18));
Assert.That(score, Is.LessThanOrEqualTo(100));

// xUnit
Assert.True(age > 18);
Assert.True(score <= 100);

// MSTest
Assert.IsTrue(age > 18);
Assert.IsTrue(score <= 100);
```

#### **📦 Collections**

```csharp
// NUnit
Assert.That(users, Has.Count.EqualTo(3));
Assert.That(fruits, Contains.Item("pomme"));
Assert.That(numbers, Is.EqualTo(new[] { 1, 2, 3 }));

// xUnit
Assert.Equal(3, users.Count);
Assert.Contains("pomme", fruits);
Assert.Equal(new[] { 1, 2, 3 }, numbers);

// MSTest
Assert.AreEqual(3, users.Count);
CollectionAssert.Contains(fruits.ToList(), "pomme");
CollectionAssert.AreEqual(new[] { 1, 2, 3 }, numbers.ToArray());
```

#### **❌ Exceptions**

```csharp
// NUnit
Assert.Throws<DivideByZeroException>(() => Diviser(10, 0));
Assert.That(() => Login(""), Throws.ArgumentException.With.Message.Contains("Email requis"));

// xUnit
Assert.Throws<DivideByZeroException>(() => Diviser(10, 0));
var exception = Assert.Throws<ArgumentException>(() => Login(""));
Assert.Contains("Email requis", exception.Message);

// MSTest
Assert.ThrowsException<DivideByZeroException>(() => Diviser(10, 0));
var exception = Assert.ThrowsException<ArgumentException>(() => Login(""));
Assert.IsTrue(exception.Message.Contains("Email requis"));
```

---

## 🧰 Les Outils de Test

### 🏗️ **Fixture**

**💡 Définition :** **Données ou état initial** préparé pour les tests

**🎯 Objectif :** Avoir un environnement **prévisible et reproductible**

**📝 Types de Fixtures :**

#### **📊 Données de test**

```csharp
// 🏗️ Fixture - Données utilisateur
public class UserFixture
{
    public static User GetValidUser() => new User
    {
        Id = 1,
        Name = "John Doe",
        Email = "john@test.com",
        Role = "Admin"
    };

    public static List<User> GetUserList() => new List<User>
    {
        new User { Id = 1, Name = "John", Email = "john@test.com" },
        new User { Id = 2, Name = "Jane", Email = "jane@test.com" }
    };
}

[Test]
public void DevraitAfficherNomUtilisateur()
{
    // 📊 Utilisation fixture
    var user = UserFixture.GetValidUser();

    var result = _userService.DisplayUserName(user);

    Assert.That(result, Is.EqualTo("John Doe"));
}
```

#### **🗄️ Base de données**

```csharp
// 🏗️ Fixture - Configuration BDD pour tests
[TestFixture]
public class UserRepositoryTests
{
    private TestDbContext _context;

    [SetUp]
    public void Setup()
    {
        // 🏗️ Setup base de données en mémoire
        var options = new DbContextOptionsBuilder<TestDbContext>()
            .UseInMemoryDatabase(databaseName: Guid.NewGuid().ToString())
            .Options;

        _context = new TestDbContext(options);

        // 🏗️ Seed des données de test
        _context.Users.AddRange(UserFixture.GetUserList());
        _context.SaveChanges();
    }

    [TearDown]
    public void TearDown()
    {
        _context.Dispose();
    }
}
```

#### **📁 Fichiers**

```csharp
// 🏗️ Fixture - Fichier JSON de test
public class ApiResponseFixture
{
    public static string GetApiResponseJson()
    {
        return File.ReadAllText("TestData/api_response.json");
    }

    public static ApiResponse GetApiResponse()
    {
        var json = GetApiResponseJson();
        return JsonSerializer.Deserialize<ApiResponse>(json);
    }
}
```

---

### 🎭 **Mock (Simulacre)**

**💡 Définition :** **Faux objet** qui imite le comportement d'un vrai composant

**🎯 Utilisation :** Isoler le code testé des dépendances externes

**📝 Exemples pratiques avec Moq :**

#### **🌐 Mock d'API**

```csharp
// 🎭 Mock d'un service externe avec Moq
[Test]
public async Task DevraitRecupererUtilisateur()
{
    // Arrange
    var mockApiService = new Mock<IApiService>();
    mockApiService
        .Setup(x => x.GetUserAsync(1))
        .ReturnsAsync(new User { Id = 1, Name = "John" });

    var userController = new UserController(mockApiService.Object);

    // Act
    var result = await userController.GetUser(1);

    // Assert
    mockApiService.Verify(x => x.GetUserAsync(1), Times.Once);
    Assert.That(result.Name, Is.EqualTo("John"));
}
```

#### **💾 Mock de repository**

```csharp
// 🎭 Mock du repository
[Test]
public async Task DevraitSauvegarderUtilisateur()
{
    // Arrange
    var mockRepository = new Mock<IUserRepository>();
    var mockEmailService = new Mock<IEmailService>();

    mockRepository
        .Setup(x => x.SaveAsync(It.IsAny<User>()))
        .ReturnsAsync(true);

    var userService = new UserService(mockRepository.Object, mockEmailService.Object);

    // Act
    var user = new User { Name = "John", Email = "john@test.com" };
    var result = await userService.CreateUserAsync(user);

    // Assert
    mockRepository.Verify(x => x.SaveAsync(It.Is<User>(u => u.Name == "John")), Times.Once);
    Assert.That(result, Is.True);
}
```

#### **📧 Mock de services**

```csharp
// 🎭 Mock service email
[Test]
public async Task DevraitEnvoyerEmailBienvenue()
{
    // Arrange
    var mockEmailService = new Mock<IEmailService>();
    mockEmailService
        .Setup(x => x.SendWelcomeEmailAsync(It.IsAny<string>()))
        .ReturnsAsync(new EmailResult { Sent = true });

    var userService = new UserService(null, mockEmailService.Object);

    // Act
    await userService.SendWelcomeEmailAsync("john@test.com");

    // Assert
    mockEmailService.Verify(
        x => x.SendWelcomeEmailAsync("john@test.com"),
        Times.Once
    );
}
```

---

### 🔌 **Stub (Bouchon)**

**💡 Définition :** Version **simplifiée** d'un composant qui retourne des réponses prédéfinies

**🔄 Différence avec Mock :** Stub = réponses fixes, Mock = comportement intelligent

**📝 Exemples :**

#### **⏰ Stub de date**

```csharp
// 🔌 Stub pour date fixe
public class DateTimeStub : IDateTimeProvider
{
    public DateTime Now => new DateTime(2024, 1, 15);
    public DateTime UtcNow => new DateTime(2024, 1, 15);
}

[Test]
public void DevraitCreerRapportAvecDateActuelle()
{
    // Arrange
    var dateStub = new DateTimeStub();
    var reportService = new ReportService(dateStub);

    // Act
    var report = reportService.CreateReport();

    // Assert
    Assert.That(report.Date, Is.EqualTo(new DateTime(2024, 1, 15)));
}
```

#### **🎲 Stub de random**

```csharp
// 🔌 Stub pour valeur aléatoire fixe
public class RandomStub : IRandom
{
    public int Next(int min, int max) => 50;
    public double NextDouble() => 0.5;
}

[Test]
public void DevraitGenererNombrePrevisible()
{
    // Arrange
    var randomStub = new RandomStub();
    var gameService = new GameService(randomStub);

    // Act
    var number = gameService.GenerateRandomNumber();

    // Assert
    Assert.That(number, Is.EqualTo(50));
}
```

#### **🌐 Stub de configuration**

```csharp
// 🔌 Stub de configuration
public class ConfigurationStub : IConfiguration
{
    private readonly Dictionary<string, string> _config = new()
    {
        ["ApiUrl"] = "https://test-api.com",
        ["Timeout"] = "5000",
        ["Retries"] = "3"
    };

    public string this[string key]
    {
        get => _config.TryGetValue(key, out var value) ? value : null;
        set => _config[key] = value;
    }

    // Autres méthodes IConfiguration...
}
```

---

## 🎯 System Under Test (SUT)

### 🔍 **System Under Test (SUT)**

**💡 Définition :** Le **composant ou système** que vous êtes en train de tester

**🎯 Objectif :** Identifier clairement **ce qui est testé** vs **ce qui est mocké**

**📝 Exemples par niveau :**

#### **⚡ Test Unitaire - SUT = Méthode**

```csharp
// 🎯 SUT : La méthode CalculateTotal
public class OrderCalculator
{
    public decimal CalculateTotal(List<OrderItem> items, decimal discount)
    {
        var subtotal = items.Sum(item => item.Price * item.Quantity);
        return subtotal * (1 - discount);
    }
}

[Test]
public void CalculateTotal_DevraitAppliquerRemise()
{
    // Arrange
    var calculator = new OrderCalculator();
    var items = new List<OrderItem>
    {
        new OrderItem { Price = 100, Quantity = 1 },
        new OrderItem { Price = 50, Quantity = 1 }
    };

    // Act - 🎯 SUT appelé ici
    var total = calculator.CalculateTotal(items, 0.1m);

    // Assert
    Assert.That(total, Is.EqualTo(135m)); // 150 - 10%
}
```

#### **🧩 Test Intégration - SUT = Service**

```csharp
// 🎯 SUT : Le service UserService
public class UserService
{
    private readonly IUserRepository _repository;
    private readonly IEmailService _emailService;

    public UserService(IUserRepository repository, IEmailService emailService)
    {
        _repository = repository;
        _emailService = emailService;
    }

    public async Task<User> CreateUserAsync(User userData)
    {
        var user = await _repository.SaveAsync(userData);
        await _emailService.SendWelcomeEmailAsync(user.Email);
        return user;
    }
}

[Test]
public async Task UserService_DevraitCreerUtilisateurEtEnvoyerEmail()
{
    // Arrange - 🎭 Mocks des dépendances
    var mockRepo = new Mock<IUserRepository>();
    var mockEmail = new Mock<IEmailService>();

    var userData = new User { Name = "John", Email = "john@test.com" };
    var savedUser = new User { Id = 1, Name = "John", Email = "john@test.com" };

    mockRepo.Setup(x => x.SaveAsync(userData)).ReturnsAsync(savedUser);
    mockEmail.Setup(x => x.SendWelcomeEmailAsync(userData.Email)).Returns(Task.CompletedTask);

    // 🎯 SUT : UserService
    var userService = new UserService(mockRepo.Object, mockEmail.Object);

    // Act
    var result = await userService.CreateUserAsync(userData);

    // Assert
    Assert.That(result, Is.Not.Null);
    Assert.That(result.Id, Is.EqualTo(1));
    mockEmail.Verify(x => x.SendWelcomeEmailAsync("john@test.com"), Times.Once);
}
```

#### **🔍 Test E2E - SUT = Application complète**

```csharp
// 🎯 SUT : Toute l'application web avec WebApplicationFactory
[Test]
public async Task UtilisateurPeutCommanderProduit()
{
    // Arrange - 🎯 SUT : Application web complète
    using var factory = new WebApplicationFactory<Program>();
    var client = factory.CreateClient();

    // Act & Assert - 🎯 Test de l'interface utilisateur complète
    var response = await client.GetAsync("/products");
    response.EnsureSuccessStatusCode();

    var content = await response.Content.ReadAsStringAsync();
    Assert.That(content, Does.Contain("Produits disponibles"));
}
```

---

## 🏗️ Architecture Typique d'un Test

### 📋 **Anatomie Complète**

```csharp
// 📦 Test Suite
[TestFixture]
public class UserServiceTests
{
    // 🏗️ Fixtures
    private User _userFixture;

    // 🎭 Mocks
    private Mock<IUserRepository> _mockRepository;
    private Mock<IEmailService> _mockEmailService;

    // 🎯 SUT
    private UserService _userService;

    // ⚙️ Setup avant chaque test
    [SetUp]
    public void Setup()
    {
        // 🏗️ Initialisation des fixtures
        _userFixture = new User
        {
            Name = "John Doe",
            Email = "john@test.com"
        };

        // 🎭 Initialisation des mocks
        _mockRepository = new Mock<IUserRepository>();
        _mockEmailService = new Mock<IEmailService>();

        // 🎯 Initialisation du SUT
        _userService = new UserService(_mockRepository.Object, _mockEmailService.Object);
    }

    // 🧪 Test Case
    [Test]
    public async Task DevraitCreerUtilisateurAvecSucces()
    {
        // Arrange - 🔌 Configuration des stubs
        var savedUser = new User { Id = 1, Name = _userFixture.Name, Email = _userFixture.Email };

        _mockRepository
            .Setup(x => x.SaveAsync(It.IsAny<User>()))
            .ReturnsAsync(savedUser);

        _mockEmailService
            .Setup(x => x.SendWelcomeEmailAsync(It.IsAny<string>()))
            .Returns(Task.CompletedTask);

        // Act - 🎯 Appel du SUT
        var result = await _userService.CreateUserAsync(_userFixture);

        // Assert - ✅ Assertions
        Assert.That(result.Id, Is.EqualTo(1));
        Assert.That(result.Name, Is.EqualTo("John Doe"));

        _mockRepository.Verify(x => x.SaveAsync(_userFixture), Times.Once);
        _mockEmailService.Verify(x => x.SendWelcomeEmailAsync(_userFixture.Email), Times.Once);
    }

    // 🧹 Cleanup après chaque test
    [TearDown]
    public void TearDown()
    {
        _userService?.Dispose();
    }
}
```

---

## 📊 Tableau Récapitulatif

| **Terme**       | **🎯 Rôle**            | **📝 Exemple C#**            | **🔧 Utilisation**       |
| --------------- | ---------------------- | ---------------------------- | ------------------------ |
| **Test Case**   | 🧪 Scénario spécifique | `[Test] public void Login()` | Vérifier un comportement |
| **Test Suite**  | 📦 Groupe de tests     | `[TestFixture] public class` | Organiser les tests      |
| **Test Runner** | 🏃 Exécuteur           | `dotnet test`, NUnit, xUnit  | Lancer et reporter       |
| **Assertion**   | ✅ Vérification        | `Assert.That().Is.EqualTo()` | Valider le résultat      |
| **Fixture**     | 🏗️ Données test        | `UserFixture.GetValidUser()` | État initial prévisible  |
| **Mock**        | 🎭 Faux intelligent    | `Mock<IService>().Setup()`   | Simuler dépendances      |
| **Stub**        | 🔌 Réponse fixe        | `DateTimeStub : IDateTime`   | Valeurs prédéfinies      |
| **SUT**         | 🎯 Code testé          | `userService.CreateAsync()`  | Ce qu'on teste vraiment  |

---

## 🛠️ Frameworks et Outils C#

### **📚 Frameworks de Test**

```csharp
// NUnit - Le plus populaire
[TestFixture]
public class MyTests
{
    [Test]
    public void MonTest() { }
}

// xUnit - Moderne et extensible
public class MyTests
{
    [Fact]
    public void MonTest() { }
}

// MSTest - Microsoft officiel
[TestClass]
public class MyTests
{
    [TestMethod]
    public void MonTest() { }
}
```

### **🎭 Outils de Mocking**

```csharp
// Moq - Le plus utilisé
var mock = new Mock<IService>();
mock.Setup(x => x.Method()).Returns(result);

// NSubstitute - Syntaxe fluide
var substitute = Substitute.For<IService>();
substitute.Method().Returns(result);

// FakeItEasy - Syntaxe naturelle
var fake = A.Fake<IService>();
A.CallTo(() => fake.Method()).Returns(result);
```

### **🗄️ Bases de Données de Test**

```csharp
// Entity Framework In-Memory
services.AddDbContext<TestDbContext>(options =>
    options.UseInMemoryDatabase("TestDb"));

// SQLite In-Memory
services.AddDbContext<TestDbContext>(options =>
    options.UseSqlite("DataSource=:memory:"));
```

---

## 💡 Conseils Pratiques

### ✅ **Bonnes Pratiques**

- **📛 Noms explicites** : `DevraitRetournerErreurQuandEmailInvalide`
- **🎯 Un concept par test** : Ne testez qu'une chose à la fois
- **🏗️ Setup propre** : Utilisez `[SetUp]` et `[TearDown]`
- **🎭 Mocks précis** : Ne moquez que les dépendances externes
- **🔍 SUT identifiable** : Clair sur ce qui est testé

### ❌ **Erreurs à Éviter**

- **🙅 Tests trop complexes** : Si c'est dur à comprendre, c'est mal conçu
- **🎭 Trop de mocks** : Vous testez les mocks, pas votre code
- **🔧 Tests fragiles** : Qui cassent pour rien
- **📝 Assertions multiples** : Difficile à déboguer quand ça échoue

### **🚀 Commandes Utiles**

```bash
# Créer un projet de test
dotnet new nunit -n MonProjet.Tests

# Ajouter les packages
dotnet add package NUnit
dotnet add package NUnit3TestAdapter
dotnet add package Moq

# Exécuter les tests
dotnet test

# Avec couverture de code
dotnet test --collect:"XPlat Code Coverage"
```

---

## 🚀 Étapes pour Maîtriser le Vocabulaire

1. **📚 Commencer** par écrire des Test Cases simples avec NUnit/xUnit
2. **📦 Organiser** en Test Suites avec `[TestFixture]`
3. **🏃 Utiliser** `dotnet test` comme Test Runner
4. **✅ Maîtriser** les assertions de votre framework
5. **🏗️ Créer** des fixtures réutilisables
6. **🎭 Apprendre** Moq pour les mocks
7. **🎯 Identifier** clairement votre SUT

---

> 💡 **Astuce** : La maîtrise du vocabulaire facilite la communication en équipe et la lecture de la documentation .NET !
