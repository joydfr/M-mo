## 🧭 Implémentation du Pattern MVC (Model-View-Controller)

Le **pattern MVC** sépare une application en trois parties :

- **M (Model)** : les données et la logique métier
- **V (View)** : l’interface utilisateur (HTML, UI, console…)
- **C (Controller)** : l’orchestrateur des actions et de la navigation

---

### 📦 1. Création des Modèles

#### 🧱 Définition des entités

Les **entités** représentent les objets du domaine (ex: `Membre`, `Produit`, `Commande`).  
Elles peuvent contenir des **attributs**, des **relations**, et parfois des **règles métier simples**.

```csharp
public class Membre
{
    public int Id { get; set; }
    public string Nom { get; set; }
    public string Email { get; set; }

    // Logique métier intégrée
    public bool EstEmailValide()
        => Email.Contains("@");
}
```

---

🧠 **Logique métier**

Elle peut être portée par :

- des méthodes dans l’entité si elle est simple
- des services métier externes si elle est plus complexe

```csharp
public class MembreService
{
    public bool PeutCréer(Membre membre)
    {
        return !string.IsNullOrEmpty(membre.Nom) && membre.EstEmailValide();
    }
}
```

---

### 🖼️ 2. Création des Vues

#### 🎨 Templates

Les vues sont des fichiers qui décrivent le rendu HTML ou interface.

**Exemples :**

- Razor (.cshtml) en ASP.NET MVC
- XAML en WPF
- Blazor pour composants UI interactifs

#### 👁️ Rendu des données

```html
<!-- Exemple Razor .cshtml -->
<h2>Détails du membre</h2>
<p>Nom : @Model.Nom</p>
<p>Email : @Model.Email</p>
```

Les données du Modèle sont injectées dans le template.

---

### 🧭 3. Création des Contrôleurs

#### 🗺️ Routage

Les contrôleurs reçoivent les requêtes HTTP et déclenchent les actions :

```csharp
[Route("membres")]
public class MembreController : Controller
{
    [HttpGet("{id}")]
    public IActionResult Details(int id)
    {
        var membre = _service.ObtenirParId(id);
        return View(membre);
    }
}
```

ASP.NET Core configure le routage avec `[Route]`, `[HttpGet]`, `[HttpPost]`, etc.

---

#### 🧪 Gestion des actions

Une action est une méthode publique qui gère une requête et renvoie une vue ou un résultat :

```csharp
[HttpPost]
public IActionResult Creer(Membre model)
{
    if (!ModelState.IsValid)
        return View(model);

    _service.Creer(model);
    return RedirectToAction("Index");
}
```

---

### 🔁 Comparaison MVC vs MVVM

| 🧩 Critère                 | MVC (Web / Console)                 | MVVM (Desktop / SPA)                             |
| -------------------------- | ----------------------------------- | ------------------------------------------------ |
| 🔄 Communication           | Contrôleur → Vue                    | Vue ↔ ViewModel (liaison 2 sens)                 |
| 🧠 Logique de présentation | Dans le contrôleur                  | Dans le ViewModel                                |
| 🧱 Vue                     | Passive                             | Active (bind aux propriétés)                     |
| 💬 Événements              | Contrôleur gère les clics / actions | Liaison de commande (Command)                    |
| 🔧 Technologies typiques   | ASP.NET MVC, Laravel, Symfony       | WPF, Xamarin, Blazor, Angular, React (MVVM-like) |
| 🔍 Binding UI ↔ Données    | Manuel ou Razor                     | Automatique via data-binding                     |

---

### ✅ Checklist MVC

- Les Modèles sont clairs et centrés sur le domaine
- Les Vues sont responsables uniquement de l’affichage
- Les Contrôleurs agissent comme intermédiaires sans logique métier
- Le routage est défini proprement
- Le code est testable et maintenable via la séparation des rôles

---
