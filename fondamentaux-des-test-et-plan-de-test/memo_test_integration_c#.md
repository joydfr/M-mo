# 🧠 Mémo – Tests d’intégration en C# avec ASP.NET Core

---

## 🎯 Objectif

Réaliser des tests d’intégration sur une API ASP.NET Core :

- en simulant l’application réelle via `WebApplicationFactory`
- en utilisant `HttpClient` pour envoyer des requêtes HTTP
- en isolant la base de données grâce à une InMemoryDatabase (EF Core)

---

## 🧩 Structure des projets

```
/TaskManagementApi           → Projet principal ASP.NET Core API
/TaskManagementApi.Tests     → Projet de tests
TaskManagementApi.sln        → Solution liant les deux projets
```

---

## 1. ✅ Configuration de base

```bash
dotnet new sln -n TaskManagementApi
dotnet sln TaskManagementApi.sln add TaskManagementApi/TaskManagementApi.csproj
dotnet sln TaskManagementApi.sln add TaskManagementApi.Tests/TaskManagementApi.Tests.csproj
```

---

## 2. 🧪 Test d’intégration de base

```csharp
public class TaskManagementApiIntegrationTests : IClassFixture<WebApplicationFactory<Program>>
{
    private readonly HttpClient _client;

    public TaskManagementApiIntegrationTests(WebApplicationFactory<Program> factory)
    {
        _client = factory.CreateClient();
    }

    [Fact]
    public async Task GetTasks_ReturnSuccessAndCorrectContentType()
    {
        var response = await _client.GetAsync("/api/taskmanagements");
        Assert.Equal(HttpStatusCode.OK, response.StatusCode);
        Assert.Equal("application/json; charset=utf-8", response.Content.Headers.ContentType?.ToString());
    }
}
```

---

## 3. 🧰 CustomWebApplicationFactory (avec DB InMemory)

```csharp
public class CustomWebApplicationFactory<TStartup> : WebApplicationFactory<TStartup> where TStartup : class
{
    protected override void ConfigureWebHost(IWebHostBuilder builder)
    {
        builder.ConfigureServices(services =>
        {
            // Supprimer le DbContext existant
            var descriptor = services.SingleOrDefault(d =>
                d.ServiceType == typeof(DbContextOptions<AppDbContext>));
            if (descriptor != null)
                services.Remove(descriptor);

            // Ajouter un DbContext InMemory
            services.AddDbContext<AppDbContext>(options =>
                options.UseInMemoryDatabase("TestDb"));
        });
    }
}
```

---

## 4. ✍️ Exemple de test avec POST

```csharp
[Fact]
public async Task PostTask_ReturnCreatedTask()
{
    var task = new { Title = "Test Task", Done = false };

    var response = await _client.PostAsJsonAsync("/api/taskmanagements", task);

    response.EnsureSuccessStatusCode();
    var createdTask = await response.Content.ReadFromJsonAsync<TaskItem>();

    Assert.Equal("Test Task", createdTask!.Title);
    Assert.False(createdTask.Done);
}
```

---

## 5. 📦 Modèle de tâche (API)

```csharp
public class TaskItem
{
    public int Id { get; set; }
    public string Title { get; set; } = string.Empty;
    public bool Done { get; set; }
}
```

---

## 6. 🗃 Exemple de AppDbContext (API)

```csharp
public class AppDbContext : DbContext
{
    public AppDbContext(DbContextOptions<AppDbContext> options) : base(options) { }

    public DbSet<TaskItem> TaskItems => Set<TaskItem>();
}
```

---

## 7. 🚀 Lancer les tests

```bash
dotnet test TaskManagementApi.sln
```

---

## 🧩 Récapitulatif des outils utilisés

| Outil / bibliothèque             | Utilité                                  |
| -------------------------------- | ---------------------------------------- |
| xUnit                            | Framework de test                        |
| Microsoft.AspNetCore.Mvc.Testing | Fournit WebApplicationFactory            |
| HttpClient                       | Envoie des requêtes à l’API              |
| EF Core InMemory                 | Simule la base de données                |
| IClassFixture<>                  | Partage l’instance WebApplicationFactory |

---

## 🧠 Ce qu’il faut retenir

- Un test d’intégration lance l’application réelle en mémoire pour tester le comportement global (sans mock).
- Grâce à WebApplicationFactory et à la DB InMemory, on évite de toucher à une base réelle, tout en testant l’application “comme en vrai”.
- C’est utile pour tester des contrôleurs, la logique métier, ou des appels HTTP end-to-end, tout en conservant des tests rapides et isolés.
