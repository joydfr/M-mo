# 🏆 Bonnes Pratiques des Tests

## 🎯 Introduction

Écrire des tests, c'est bien. Écrire de **bons tests**, c'est mieux ! Découvrons les pratiques qui transforment vos tests en véritables gardiens de la qualité.

---

## 🏗️ Structure d'un Test

### 📐 **Arrange-Act-Assert (AAA)**

**💡 Principe :** Structure en **3 phases distinctes** pour des tests clairs et maintenables

```
🏗️ ARRANGE  → Préparer les données et l'environnement
🎬 ACT      → Exécuter l'action à tester
✅ ASSERT   → Vérifier le résultat obtenu
```

#### **📝 Exemple JavaScript**

```javascript
test("calculatrice devrait additionner deux nombres", () => {
  // 🏗️ ARRANGE - Préparation
  const calculatrice = new Calculatrice();
  const nombre1 = 5;
  const nombre2 = 3;
  const resultatAttendu = 8;

  // 🎬 ACT - Action
  const resultat = calculatrice.additionner(nombre1, nombre2);

  // ✅ ASSERT - Vérification
  expect(resultat).toBe(resultatAttendu);
});
```

#### **📝 Exemple avec API**

```javascript
test("API devrait créer un nouvel utilisateur", async () => {
  // 🏗️ ARRANGE
  const nouveauUtilisateur = {
    nom: "Dupont",
    email: "dupont@test.com",
    age: 30,
  };

  // 🎬 ACT
  const response = await fetch("/users", {
    method: "POST",
    body: JSON.stringify(nouveauUtilisateur),
  });
  const utilisateurCree = await response.json();

  // ✅ ASSERT
  expect(response.status).toBe(201);
  expect(utilisateurCree.nom).toBe("Dupont");
  expect(utilisateurCree.id).toBeDefined();
});
```

---

### 🥒 **Given-When-Then (Gherkin)**

**💡 Principe :** Structure **orientée métier** qui raconte une histoire

```
🎯 GIVEN   → Étant donné un contexte initial
⚡ WHEN    → Quand une action se produit
✅ THEN    → Alors le résultat devrait être...
```

#### **📝 Exemple E-commerce**

```javascript
test("remise devrait être appliquée pour commande > 100€", () => {
  // 🎯 GIVEN - Contexte initial
  const panier = new Panier();
  panier.ajouterProduit({ nom: "Laptop", prix: 120 });
  const codePromo = "REDUCTION10";

  // ⚡ WHEN - Action déclenchée
  const total = panier.calculerTotal(codePromo);

  // ✅ THEN - Résultat attendu
  expect(total).toBe(108); // 120 - 10%
  expect(panier.remiseAppliquee).toBe(true);
});
```

#### **📝 Exemple avec scénario complexe**

```javascript
describe("Système de réservation", () => {
  test("client peut réserver une chambre disponible", () => {
    // 🎯 GIVEN - État initial
    const hotel = new Hotel();
    hotel.ajouterChambre({ numero: 101, type: "simple", disponible: true });
    const client = { nom: "Martin", email: "martin@test.com" };

    // ⚡ WHEN - Action métier
    const reservation = hotel.reserver(101, client, "2024-07-15");

    // ✅ THEN - Vérifications métier
    expect(reservation.confirmee).toBe(true);
    expect(reservation.numeroReservation).toBeDefined();
    expect(hotel.getChambre(101).disponible).toBe(false);
  });
});
```

---

### 🔄 **Comparaison AAA vs Given-When-Then**

| **Aspect**     | **AAA** 🏗️       | **Given-When-Then** 🥒 |
| -------------- | ---------------- | ---------------------- |
| **Focus**      | Technique        | Métier/Fonctionnel     |
| **Audience**   | Développeurs     | Équipe élargie         |
| **Style**      | Impératif        | Déclaratif             |
| **Usage**      | Tests unitaires  | Tests d'acceptation    |
| **Lisibilité** | Claire pour devs | Claire pour tous       |

---

## 🔒 Tests Isolés

### 🎯 **Principe d'Isolation**

**💡 Définition :** Chaque test doit être **indépendant** des autres et de l'environnement externe

### ✅ **Caractéristiques d'un Test Isolé**

#### **🚫 Pas de Dépendances Externes**

