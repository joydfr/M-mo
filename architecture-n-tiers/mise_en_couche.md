## 🖼️ Couche Présentation (Presentation Layer)

### 🎯 Rôle

La **couche présentation** est la **porte d’entrée de l’application**.  
Elle gère l’**interface utilisateur** (dans un projet web MVC) ou l’**API REST** (dans une Web API), et transmet les requêtes vers la logique applicative.

---

### 🧰 Outils typiques

- 🌐 ASP.NET Core MVC
- 🔁 ASP.NET Core Web API
- 🧪 Razor / Blazor (dans les apps UI)

---

## 🧩 Contrôleurs

### 📍 Rôle des contrôleurs

- Reçoivent les **requêtes HTTP**
- Appellent les **handlers ou services**
- Transforment les **données en réponse (DTO)**
- Gèrent les **codes HTTP** (`200 OK`, `404 Not Found`, `400 BadRequest`, etc.)

---

### 🧪 Exemple d’un contrôleur API

```csharp
[ApiController]
[Route("api/[controller]")]
public class MembresController : ControllerBase
{
    private readonly IMembreService _membreService;
    private readonly IMapper _mapper;

    public MembresController(IMembreService membreService, IMapper mapper)
    {
        _membreService = membreService;
        _mapper = mapper;
    }

    [HttpGet]
    public IActionResult GetAll()
    {
        var membres = _membreService.ObtenirTous();
        var membresDto = _mapper.Map<List<MembreDto>>(membres);
        return Ok(membresDto);
    }

    [HttpPost]
    public IActionResult Creer([FromBody] MembreDto dto)
    {
        if (!ModelState.IsValid)
            return BadRequest(ModelState);

        var membre = _mapper.Map<Membre>(dto);
        _membreService.Creer(membre);

        return CreatedAtAction(nameof(GetAll), new { id = membre.Id }, dto);
    }
}
```

---

✅ **Checklist Contrôleurs**

- Utilise `[ApiController]` et `[Route]`
- Ne contient aucune logique métier
- Utilise des DTO en entrée et en sortie
- Renvoie des codes HTTP adaptés (200, 201, 400, etc.)
- Valide les données via `[FromBody]` + annotations

---

🧭 **Bonne pratique : fine séparation**

| Couche        | Rôle                          |
| ------------- | ----------------------------- |
| Présentation  | Gère la requête et la réponse |
| Application   | Coordonne l’action à réaliser |
| Métier        | Applique la logique métier    |
| Données (DAL) | Lit/écrit dans la base        |

---

🧰 **À noter pour une UI Web (MVC)**

Dans une architecture MVC (pas API), les contrôleurs retournent des `ViewResult` :

```csharp
public IActionResult Index()
{
    var membres = _membreService.ObtenirTous();
    return View(membres); // Passe les données à la vue .cshtml
}
```

---
