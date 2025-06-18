# 🐳 Mémo Docker pour une application .NET (C#)

---

## 🔨 1. `docker build`

```bash
docker build -t mon-app-dotnet .
```

| Élément | Description                                  |
| ------- | -------------------------------------------- |
| `-t`    | Tag de l’image (ex: `mon-app-dotnet:latest`) |
| `.`     | Dossier courant = contexte de build          |

---

## 📦 2. Contexte de build

Docker envoie tous les fichiers du dossier `.` au démon Docker pour construire l’image.

Exemple de structure typique :

```
.
├── Dockerfile
├── monApp.csproj
├── Program.cs
└── ...
```

> ⚠️ Si tu lances `docker build` ailleurs, il ne trouvera pas ton `.csproj` → erreur.

---

## ⚙️ 3. Cache Docker et .NET

Chaque ligne du Dockerfile est une étape. Docker ne la relance que si un fichier utilisé à cette étape change.

---

## Exemple de Dockerfile multi-étapes .NET

```dockerfile
# Étape 1 : Build
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /src

COPY monApp.csproj ./
RUN dotnet restore

COPY . ./
RUN dotnet publish -c Release -o /app/publish

# Étape 2 : Runtime
FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS runtime
WORKDIR /app
COPY --from=build /app/publish .
ENTRYPOINT ["dotnet", "monApp.dll"]
```

---

## 🚀 Explication des étapes

| Étape | Instruction              | Description                                        |
| ----- | ------------------------ | -------------------------------------------------- |
| 1     | `COPY monApp.csproj ./`  | Permet de cacher le restore si seul le code change |
| 2     | `RUN dotnet restore`     | Installe les dépendances NuGet (comme pip install) |
| 3     | `COPY . ./`              | Copie le reste du code (.cs, .json, etc.)          |
| 4     | `RUN dotnet publish ...` | Compile le projet pour la prod                     |
| 5     | `COPY --from=build ...`  | Multi-stage build : copie binaire final            |

---

## ✅ Pourquoi cet ordre ?

- Si tu modifies uniquement le code (ex : `Program.cs`), Docker ne refera pas :
  - `dotnet restore` ✅ (si `.csproj` inchangé)
  - ni l’installation de l’image de base ✅
- → Build plus rapide ⚡

---

## 📏 Optimiser la taille de l’image

- Multi-stage build : l’étape build (SDK .NET) n’est pas dans l’image finale.
- L’image finale contient uniquement le runtime et les binaires compilés.
- 🪶 Résultat : image plus légère, rapide et propre pour la prod.

---

## 🔁 Résumé des bonnes pratiques

| Bonne pratique                       | Pourquoi ?                          |
| ------------------------------------ | ----------------------------------- |
| `COPY .csproj` puis `dotnet restore` | Bénéficier du cache                 |
| `COPY .` ensuite                     | Ne pas casser le cache inutilement  |
| `dotnet publish` dédié               | Binaire optimisé pour prod          |
| Multi-stage build                    | Image finale plus légère            |
| Utiliser `.dockerignore`             | Ne pas envoyer de fichiers inutiles |

---

## 🧠 Mémo visuel .NET

| Dockerfile (ordre)    | Cache ?                  |
| --------------------- | ------------------------ |
| 1. FROM dotnet/sdk    | Oui (si tag stable)      |
| 2. COPY \*.csproj     | Oui (si pas modifié)     |
| 3. RUN dotnet restore | Oui (si csproj inchangé) |
| 4. COPY reste du code | Rejoué si code changé    |
| 5. RUN dotnet publish | Rejoué si code changé    |
| 6. FROM dotnet/aspnet | Oui                      |
| 7. COPY depuis build  | Toujours fait            |
| 8. ENTRYPOINT         | Exécuté à l’exécution    |

---

## ℹ️ Pourquoi le `.` dans `docker build` est essentiel

Le `.` à la fin de la commande `docker build` indique à Docker d’utiliser le dossier courant comme **contexte de build**. Cela signifie que tous les fichiers de ce dossier (et sous-dossiers) seront accessibles pendant la construction de l’image.

### Exemple

```bash
docker build -t mon-image .
```

- Le `.` = “prends tous les fichiers ici comme contexte”
- Docker lit le `Dockerfile` et peut copier d’autres fichiers (avec `COPY`, `ADD`, etc.)

### Changer le contexte

Tu peux spécifier un autre dossier comme contexte :

```bash
docker build -t autre-image ../autre-projet
```

Ici, Docker utilisera les fichiers de `../autre-projet` pour construire l’image.

### Attention aux erreurs

Si tu oublies le `.` ou ne précises pas de contexte, Docker ne saura pas où chercher les fichiers et affichera une erreur.

```bash
docker build -t mon-image      # ❌ Erreur probable : contexte manquant
```

---

> **Astuce :** Pour bien comprendre, teste avec deux dossiers différents et observe quels fichiers Docker “voit” selon le contexte choisi.
