## 🧑‍💻 Interface Utilisateur (UI Layer)

### 🎯 Rôle

La **couche UI** est la **partie visible** de l’application. Elle permet à l’utilisateur de :

- Interagir avec l’application 👤
- Saisir des données via clavier, souris ou autres ⌨️
- Consulter des résultats ou messages visuels 📋

---

### 🧩 Selon le type de projet

| 🛠️ Technologie        | Description                        |
| --------------------- | ---------------------------------- |
| ASP.NET MVC           | UI web en Razor + contrôleurs      |
| Blazor WebAssembly    | SPA .NET côté client (comme React) |
| MAUI / WPF / WinForms | UI pour desktop                    |
| Console App           | UI en ligne de commande            |
| Angular / React / Vue | Front JS en mode API REST          |

---

## ⌨️ Gestion des Entrées / Sorties

### 📥 Entrées utilisateur (Input)

- Champs de formulaire (`input`, `select`, etc.)
- Fichiers uploadés
- Saisie clavier (console, WPF, Blazor…)
- Événements (`onClick`, `onChange`, etc.)

**Exemple ASP.NET Core Razor :**

```html
<form asp-action="Creer">
  <input asp-for="Nom" />
  <input asp-for="Email" />
  <button type="submit">Envoyer</button>
</form>
```

**Exemple Console App :**

```csharp
Console.WriteLine("Entrez votre nom : ");
string nom = Console.ReadLine();
```

---

### 📤 Sorties utilisateur (Output)

- Affichage de données dans des vues (tableaux, cartes, etc.)
- Messages d’erreur ou de confirmation
- Logs visibles
- Résultats en console ou en JSON (API)

**Exemple Blazor ou Razor :**

```html
<p>@Model.Nom</p>
```

**Exemple API REST :**

```json
{
  "id": 1,
  "nom": "Jody",
  "email": "jody@example.com"
}
```

---

## ✅ Checklist UI / Entrées / Sorties

- L’interface est claire et accessible 👁️
- Les saisies utilisateur sont validées côté client et serveur
- Les retours sont pertinents : messages, états, erreurs
- Le système gère les erreurs de saisie (ex. champs requis)
- Les données affichées sont issues de la logique applicative via DTO

---

## 🧠 Bonnes pratiques

| ✔️ Conseil                         | ✅ Pourquoi                      |
| ---------------------------------- | -------------------------------- |
| Utiliser des DTO pour l’UI         | Éviter d’exposer des entités     |
| Isoler la logique métier de la vue | Séparation des responsabilités   |
| Utiliser des validations côté UI   | Meilleure UX et sécurité         |
| Favoriser le feedback utilisateur  | UI plus compréhensible et fluide |
