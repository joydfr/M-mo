## 📦 DTO (Data Transfer Object)

### 🔍 Qu'est-ce qu'un DTO ?

Un **DTO** est un **objet simplifié** utilisé pour **transporter des données** entre les couches (API ↔ service ↔ client), sans exposer directement les **entités** de la base de données.

---

### 🎯 Pourquoi utiliser des DTOs ?

- ✅ **Sécurité** : on évite de renvoyer des champs sensibles (ex : mot de passe)
- ✅ **Contrôle** : on expose **uniquement** ce qui est nécessaire à l’extérieur
- ✅ **Flexibilité** : le format de sortie peut différer du format interne (ex : noms, types, structures)
- ✅ **Évolution** : un DTO peut évoluer sans impacter la base

---

### 📁 Exemple de `MembreDto`

```csharp
public class MembreDto
{
    public int Id { get; set; }
    public string Nom { get; set; }
    public string Email { get; set; }
}
```

---

## 🔄 Conversion DTO ↔️ Entités

Il existe plusieurs approches :

### 🛠️ 1. Conversion manuelle

#### 🔃 Entité vers DTO

```csharp
public static MembreDto ToDto(Membre membre)
{
    return new MembreDto
    {
        Id = membre.Id,
        Nom = membre.Nom,
        Email = membre.Email
    };
}
```

#### 🔁 DTO vers Entité

```csharp
public static Membre ToEntity(MembreDto dto)
{
    return new Membre
    {
        Id = dto.Id,
        Nom = dto.Nom,
        Email = dto.Email
        // Attention : pas de champs comme DateAdhesion si non exposé
    };
}
```

💡 Tu peux aussi les encapsuler dans une classe `MembreMapper`.

---

### 🤖 2. Conversion automatique avec AutoMapper

AutoMapper permet d’automatiser les conversions via un profil :

#### 📦 Installation

```bash
dotnet add package AutoMapper.Extensions.Microsoft.DependencyInjection
```

#### ⚙️ Configuration

```csharp
public class MappingProfile : Profile
{
    public MappingProfile()
    {
        CreateMap<Membre, MembreDto>().ReverseMap();
    }
}
```

#### 🔌 Enregistrement dans `Program.cs`

```csharp
builder.Services.AddAutoMapper(typeof(MappingProfile));
```

#### 🧪 Utilisation dans un contrôleur

```csharp
[HttpGet]
public IActionResult GetAll()
{
    var membres = _membreService.ObtenirTous();
    var membresDto = _mapper.Map<List<MembreDto>>(membres);
    return Ok(membresDto);
}
```

---

## ✅ Checklist DTO

- Créer un DTO pour chaque entité exposée
- Masquer les champs sensibles ou inutiles
- Ajouter une méthode de mapping manuelle ou un profil AutoMapper
- Utiliser les DTOs dans les contrôleurs/API (pas les entités directement !)
- Garder les DTOs à jour quand les besoins changent

---

## 📌 Résumé

| 🔹 Élément    | 📄 Rôle                                                                  |
| ------------- | ------------------------------------------------------------------------ |
| DTO           | Objet de transfert pour les données exposées                             |
| Mapper        | Convertit entre entités (interne) et DTO (externe)                       |
| Manuel / Auto | Conversion à la main ou via AutoMapper                                   |
| Utilisation   | Toujours côté contrôleur ou API (jamais exposer les entités directement) |

---

## 🧠 Logique Applicative (Application Layer)

### 🔍 Définition

La **logique applicative** (ou "logique de coordination") détermine **"ce que fait l’application"** :

- Elle orchestre les **cas d’usage**
- Elle **coordonne les appels** aux services, aux repositories, ou à d'autres composants métier
- Elle ne contient **ni logique métier pure**, ni accès direct à l’infrastructure

---

### 🧱 Position dans l’architecture

📌 Dans une architecture **N-tiers**, elle peut être intégrée à la couche métier.  
📌 Dans une architecture **Clean / Hexagonale**, elle est séparée en **"Application Layer"**.

---

### ⚙️ Exemples de tâches dans la logique applicative

- Authentifier un utilisateur via un service
- Gérer une commande (validation + enregistrement)
- Orchestrer plusieurs services pour un cas d’usage
- Préparer un DTO de réponse à partir de plusieurs sources

---

### 🧩 Exemple C#

#### Cas d’usage : Créer un membre

```csharp
public class CreerMembreHandler
{
    private readonly IMembreService _membreService;
    private readonly IEmailService _emailService;

    public CreerMembreHandler(IMembreService membreService, IEmailService emailService)
    {
        _membreService = membreService;
        _emailService = emailService;
    }

    public void Executer(MembreDto membreDto)
    {
        // 1. Mapper DTO → Entité
        var membre = MembreMapper.ToEntity(membreDto);

        // 2. Logique métier via service
        _membreService.Creer(membre);

        // 3. Action secondaire
        _emailService.EnvoyerEmailBienvenue(membre.Email);
    }
}
```

---

📦 Structure typique en Clean Architecture

```
/Application
  /UseCases
    - CreerMembreHandler.cs
  /DTOs
    - MembreDto.cs
```

---

✅ Avantages

- Centralisation des cas d’usage : chaque scénario est clair, explicite et isolé
- Test unitaire facile : chaque handler est indépendant
- Pas de mélange de logique technique et métier

---

✅ Checklist : Logique applicative

- Chaque cas d’usage a une classe dédiée (ex: CreerMembreHandler)
- Orchestration claire entre DTO / Services / Repositories
- Logique métier conservée dans les services métier
- Conversion DTO ↔ entités gérée proprement
- Facilement testable (mock des services)

---

📌 À retenir

| 🔹 Élément          | 📄 Rôle                                         |
| ------------------- | ----------------------------------------------- |
| Logique applicative | Définit ce que l’appli fait dans un cas d’usage |
| Services métiers    | Gèrent les règles métier pures                  |
| Contrôleurs/API     | Reçoivent la requête, délèguent à l’application |
