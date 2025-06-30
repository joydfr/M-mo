# 📚 Vocabulaire Essentiel des Tests

## 🎯 Introduction

Maîtriser le vocabulaire des tests est essentiel pour comprendre et communiquer efficacement dans le monde du testing ! Voici tous les termes que vous devez connaître.

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

```javascript
// ✅ Un Test Case
test("devrait connecter utilisateur avec identifiants valides", () => {
  // Given - Données d'entrée
  const email = "user@test.com";
  const password = "123456";

  // When - Action
  const result = login(email, password);

  // Then - Vérification
  expect(result.success).toBe(true);
});
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

**💻 En code :**

```javascript
// 📦 Test Suite
describe("Authentification", () => {
  test("connexion réussie", () => {
    /* ... */
  });
  test("mot de passe incorrect", () => {
    /* ... */
  });
  test("email inexistant", () => {
    /* ... */
  });
});
```

---

### 🏃 **Test Runner (Lanceur de Tests)**

**💡 Définition :** L'outil qui **exécute vos tests** et génère les rapports

**🔧 Fonctionnalités :**

- **▶️ Exécution** automatique des tests
- **📊 Rapports** détaillés (succès/échecs)
- **⚡ Parallélisation** pour la vitesse
- **🔍 Filtrage** par nom, tag, etc.

**🛠️ Exemples populaires :**

```
Jest     🟨 → JavaScript/TypeScript
PHPUnit  🐘 → PHP
pytest   🐍 → Python
JUnit    ☕ → Java
RSpec    💎 → Ruby
```

**📊 Exemple de sortie :**

```
🏃 Test Runner Results:
✅ Authentification
  ✅ connexion réussie (12ms)
  ❌ mot de passe incorrect (8ms)
  ✅ email inexistant (15ms)

📊 Résumé: 2 passed, 1 failed, 3 total
```

---

## ✅ Les Assertions

### 🎯 **Assertion**

**💡 Définition :** Une **vérification** qui confirme qu'un résultat correspond à l'attendu

**🔍 Types d'assertions courantes :**

#### **⚖️ Égalité**

```javascript
expect(result).toBe(42); // Égalité stricte
expect(user.name).toEqual("John"); // Égalité de valeur
```

#### **✅ Booléens**

```javascript
expect(isValid).toBeTruthy(); // Vrai
expect(isEmpty).toBeFalsy(); // Faux
expect(isAdmin).toBe(true); // Strictement true
```

#### **📏 Comparaisons**

```javascript
expect(age).toBeGreaterThan(18); // > 18
expect(score).toBeLessThanOrEqual(100); // <= 100
```

#### **📦 Collections**

```javascript
expect(users).toHaveLength(3); // Taille
expect(fruits).toContain("pomme"); // Contient
expect(numbers).toEqual([1, 2, 3]); // Contenu identique
```

#### **❌ Exceptions**

```javascript
expect(() => diviser(10, 0)).toThrow(); // Lance erreur
expect(() => login("")).toThrow("Email requis"); // Message spécifique
```

---

## 🧰 Les Outils de Test

### 🏗️ **Fixture**

**💡 Définition :** **Données ou état initial** préparé pour les tests

**🎯 Objectif :** Avoir un environnement **prévisible et reproductible**

**📝 Types de Fixtures :**

#### **📊 Données de test**

```javascript
// 🏗️ Fixture - Données utilisateur
const userFixture = {
  id: 1,
  name: "John Doe",
  email: "john@test.com",
  role: "admin",
};

test("devrait afficher nom utilisateur", () => {
  const user = userFixture; // 📊 Utilisation fixture
  expect(displayUserName(user)).toBe("John Doe");
});
```

#### **🗄️ Base de données**

```javascript
// 🏗️ Fixture - État BDD initial
beforeEach(() => {
  database.seed([
    { table: "users", data: userFixture },
    { table: "products", data: productFixtures },
  ]);
});
```

#### **📁 Fichiers**

```javascript
// 🏗️ Fixture - Fichier JSON de test
const responseFixture = require("./fixtures/api_response.json");
```

---

### 🎭 **Mock (Simulacre)**

**💡 Définition :** **Faux objet** qui imite le comportement d'un vrai composant

**🎯 Utilisation :** Isoler le code testé des dépendances externes

**📝 Exemples pratiques :**

#### **🌐 Mock d'API**

```javascript
// 🎭 Mock d'un service externe
const mockApiService = {
  getUser: jest.fn().mockResolvedValue({
    id: 1,
    name: "John",
  }),
  updateUser: jest.fn().mockResolvedValue(true),
};

