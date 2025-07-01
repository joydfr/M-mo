# 🎓 Tests Unitaires C# - Guide Débutant Complet

## 🚀 Étape 0 : Configuration et Premier Test

### 📦 Installation des packages NuGet

```xml
<!-- Dans votre fichier .csproj de test -->
<PackageReference Include="Microsoft.NET.Test.Sdk" Version="17.0.0" />
<PackageReference Include="NUnit" Version="3.13.2" />
<PackageReference Include="NUnit3TestAdapter" Version="4.1.0" />
<PackageReference Include="Moq" Version="4.18.0" />
```

### 🏗️ Structure de projet recommandée

```
MonProjet/
├── MonProjet/
│   └── Calculatrice.cs
└── MonProjet.Tests/
    └── CalculatriceTests.cs
```

### 👶 Mon Premier Test (Exemple complet)

```csharp
// Dans Calculatrice.cs
public class Calculatrice
{
    public int Additionner(int a, int b)
    {
        return a + b;
    }
}

// Dans CalculatriceTests.cs
using NUnit.Framework;

[TestFixture]
public class CalculatriceTests
{
    [Test]
    public void Additionner_Avec2Et3_Retourne5()
    {
        // Arrange (Préparation)
        var calculatrice = new Calculatrice();
        int a = 2;
        int b = 3;
        int resultatAttendu = 5;

        // Act (Action)
        int resultat = calculatrice.Additionner(a, b);

        // Assert (Vérification)
        Assert.AreEqual(resultatAttendu, resultat);
    }
}
```

---

## 🎯 Exercice 1 : Calculatrice Ultra-Simple

### 📝 Code à tester

```csharp
public class Calculatrice
{
    public int Additionner(int a, int b)
    {
        return a + b;
    }

    public int Soustraire(int a, int b)
    {
        return a - b;
    }
}
```

### 📋 Template de test pour vous aider

```csharp
using NUnit.Framework;

[TestFixture]
public class CalculatriceTests
{
    private Calculatrice _calculatrice;

    [SetUp]
    public void Setup()
    {
        // Cette méthode s'exécute avant chaque test
        _calculatrice = new Calculatrice();
    }

    [Test]
    public void Additionner_AvecDeuxNombresPositifs_RetourneLaSomme()
    {
        // Arrange
        int a = /* À COMPLÉTER */;
        int b = /* À COMPLÉTER */;
        int attendu = /* À COMPLÉTER */;

        // Act
        int resultat = /* À COMPLÉTER */;

        // Assert
        Assert.AreEqual(/* À COMPLÉTER */);
    }

    [Test]
    public void Additionner_AvecZero_RetourneLAutreNombre()
    {
        // TODO: Écrivez ce test vous-même !
    }

    [Test]
    public void Soustraire_AvecDeuxNombres_RetourneLaDifference()
    {
        // TODO: Écrivez ce test vous-même !
    }
}
```

**🎯 Mission :** Complétez les tests ci-dessus !

---

## 🎯 Exercice 2 : Gestion des Exceptions

### 📝 Code à tester

```csharp
public class Diviseur
{
    public double Diviser(int a, int b)
    {
        if (b == 0)
            throw new DivideByZeroException("Division par zéro interdite");

        return (double)a / b;
    }
}
```

### 📋 Template de test

```csharp
[TestFixture]
public class DiviseurTests
{
    private Diviseur _diviseur;

    [SetUp]
    public void Setup()
    {
        _diviseur = new Diviseur();
    }

    [Test]
    public void Diviser_AvecNombreurEtDenominateur_RetourneLeQuotient()
    {
        // Arrange
        int a = 10;
        int b = 2;
        double attendu = 5.0;

        // Act
        double resultat = _diviseur.Diviser(a, b);

        // Assert
        Assert.AreEqual(attendu, resultat, 0.001); // 0.001 = tolérance pour les doubles
    }

    [Test]
    public void Diviser_ParZero_LanceUneException()
    {
        // Arrange
        int a = 10;
        int b = 0;

        // Act & Assert (en une seule ligne pour les exceptions)
        Assert.Throws<DivideByZeroException>(() => _diviseur.Diviser(a, b));
    }
}
```

**🎯 Mission :** Exécutez ces tests et ajoutez un test pour la division de nombres négatifs !

---

## 🎯 Exercice 3 : Mon Premier Mock (Simulation)

### 🤔 Pourquoi mocker ?

Imaginez un service qui envoie des emails. Vous ne voulez pas envoyer de vrais emails à chaque test !

### 📝 Code à tester

```csharp
public interface IEmailService
{
    bool EnvoyerEmail(string destinataire, string message);
}

public class NotificationService
{
    private readonly IEmailService _emailService;

    public NotificationService(IEmailService emailService)
    {
        _emailService = emailService;
    }

    public string EnvoyerBienvenue(string email, string nom)
    {
        if (string.IsNullOrEmpty(nom))
            return "Nom invalide";

        string message = $"Bienvenue {nom} !";
        bool succes = _emailService.EnvoyerEmail(email, message);

        return succes ? "Email envoyé" : "Échec envoi";
    }
}
```

### 📋 Template de test avec Mock

