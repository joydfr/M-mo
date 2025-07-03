# 🏗️ Mémo : Implémentation d'une Architecture N-Tiers

## 📚 Qu'est-ce que l'architecture N-Tiers ?

L'architecture N-tiers est une **séparation logique** du code d'une application en plusieurs **couches indépendantes**, pour améliorer la **maintenabilité**, la **testabilité** et la **réutilisabilité**.

### 🔍 Les principales couches :

- 🎨 **Présentation** (UI) : Interface utilisateur
- 🧠 **Métier** (Business Logic) : Règles métiers
- 🗃️ **Données** (Data Access Layer) : Communication avec la base de données

---

## 🛠️ Implémentation de la couche Données

### 📁 1. Mise en place de la Couche Données

- Crée un **projet** ou un **dossier** dédié (ex. `MonApp.Data`).
- Référence-le dans les autres projets via une dépendance.

---

### 🔄 2. Accès aux Données / Repository

🔸 **But** : Interagir avec la base de données **sans exposer directement** les technologies utilisées (ex : Entity Framework, SQL brut, Dapper...).

#### 🧱 Étapes :

- Créer une **interface générique** `IRepository<T>` :

  ```csharp
  public interface IRepository<T>
  {
          IEnumerable<T> GetAll();
          T GetById(int id);
          void Add(T entity);
          void Update(T entity);
          void Delete(int id);
  }
  ```

- Implémenter cette interface :

  ```csharp
  public class Repository<T> : IRepository<T> where T : class
  {
          private readonly DbContext _context;
          private readonly DbSet<T> _dbSet;

          public Repository(DbContext context)
          {
                  _context = context;
                  _dbSet = context.Set<T>();
          }

          public IEnumerable<T> GetAll() => _dbSet.ToList();
          public T GetById(int id) => _dbSet.Find(id);
          public void Add(T entity) => _dbSet.Add(entity);
          public void Update(T entity) => _dbSet.Update(entity);
          public void Delete(int id)
          {
                  var entity = _dbSet.Find(id);
                  if (entity != null) _dbSet.Remove(entity);
          }
  }
  ```

- Injecter le repository via le container DI :
  ```csharp
  services.AddScoped(typeof(IRepository<>), typeof(Repository<>));
  ```

---

### 🧬 3. Modèles de Données / Entités

🔸 But : Représenter les tables de la base sous forme d’objets C#.

🧱 Étapes :

- Créer une classe pour chaque entité :

  ```csharp
  public class Membre
  {
          public int Id { get; set; }
          public string Nom { get; set; }
          public string Email { get; set; }
          public DateTime DateAdhesion { get; set; }
  }
  ```

- Ajouter les annotations de données si nécessaire (`[Key]`, `[Required]`, `[ForeignKey]`, etc.).
- Utiliser DbContext pour déclarer les entités :

  ```csharp
  public class AppDbContext : DbContext
  {
          public DbSet<Membre> Membres { get; set; }

          public AppDbContext(DbContextOptions<AppDbContext> options)
                  : base(options) { }
  }
  ```

---

✅ **Résumé visuel**

| 📌 Éléments                | 📄 À faire                                  |
| -------------------------- | ------------------------------------------- |
| 📁 Couche Données          | Créer un projet dédié                       |
| 🧩 Repository              | Interface + Implémentation                  |
| 🧬 Entités                 | Modèles C# représentant les tables          |
| 🧠 DbContext               | Configuration de l’accès DB                 |
| 🧪 Injection de dépendance | Configuration dans Startup.cs ou Program.cs |

---

🧪 **Bonus : Vérification**

- La couche données est séparée et réutilisable
- Les entités sont bien mappées à la BDD
- Le DbContext est bien injecté
- Les repositories sont bien abstraits et testables

---
