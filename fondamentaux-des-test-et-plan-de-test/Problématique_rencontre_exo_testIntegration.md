# 📋 MÉMO - Problématiques Rencontrées et Solutions

## 🚀 Projet BookApi

### 1. Erreurs de syntaxe dans `BooksController.cs`

- **Problème :**
  - `private readondly BookService` (faute de frappe dans `readonly`)
- **Erreur :**
  - Compilation échouée à cause du mot-clé incorrect
  ```bash
  CS1002: ; attendu
  CS1519: Jeton ';' non valide dans la déclaration de membre
  ```
- **Solution :**

  - Correction en `private readonly BookService`

  ```bash
  // ❌ Avant
      private readondly BookService _bookService;

  // ✅ Après
      private readonly BookService _bookService;
  ```

### 2. Casse incorrecte dans le modèle `Book.cs`

- **Problème :**
  - Classe définie comme `book` (minuscule) au lieu de `Book` (majuscule)
- **Erreur :**
  - Incohérence de casse, erreurs de compilation ou de mapping
  ```bash
  CS0246: Le type ou le nom d'espace de noms 'book' est introuvable
  ```
- **Solution :**
  - Renommage en `Book`

```bash
    // ❌ Avant
        public class book

    // ✅ Après
        public class Book
```

### 3. Classe `Program` inaccessible pour les tests d'intégration

- **Problème :**
  - Top-level statements empêchent l'accès à la classe `Program`
- **Erreur :**
  - Impossible de référencer `Program` dans les tests
  ```bash
  CS0234: Le nom de type ou d'espace de noms 'Program' n'existe pas dans l'espace de noms 'BookApi'
  ```
- **Solution :**
  - Conversion en classe `Program` traditionnelle avec namespace explicite
  - Ajout de `[assembly: InternalsVisibleTo("NomDuProjetDeTest")]` dans le fichier projet

```bash
    namespace BookApi
{
    public class Program
    {
        public static void Main(string[] args) { ... }
    }
}
```

### 4. Dépendance manquante pour les tests

- **Problème :**
  - Package `Microsoft.AspNetCore.Mvc.Testing` absent
- **Solution :**
  - Ajout du package via NuGet

```bash
   <PackageReference Include="Microsoft.AspNetCore.Mvc.Testing" Version="8.0.0" />
```

---

## 🎯 Projet TaskManagementApi

### 1. Erreurs de syntaxe dans `TaskManagementModel.cs`

- **Problème :**
  - Namespace sans accolades, `classe` au lieu de `class`, point-virgule superflu
- **Erreur :**
  - Compilation échouée
- **Solution :**
  - Correction de la syntaxe, utilisation de `class`, suppression des points-virgules inutiles

### 2. Structure incorrecte dans `Program.cs`

- **Problème :**
  - Mélange de top-level statements et classe
- **Erreur :**
  - Structure de code invalide

```bash
    CS1514: { attendue
    CS1513: } attendue
    CS1597: Point-virgule non valide après un bloc
```

- **Solution :**
  - Restructuration complète avec classe `Program` traditionnelle
  - Ajout de `app.MapControllers()`
  ```bash
  // ❌ Avant
  namespace TaskManagementApi
  public classe TaskItem {
      public int Id { get; set; };

  // ✅ Après
  namespace TaskManagementApi.Models
  {
  public class TaskItem
  {
      public int Id { get; set; }
  }
  ```

### 3. Erreurs dans `TaskManagementServices.cs`

- **Problème :**
  - Import incorrect, conflit de noms, type de retour incorrect
- **Erreur :**
  - Compilation échouée, erreurs de type

```bash
    CS1519: Jeton non valide dans la déclaration de membre
    CS8124: Le tuple doit contenir au moins deux éléments
    CS0116: Un espace de noms ne peut pas contenir directement des membres
```

- **Solution :**
  - Correction des imports, renommage des entités, ajustement des types de retour

### 4. Entity Framework non configuré (`DbContext.cs`)

- **Problème :**
  - Packages et imports manquants, namespace absent
- **Erreur :**
  - Impossible d'utiliser EF

```bash
     CS0246: Le nom de type ou d'espace de noms 'DbContext' est introuvable
    CS0246: Le nom de type ou d'espace de noms 'DbContextOptions<>' est introuvable
    CS0246: Le nom de type ou d'espace de noms 'DbSet<>' est introuvable
    CS0246: Le nom de type ou d'espace de noms 'TaskItem' est introuvable
```