```javascript
// ❌ MAL - Dépend d'une vraie base de données
test("devrait sauvegarder utilisateur", async () => {
  const user = { nom: "Test" };
  const result = await database.save(user); // 💥 Dépendance externe
  expect(result.id).toBeDefined();
});

// ✅ BIEN - Utilise un mock
test("devrait sauvegarder utilisateur", async () => {
  // 🎭 Mock de la base de données
  const mockDb = {
    save: jest.fn().mockResolvedValue({ id: 1, nom: "Test" }),
  };

  const userService = new UserService(mockDb);
  const result = await userService.creerUtilisateur({ nom: "Test" });

  expect(result.id).toBe(1);
  expect(mockDb.save).toHaveBeenCalledWith({ nom: "Test" });
});
```

#### **🔄 Pas d'État Partagé**

```javascript
// ❌ MAL - Variable globale partagée
let compteurGlobal = 0;

test("devrait incrémenter compteur", () => {
  compteurGlobal++; // 💥 État partagé
  expect(compteurGlobal).toBe(1);
});

test("devrait doubler compteur", () => {
  compteurGlobal *= 2; // 💥 Dépend du test précédent
  expect(compteurGlobal).toBe(2); // ❌ Échoue si tests dans un autre ordre
});

// ✅ BIEN - Chaque test a son propre état
test("devrait incrémenter compteur", () => {
  const compteur = new Compteur(0); // 🎯 État local
  compteur.incrementer();
  expect(compteur.valeur).toBe(1);
});

test("devrait doubler compteur", () => {
  const compteur = new Compteur(1); // 🎯 État indépendant
  compteur.doubler();
  expect(compteur.valeur).toBe(2);
});
```

#### **🔧 Setup/Teardown Propres**

```javascript
describe("UserService", () => {
  let userService;
  let mockDatabase;

  // 🏗️ Setup avant chaque test
  beforeEach(() => {
    mockDatabase = createMockDatabase();
    userService = new UserService(mockDatabase);
  });

  // 🧹 Nettoyage après chaque test
  afterEach(() => {
    mockDatabase.reset();
    userService = null;
  });

  test("devrait créer utilisateur", () => {
    // 🎯 Test isolé avec son propre contexte
    const result = userService.creer({ nom: "John" });
    expect(result).toBeDefined();
  });
});
```

---

## 🔄 Tests Indépendants

### 🎯 **Principe d'Indépendance**

**💡 Définition :** L'ordre d'exécution des tests ne doit **jamais** affecter le résultat

### ✅ **Bonnes Pratiques pour l'Indépendance**

#### **🎯 Tests Auto-Suffisants**

```javascript
// ✅ BIEN - Chaque test se prépare lui-même
describe("Panier d'achat", () => {
  test("devrait calculer total vide", () => {
    const panier = new Panier(); // 🎯 Création locale
    expect(panier.total()).toBe(0);
  });

  test("devrait calculer total avec produits", () => {
    const panier = new Panier(); // 🎯 Nouveau panier
    panier.ajouter({ prix: 10 });
    panier.ajouter({ prix: 20 });
    expect(panier.total()).toBe(30);
  });

  test("devrait appliquer remise", () => {
    const panier = new Panier(); // 🎯 État propre
    panier.ajouter({ prix: 100 });
    panier.appliquerRemise(0.1);
    expect(panier.total()).toBe(90);
  });
});
```

#### **🔀 Test d'Ordre d'Exécution**

```javascript
// 🧪 Vérifiez que vos tests passent dans n'importe quel ordre
describe("Tests d'indépendance", () => {
  // Ces tests doivent passer même si exécutés dans le désordre

  test("Z - dernier alphabétiquement", () => {
    const service = new MonService();
    expect(service.methodeZ()).toBe("Z");
  });

  test("A - premier alphabétiquement", () => {
    const service = new MonService();
    expect(service.methodeA()).toBe("A");
  });

  test("M - milieu alphabétiquement", () => {
    const service = new MonService();
    expect(service.methodeM()).toBe("M");
  });
});
```

#### **📊 Données de Test Indépendantes**

```javascript
// ✅ Factory pattern pour créer des données fraîches
class TestDataFactory {
  static creerUtilisateur(options = {}) {
    return {
      id: Math.random(), // 🎲 ID unique
      nom: options.nom || "Test User",
      email: options.email || `test${Date.now()}@example.com`,
      createdAt: new Date(),
      ...options,
    };
  }
}

test("devrait valider email unique", () => {
  const user = TestDataFactory.creerUtilisateur({
    email: "unique@test.com",
  });
  expect(validateur.emailUnique(user.email)).toBe(true);
});
```

