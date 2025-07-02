# 🧪 Mémo – Exercices de tests d’intégration en C# (avec réponses)

---

## 🔰 Exercice 1 – Premier test d’intégration : GET /api/taskmanagements

### 🎯 Objectif

Découvrir WebApplicationFactory et effectuer une requête HTTP simple sur l’API.

### 📝 Énoncé

Crée un test d’intégration qui vérifie que la route GET /api/taskmanagements renvoie un statut 200 OK et un contenu application/json.

### ✅ Réponse

```csharp
[Fact]
public async Task GetTasks_ReturnSuccessAndCorrectContentType()
{
    var response = await _client.GetAsync("/api/taskmanagements");
    Assert.Equal(HttpStatusCode.OK, response.StatusCode);
    Assert.Equal("application/json; charset=utf-8", response.Content.Headers.ContentType?.ToString());
}
```

### 🧠 Notions

- WebApplicationFactory
- HttpClient.GetAsync
- Assert.Equal

---

## 🚀 Exercice 2 – Créer une tâche via POST

### 🎯 Objectif

Tester la route POST /api/taskmanagements avec des données JSON.

### 📝 Énoncé

Crée un test qui envoie une tâche via POST et vérifie que la tâche est bien créée, avec un titre identique.

### ✅ Réponse

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

### 🧠 Notions

- HttpClient.PostAsJsonAsync
- ReadFromJsonAsync<T>()
- response.EnsureSuccessStatusCode()

---

## 🧱 Exercice 3 – Utiliser une base de données InMemory

### 🎯 Objectif

Découvrir comment isoler les tests avec une base de données EF Core InMemory.

### 📝 Énoncé

Configure l’API pour qu’elle utilise une base de données EF Core InMemory uniquement pour les tests.

### ✅ Réponse

```csharp
public class CustomWebApplicationFactory<TStartup> : WebApplicationFactory<TStartup> where TStartup : class
{
    protected override void ConfigureWebHost(IWebHostBuilder builder)
    {
        builder.ConfigureServices(services =>
        {
            // Supprimer le DbContext déjà enregistré
            var descriptor = services.SingleOrDefault(d =>
                d.ServiceType == typeof(DbContextOptions<AppDbContext>));
            if (descriptor != null)
                services.Remove(descriptor);

            // Remplacer par un DbContext InMemory
            services.AddDbContext<AppDbContext>(options =>
                options.UseInMemoryDatabase("TestDb"));
        });
    }
}
```

Et ensuite dans les tests :

```csharp
public class TaskManagementApiIntegrationTests : IClassFixture<CustomWebApplicationFactory<Program>>
{
    private readonly HttpClient _client;

    public TaskManagementApiIntegrationTests(CustomWebApplicationFactory<Program> factory)
    {
        _client = factory.CreateClient();
    }

    // tests ici
}
```

### 🧠 Notions

- IServiceCollection.Remove
- UseInMemoryDatabase
- Remplacement du contexte EF Core à des fins de test

---

## 🧪 Exercice 4 (optionnel) – Tester la récupération après insertion

### 🎯 Objectif

Tester que les données postées sont bien persistées dans le contexte de test.

### 📝 Énoncé

Poste une tâche, puis appelle GET pour vérifier qu’elle est bien présente dans la réponse.

### ✅ Réponse (à adapter selon l’implémentation réelle)

```csharp
[Fact]
public async Task PostAndThenGetTask_ReturnInsertedTask()
{
    var newTask = new { Title = "Integration Test Task", Done = false };
    var postResponse = await _client.PostAsJsonAsync("/api/taskmanagements", newTask);
    postResponse.EnsureSuccessStatusCode();

    var getResponse = await _client.GetAsync("/api/taskmanagements");
    getResponse.EnsureSuccessStatusCode();

    var tasks = await getResponse.Content.ReadFromJsonAsync<List<TaskItem>>();
    Assert.Contains(tasks!, t => t.Title == "Integration Test Task" && t.Done == false);
}
```

### 🧠 Notions

- Enchaînement POST + GET
- Vérification de la persistance en mémoire
- Assert.Contains

---

## 📚 Bonus – Références utiles

- 📘 Microsoft Docs – Integration tests in ASP.NET Core
- 📘 EF Core InMemory Provider