- **Solution :**
  - Ajout des packages, imports et namespace

```bash
       <!-- Ajout des packages -->
    <PackageReference Include="Microsoft.EntityFrameworkCore" Version="8.0.0" />
    <PackageReference Include="Microsoft.EntityFrameworkCore.InMemory" Version="8.0.0" />
```

### 5. Erreurs dans les fichiers de tests

- **Problème :**
  - Références et imports incorrects, extension manquante
- **Erreur :**
  - Références incorrectes : TaskManagementApi.Data au lieu de TaskManagementApi.Database
  - AppDbContext au lieu de AppDbContexte
  - Import manquant : Microsoft.AspNetCore.Hosting
  - Extension PostAsJsonAsync manquante
- **Solution :**

  - Correction des références, ajout des imports nécessaires

  ```bash
      // Corrections des imports
      using Microsoft.AspNetCore.Hosting;
      using System.Net.Http.Json;
      using TaskManagementApi.Database;

      // Corrections des références
      services.AddDbContext<AppDbContexte>(options => ...)
  ```

### 6. Erreurs dans `TaskManagementController.cs`

- **Problème :**
  - Nom de constructeur incorrect, conventions non respectées, type de retour erroné
- **Erreur :**

  - Compilation échouée, comportements inattendus

  ```bash
  // ❌ Avant
  public class TaskManagementsController : ControllerBase
  {
      private readonly TaskService _TaskService; // PascalCase incorrect
      public TaskManagementController(TaskService taskService) // Nom incorrect
      {
          _TaskService = taskService;
      }

      [HttpGet]
      public ActionResult<IEnumerable<Task>> GetTask() // Type incorrect
      {
          returnOk(_TaskService.GetAll()); // Syntaxe incorrecte
      }

      [HttpPost]
      public ActionResult<IEbumerable<Task>> PostTask() // Type incorrect + faute
      {
          returnOK(_TaskService) // Syntaxe incorrecte
      }
  }
  ```

- **Solution :**
  - Correction des noms, conventions et types de retour

```bash
// ✅ Après
    public class TaskManagementsController : ControllerBase
    {
        private readonly TaskService _taskService; // camelCase correct

        public TaskManagementsController(TaskService taskService) // Nom correct
        {
            _taskService = taskService;
        }

        [HttpGet]
        public ActionResult<IEnumerable<TaskItem>> GetTasks() // Type correct
        {
            return Ok(_taskService.GetAll()); // Syntaxe correcte
        }

        [HttpPost]
        public async Task<ActionResult<TaskItem>> PostTask([FromBody] TaskItem taskItem) // Complet
        {
            if (taskItem == null)
                return BadRequest("Task item is required");

            var createdTask = await _taskService.PostTask(taskItem);
            return Ok(createdTask);
        }
    }
```

---

## 📊 Résumé des Solutions Appliquées

### 🔧 Corrections de Syntaxe

- Fautes de frappe (`readondly` → `readonly`, `classe` → `class`)
- Casse des identifiants (`book` → `Book`)
- Suppression des points-virgules superflus
- Ajout des accolades manquantes

### 📦 Dépendances Ajoutées

- `Microsoft.AspNetCore.Mvc.Testing`
- `Microsoft.EntityFrameworkCore`
- `Microsoft.EntityFrameworkCore.InMemory`

### 🏗️ Architecture Corrigée

- Conversion des top-level statements en classes traditionnelles
- Ajout des namespaces appropriés
- Configuration des contrôleurs (`app.MapControllers()`)
- Configuration EF avec base en mémoire

### 🧪 Tests d'Intégration

- Factory personnalisée pour les tests
- Base de données de test séparée
- Correction des références de types et namespaces

### 📝 Conventions de Code

- Respect de la convention camelCase pour les champs privés
- Noms de constructeurs corrects
- Types de retour appropriés
- Gestion asynchrone correcte

---

## 🎯 Résultat Final

- **BookApi** : Compilation réussie, tests passent (1/1)
- **TaskManagementApi** : Compilation réussie, tests passent (2/2)
- 0 erreur de compilation sur les deux projets
- APIs fonctionnelles avec endpoints REST complets
- Entity Framework configuré avec base de données en mémoire
- Tests d'intégration opérationnels

**Total des problèmes résolus : 15+ erreurs critiques 🚀**