test("devrait récupérer utilisateur", async () => {
  const user = await getUserProfile(1);

  expect(mockApiService.getUser).toHaveBeenCalledWith(1);
  expect(user.name).toBe("John");
});
```

#### **💾 Mock de base de données**

```javascript
// 🎭 Mock du repository
const mockUserRepository = {
  findById: jest.fn(),
  save: jest.fn(),
  delete: jest.fn(),
};
```

#### **📧 Mock de services**

```javascript
// 🎭 Mock service email
const mockEmailService = {
  send: jest.fn().mockResolvedValue({ sent: true }),
};
```

---

### 🔌 **Stub (Bouchon)**

**💡 Définition :** Version **simplifiée** d'un composant qui retourne des réponses prédéfinies

**🔄 Différence avec Mock :** Stub = réponses fixes, Mock = comportement intelligent

**📝 Exemples :**

#### **⏰ Stub de date**

```javascript
// 🔌 Stub pour date fixe
const dateStub = new Date("2024-01-15");
Date.now = jest.fn(() => dateStub.getTime());

test("devrait créer rapport avec date actuelle", () => {
  const report = createReport();
  expect(report.date).toBe("2024-01-15");
});
```

#### **🎲 Stub de random**

```javascript
// 🔌 Stub pour valeur aléatoire fixe
Math.random = jest.fn(() => 0.5);

test("devrait générer nombre prévisible", () => {
  const number = generateRandomNumber();
  expect(number).toBe(50); // Basé sur 0.5
});
```

#### **🌐 Stub de configuration**

```javascript
// 🔌 Stub de configuration
const configStub = {
  apiUrl: "https://test-api.com",
  timeout: 5000,
  retries: 3,
};
```

---

## 🎯 System Under Test (SUT)

### 🔍 **System Under Test (SUT)**

**💡 Définition :** Le **composant ou système** que vous êtes en train de tester

**🎯 Objectif :** Identifier clairement **ce qui est testé** vs **ce qui est mocké**

**📝 Exemples par niveau :**

#### **⚡ Test Unitaire - SUT = Fonction**

```javascript
// 🎯 SUT : La fonction calculateTotal
function calculateTotal(items, discount) {
  return items.reduce((sum, item) => sum + item.price, 0) * (1 - discount);
}

test("calculateTotal devrait appliquer remise", () => {
  const items = [{ price: 100 }, { price: 50 }];

  // 🎯 SUT appelé ici
  const total = calculateTotal(items, 0.1);

  expect(total).toBe(135); // 150 - 10%
});
```

#### **🧩 Test Intégration - SUT = Service**

```javascript
// 🎯 SUT : Le service UserService
class UserService {
  constructor(repository, emailService) {
    this.repository = repository;
    this.emailService = emailService;
  }

  async createUser(userData) {
    const user = await this.repository.save(userData);
    await this.emailService.sendWelcome(user.email);
    return user;
  }
}

