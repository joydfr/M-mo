## 🧠 Mise en place de la Couche Métier (Business Layer)

La **couche métier** contient toute la **logique de traitement** de l’application. Elle agit comme un **intermédiaire entre la présentation (UI) et les données (DAL)**, et permet de **centraliser les règles métiers**.

---

### ⚙️ Services

#### 🔍 Rôle des services :

Les services encapsulent la **logique fonctionnelle** :

- Calculs métiers
- Validation métier
- Orchestration des appels aux repositories

---

### 🧩 Étapes de mise en place

#### 1. Définir les interfaces (dans un dossier `Services/Interfaces`)

```csharp
public interface IMembreService
{
    IEnumerable<Membre> ObtenirTous();
    Membre ObtenirParId(int id);
    void Creer(Membre membre);
    void Modifier(Membre membre);
    void Supprimer(int id);
}
```

---

#### 2. Implémenter le service (dans Services/Impl ou similaire)

```csharp
public class MembreService : IMembreService
{
    private readonly IRepository<Membre> _repository;

    public MembreService(IRepository<Membre> repository)
    {
        _repository = repository;
    }

    public IEnumerable<Membre> ObtenirTous() => _repository.GetAll();

    public Membre ObtenirParId(int id) => _repository.GetById(id);

    public void Creer(Membre membre)
    {
        // Exemple de logique métier :
        if (string.IsNullOrEmpty(membre.Nom))
            throw new ArgumentException("Le nom est obligatoire.");

        _repository.Add(membre);
    }

    public void Modifier(Membre membre)
    {
        // Exemple de validation
        if (membre.Id <= 0)
            throw new ArgumentException("Identifiant invalide.");

        _repository.Update(membre);
    }

    public void Supprimer(int id)
    {
        if (id <= 0)
            throw new ArgumentException("Identifiant invalide.");

        _repository.Delete(id);
    }
}
```

---

#### 3. Injection de dépendances dans Program.cs ou Startup.cs

```csharp
builder.Services.AddScoped<IMembreService, MembreService>();
builder.Services.AddScoped(typeof(IRepository<>), typeof(Repository<>));
```

---

✅ **Résumé**

| Élément                   | But                                                  |
| ------------------------- | ---------------------------------------------------- |
| Interface de service      | Définir les opérations disponibles                   |
| Implémentation            | Contenir la logique métier                           |
| Appel aux repositories    | Accéder aux données via la DAL                       |
| DI (Dependency Injection) | Injecter les dépendances dans le contrôleur ou l’API |

---

📌 **Exemple d’utilisation dans un contrôleur API**

```csharp
[ApiController]
[Route("api/[controller]")]
public class MembresController : ControllerBase
{
    private readonly IMembreService _membreService;

    public MembresController(IMembreService membreService)
    {
        _membreService = membreService;
    }

    [HttpGet]
    public IActionResult GetAll() => Ok(_membreService.ObtenirTous());
}
```

---

🔁 **Checklist**

- Interface définie pour chaque service
- Logique métier placée dans les services (pas dans le contrôleur)
- Services connectés aux repositories
- Injection configurée dans le programme principal