---

## 🔄 Tests Reproductibles

### 🎯 **Principe de Reproductibilité**

**💡 Définition :** Le test doit donner le **même résultat** à chaque exécution

### ✅ **Techniques pour la Reproductibilité**

#### **⏰ Contrôle du Temps**

```javascript
// ❌ MAL - Dépend de l'heure réelle
test("devrait créer timestamp récent", () => {
  const service = new TimestampService();
  const timestamp = service.maintenant();
  const maintenant = Date.now();

  // 💥 Peut échouer selon la vitesse d'exécution
  expect(timestamp).toBe(maintenant);
});

// ✅ BIEN - Temps contrôlé
test("devrait créer timestamp fixe", () => {
  const dateFixe = new Date("2024-01-15T10:30:00Z");
  jest.spyOn(Date, "now").mockReturnValue(dateFixe.getTime());

  const service = new TimestampService();
  const timestamp = service.maintenant();

  expect(timestamp).toBe(dateFixe.getTime());

  // 🧹 Nettoyage
  Date.now.mockRestore();
});
```

#### **🎲 Contrôle de l'Aléatoire**

```javascript
// ❌ MAL - Résultat imprévisible
test("devrait générer identifiant", () => {
  const service = new IdService();
  const id = service.genererId();

  // 💥 Différent à chaque exécution
  expect(id).toBe("abc123"); // Échoue aléatoirement
});

// ✅ BIEN - Aléatoire contrôlé
test("devrait générer identifiant déterministe", () => {
  // 🎲 Mock du générateur aléatoire
  jest.spyOn(Math, "random").mockReturnValue(0.5);

  const service = new IdService();
  const id = service.genererId();

  expect(id).toBe("id_500"); // Toujours le même résultat

  Math.random.mockRestore();
});
```

#### **🌐 Isolation Réseau**

```javascript
// ❌ MAL - Dépend d'un service externe
test("devrait récupérer données utilisateur", async () => {
  const service = new UserService();
  // 💥 Dépend d'une API externe
  const user = await service.getUser(1);
  expect(user.nom).toBe("John");
});

// ✅ BIEN - Réseau mocké
test("devrait récupérer données utilisateur", async () => {
  // 🌐 Mock de la requête HTTP
  const mockResponse = { nom: "John", id: 1 };
  jest.spyOn(global, "fetch").mockResolvedValue({
    ok: true,
    json: () => Promise.resolve(mockResponse),
  });

  const service = new UserService();
  const user = await service.getUser(1);

  expect(user.nom).toBe("John");
  expect(fetch).toHaveBeenCalledWith("/api/users/1");

  fetch.mockRestore();
});
```

#### **💾 Base de Données Contrôlée**

```javascript
describe("UserRepository", () => {
  let database;

  beforeEach(async () => {
    // 🗄️ Base de données en mémoire pour les tests
    database = await createInMemoryDatabase();

    // 🌱 Données initiales contrôlées
    await database.seed([
      { id: 1, nom: "Alice", email: "alice@test.com" },
      { id: 2, nom: "Bob", email: "bob@test.com" },
    ]);
  });

  afterEach(async () => {
    // 🧹 Nettoyage complet
    await database.cleanup();
  });

  test("devrait trouver utilisateur par email", async () => {
    const repo = new UserRepository(database);
    const user = await repo.findByEmail("alice@test.com");

    expect(user.nom).toBe("Alice");
    expect(user.id).toBe(1);
  });
});
```

---

## 🛠️ Outils pour de Bons Tests

### 🎯 **Helpers et Utilities**

#### **🏭 Test Builders**

```javascript
// 🏗️ Builder pour créer des objets de test
class UserBuilder {
  constructor() {
    this.data = {
      nom: "Default User",
      email: "default@test.com",
      age: 25,
      actif: true,
    };
  }

  withNom(nom) {
    this.data.nom = nom;
    return this;
  }

  withEmail(email) {
    this.data.email = email;
    return this;
  }

  inactif() {
    this.data.actif = false;
    return this;
  }

  build() {
    return { ...this.data };
  }
}

// 📝 Usage dans les tests
test("devrait valider utilisateur actif", () => {
  const user = new UserBuilder()
    .withNom("John")
    .withEmail("john@test.com")
    .build();

  expect(validateur.estValide(user)).toBe(true);
});
```

#### **🎭 Mock Factories**