test("UserService devrait créer utilisateur et envoyer email", async () => {
  // 🎭 Mocks des dépendances
  const mockRepo = { save: jest.fn().mockResolvedValue(user) };
  const mockEmail = { sendWelcome: jest.fn() };

  // 🎯 SUT : UserService
  const userService = new UserService(mockRepo, mockEmail);

  const result = await userService.createUser(userData);

  expect(result).toBeDefined();
  expect(mockEmail.sendWelcome).toHaveBeenCalled();
});
```

#### **🔍 Test E2E - SUT = Application complète**

```javascript
// 🎯 SUT : Toute l'application web
test("utilisateur peut commander un produit", () => {
  // 🎯 SUT : Interface utilisateur complète
  cy.visit("/");
  cy.get('[data-test="product"]').first().click();
  cy.get('[data-test="add-to-cart"]').click();
  cy.get('[data-test="checkout"]').click();

  cy.url().should("include", "/order-confirmation");
});
```

---

## 🏗️ Architecture Typique d'un Test

### 📋 **Anatomie Complète**

```javascript
// 📦 Test Suite
describe("UserService", () => {
  // 🏗️ Fixtures
  const userFixture = {
    name: "John Doe",
    email: "john@test.com",
  };

  // 🎭 Mocks
  let mockRepository;
  let mockEmailService;

  // 🎯 SUT
  let userService;

  // ⚙️ Setup avant chaque test
  beforeEach(() => {
    mockRepository = {
      save: jest.fn(),
      findById: jest.fn(),
    };

    mockEmailService = {
      send: jest.fn(),
    };

    // 🎯 Initialisation du SUT
    userService = new UserService(mockRepository, mockEmailService);
  });

  // 🧪 Test Case
  test("devrait créer utilisateur avec succès", async () => {
    // 🔌 Configuration des stubs
    mockRepository.save.mockResolvedValue({
      id: 1,
      ...userFixture,
    });

    // 🎯 Appel du SUT
    const result = await userService.createUser(userFixture);

    // ✅ Assertions
    expect(result.id).toBe(1);
    expect(result.name).toBe("John Doe");
    expect(mockRepository.save).toHaveBeenCalledWith(userFixture);
    expect(mockEmailService.send).toHaveBeenCalled();
  });
});
```

---

## 📊 Tableau Récapitulatif

| **Terme**       | **🎯 Rôle**            | **📝 Exemple**           | **🔧 Utilisation**       |
| --------------- | ---------------------- | ------------------------ | ------------------------ |
| **Test Case**   | 🧪 Scénario spécifique | `test('login valide')`   | Vérifier un comportement |
| **Test Suite**  | 📦 Groupe de tests     | `describe('Auth')`       | Organiser les tests      |
| **Test Runner** | 🏃 Exécuteur           | Jest, PHPUnit            | Lancer et reporter       |
| **Assertion**   | ✅ Vérification        | `expect().toBe()`        | Valider le résultat      |
| **Fixture**     | 🏗️ Données test        | `userFixture = {...}`    | État initial prévisible  |
| **Mock**        | 🎭 Faux intelligent    | `jest.fn().mockReturn()` | Simuler dépendances      |
| **Stub**        | 🔌 Réponse fixe        | `Date.now = () => 123`   | Valeurs prédéfinies      |
| **SUT**         | 🎯 Code testé          | `userService.create()`   | Ce qu'on teste vraiment  |

---

## 💡 Conseils Pratiques

### ✅ **Bonnes Pratiques**

- **📛 Noms explicites** : `devrait_retourner_erreur_quand_email_invalide`
- **🎯 Un concept par test** : Ne testez qu'une chose à la fois
- **🏗️ Setup propre** : Fixtures réutilisables et claires
- **🎭 Mocks précis** : Ne moquez que ce qui est nécessaire
- **🔍 SUT identifiable** : Clair sur ce qui est testé

### ❌ **Erreurs à Éviter**

- **🙅 Tests trop complexes** : Si c'est dur à comprendre, c'est mal conçu
- **🎭 Trop de mocks** : Vous testez les mocks, pas votre code
- **🔧 Tests fragiles** : Qui cassent pour rien
- **📝 Assertions multiples** : Difficile à déboguer quand ça échoue

---

## 🚀 Étapes pour Maîtriser le Vocabulaire

1. **📚 Commencer** par écrire des Test Cases simples
2. **📦 Organiser** en Test Suites logiques
3. **🏃 Utiliser** un Test Runner adapté à votre langage
4. **✅ Maîtriser** les assertions de base
5. **🏗️ Créer** des fixtures réutilisables
6. **🎭 Apprendre** à mocker progressivement
7. **🎯 Identifier** clairement votre SUT

---

> 💡 **Astuce** : La maîtrise du vocabulaire facilite la communication en équipe et la lecture de documentation !