```csharp
using Moq;
using NUnit.Framework;

[TestFixture]
public class NotificationServiceTests
{
    private Mock<IEmailService> _mockEmailService;
    private NotificationService _notificationService;

    [SetUp]
    public void Setup()
    {
        // Créer un faux EmailService
        _mockEmailService = new Mock<IEmailService>();

        // Injecter le faux dans notre service
        _notificationService = new NotificationService(_mockEmailService.Object);
    }

    [Test]
    public void EnvoyerBienvenue_AvecNomValide_RetourneEmailEnvoye()
    {
        // Arrange
        string email = "test@example.com";
        string nom = "John";

        // Dire au mock de retourner "true" quand on appelle EnvoyerEmail
        _mockEmailService.Setup(x => x.EnvoyerEmail(email, "Bienvenue John !"))
                        .Returns(true);

        // Act
        string resultat = _notificationService.EnvoyerBienvenue(email, nom);

        // Assert
        Assert.AreEqual("Email envoyé", resultat);

        // Vérifier que l'email a bien été "envoyé"
        _mockEmailService.Verify(x => x.EnvoyerEmail(email, "Bienvenue John !"), Times.Once);
    }

    [Test]
    public void EnvoyerBienvenue_AvecNomVide_RetourneNomInvalide()
    {
        // TODO: Écrivez ce test !
        // Indice: pas besoin de setup ici, on teste juste la validation
    }
}
```

**🎯 Mission :** Complétez le deuxième test !

---

## 🎯 Exercice 4 : Test d'une Classe avec État

### 📝 Code à tester

```csharp
public class CompteBancaire
{
    private decimal _solde;

    public CompteBancaire(decimal soldeInitial = 0)
    {
        _solde = soldeInitial;
    }

    public decimal Solde => _solde;

    public void Deposer(decimal montant)
    {
        if (montant <= 0)
            throw new ArgumentException("Le montant doit être positif");

        _solde += montant;
    }

    public void Retirer(decimal montant)
    {
        if (montant <= 0)
            throw new ArgumentException("Le montant doit être positif");

        if (montant > _solde)
            throw new InvalidOperationException("Solde insuffisant");

        _solde -= montant;
    }
}
```

### 📋 Template de test

```csharp
[TestFixture]
public class CompteBancaireTests
{
    [Test]
    public void NouveauCompte_SansParametre_SoldeEstZero()
    {
        // Arrange & Act
        var compte = new CompteBancaire();

        // Assert
        Assert.AreEqual(0, compte.Solde);
    }

    [Test]
    public void Deposer_MontantPositif_AugmenteLeSolde()
    {
        // Arrange
        var compte = new CompteBancaire(100);
        decimal montant = 50;

        // Act
        compte.Deposer(montant);

        // Assert
        Assert.AreEqual(150, compte.Solde);
    }

    [Test]
    public void Deposer_MontantNegatif_LanceException()
    {
        // TODO: Écrivez ce test !
    }

    [Test]
    public void Retirer_MontantSuperieurAuSolde_LanceException()
    {
        // TODO: Écrivez ce test !
    }
}
```

**🎯 Mission :** Complétez les tests manquants !

---

## 📚 Guide de Survie - Assertions Courantes

```csharp
// Égalité
Assert.AreEqual(attendu, actuel);
Assert.AreNotEqual(attendu, actuel);

// Vrai/Faux
Assert.IsTrue(condition);
Assert.IsFalse(condition);

// Null
Assert.IsNull(objet);
Assert.IsNotNull(objet);

// Exceptions
Assert.Throws<TypeException>(() => methodeQuiLanceException());

// Collections
Assert.Contains(element, collection);
Assert.IsEmpty(collection);

// Strings
Assert.AreEqual("attendu", actuel, ignoreCase: true);
```

---

## 🎭 Guide de Survie - Mocking avec Moq

```csharp
// Créer un mock
var mock = new Mock<IInterface>();

// Définir un comportement
mock.Setup(x => x.Methode(It.IsAny<string>())).Returns("resultat");

// Utiliser le mock
IInterface fakeService = mock.Object;

// Vérifier qu'une méthode a été appelée
mock.Verify(x => x.Methode("parametre"), Times.Once);
mock.Verify(x => x.Methode(It.IsAny<string>()), Times.Never);
```

---

## ✅ Checklist Débutant

Avant de valider un test, vérifiez :

- [ ] ✅ Mon test a un nom descriptif (`Quoi_Dans_Quel_Cas_Resultat_Attendu`)
- [ ] ✅ J'ai bien séparé Arrange / Act / Assert
- [ ] ✅ Je teste une seule chose à la fois
- [ ] ✅ Mon test est indépendant (peut tourner seul)
- [ ] ✅ Mon test est rapide (pas d'accès réseau/BDD)
- [ ] ✅ J'ai testé les cas d'erreur (exceptions)

---

## 🏃‍♂️ Pour aller plus loin

1. **Exécutez vos tests** : `dotnet test` en ligne de commande
2. **Regardez la couverture** : Combien de votre code est testé ?
3. **Red-Green-Refactor** : Écrivez le test en premier (TDD)

**Commencez petit, testez souvent ! 🚀**