```javascript
// 🏭 Factory pour créer des mocks cohérents
class MockFactory {
  static creerMockRepository() {
    return {
      save: jest.fn(),
      findById: jest.fn(),
      findAll: jest.fn(),
      delete: jest.fn(),
    };
  }

  static creerMockEmailService() {
    return {
      send: jest.fn().mockResolvedValue({ sent: true }),
      validate: jest.fn().mockReturnValue(true),
    };
  }
}

test("service devrait utiliser repository", () => {
  const mockRepo = MockFactory.creerMockRepository();
  const service = new UserService(mockRepo);

  // Test utilisant le mock standardisé
});
```

---

## 📋 Checklist des Bonnes Pratiques

### ✅ **Structure et Organisation**

- [ ] **🏗️ AAA/Given-When-Then** : Structure claire en 3 phases
- [ ] **📝 Noms descriptifs** : `devrait_faire_X_quand_Y`
- [ ] **🎯 Un concept par test** : Pas de tests multiples
- [ ] **📦 Groupement logique** : Test suites cohérentes

### ✅ **Isolation et Indépendance**

- [ ] **🚫 Pas de dépendances externes** : APIs, BDD, fichiers
- [ ] **🔄 Pas d'état partagé** : Variables globales
- [ ] **🎭 Mocks appropriés** : Dépendances mockées
- [ ] **🧹 Setup/Teardown** : Environnement propre

### ✅ **Reproductibilité**

- [ ] **⏰ Temps contrôlé** : Pas de `Date.now()` direct
- [ ] **🎲 Aléatoire fixé** : Pas de `Math.random()` direct
- [ ] **🌐 Réseau mocké** : Pas d'appels HTTP réels
- [ ] **💾 Données fixes** : État initial prévisible

### ✅ **Qualité du Code de Test**

- [ ] **📖 Tests lisibles** : Code simple et clair
- [ ] **🚀 Tests rapides** : Exécution en millisecondes
- [ ] **🔧 Tests maintenables** : Faciles à modifier
- [ ] **❌ Tests fiables** : Peu de faux positifs/négatifs

---

## 🎯 Anti-Patterns à Éviter

### ❌ **Les Erreurs Classiques**

#### **🔗 Tests Interdépendants**

```javascript
// ❌ MAL - Tests liés
describe("BAD: Tests dépendants", () => {
  let user;

  test("devrait créer utilisateur", () => {
    user = createUser("John"); // 💥 État partagé
    expect(user.nom).toBe("John");
  });

  test("devrait modifier utilisateur", () => {
    user.nom = "Jane"; // 💥 Dépend du test précédent
    expect(user.nom).toBe("Jane");
  });
});
```

#### **🐌 Tests Lents**

```javascript
// ❌ MAL - Test lent
test("devrait traiter gros fichier", async () => {
  // 💥 Lit un vrai fichier de 100MB
  const data = await fs.readFile("huge-file.txt");
  const result = processData(data);
  expect(result).toBeDefined();
});

// ✅ BIEN - Test rapide
test("devrait traiter données", () => {
  const mockData = "sample data"; // 🎯 Données minimales
  const result = processData(mockData);
  expect(result).toBeDefined();
});
```

#### **🤯 Tests Complexes**

```javascript
// ❌ MAL - Test trop complexe
test("workflow complet e-commerce", () => {
  // 💥 Teste trop de choses à la fois
  const user = createUser();
  const product = createProduct();
  const cart = addToCart(user, product);
  const order = checkout(cart);
  const payment = processPayment(order);
  const shipping = shipOrder(payment);

  expect(shipping.status).toBe("shipped");
});
```

---

## 🚀 Plan d'Action

### 📈 **Progression Recommandée**

1. **🏗️ Semaine 1** : Maîtriser AAA/Given-When-Then
2. **🔒 Semaine 2** : Pratiquer l'isolation des tests
3. **🔄 Semaine 3** : Assurer l'indépendance
4. **🎯 Semaine 4** : Garantir la reproductibilité
5. **🛠️ Semaine 5** : Utiliser les outils avancés

### 🎯 **Exercices Pratiques**

1. **Refactorez** un test existant avec AAA
2. **Identifiez** les dépendances externes dans vos tests
3. **Créez** des mocks pour isoler vos tests
4. **Exécutez** vos tests dans un ordre aléatoire
5. **Mesurez** le temps d'exécution de votre suite

---

> 💡 **Conseil Final** : De bons tests sont un investissement à long terme. Ils coûtent plus cher à écrire initialement, mais économisent énormément de temps par la suite !
