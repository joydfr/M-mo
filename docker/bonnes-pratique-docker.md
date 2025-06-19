# 🐳 Mémo – Bonnes pratiques Docker

---

## 🔐 1. Sécurité des images

- **Privilégier les images officielles et stables**
  ```dockerfile
  FROM python:3.12-slim
  FROM mcr.microsoft.com/dotnet/aspnet:8.0
  ```
- **Éviter `latest` en production**  
   Utiliser une version précise :
  ```dockerfile
  FROM node:20.12.2-alpine
  ```
- **Supprimer les outils/fichiers inutiles**
  ```dockerfile
  RUN apt-get update && apt-get install -y curl \
          && rm -rf /var/lib/apt/lists/*
  ```
- **Utiliser un utilisateur non-root**
  ```dockerfile
  RUN adduser -D appuser
  USER appuser
  ```

---

## 📦 2. Optimisation des layers

- **Grouper les commandes RUN**

  ```dockerfile
  # Mauvais
  RUN apt-get update
  RUN apt-get install -y curl

  # Meilleur
  RUN apt-get update && apt-get install -y curl && rm -rf /var/lib/apt/lists/*
  ```

- **Copier stratégiquement pour le cache**

  ```dockerfile
  COPY monApp.csproj ./
  RUN dotnet restore

  COPY . ./
  RUN dotnet publish
  ```

- **Nettoyer les fichiers temporaires**
  ```dockerfile
  RUN rm -rf /tmp/* /var/tmp/*
  ```

---

## 📝 3. Documentation du Dockerfile

- **Ajouter des commentaires**

  ```dockerfile
  # Image de base officielle .NET SDK
  FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build

  # Définir le répertoire de travail
  WORKDIR /src

  # Copier uniquement le projet (optimise le cache)
  COPY monApp.csproj ./
  RUN dotnet restore
  ```

- **Rendre le Dockerfile lisible**
  - Espacer les blocs logiques
  - Garder uniquement ce qui est nécessaire

---

## 📌 4. Gestion des versions

- **Taguer correctement les images**
  ```sh
  docker build -t mon-app:1.2.0 .
  docker build -t mon-app:latest .
  ```
- **Versionner le Dockerfile avec Git**
  ```dockerfile
  LABEL version="1.2.0" maintainer="jody@example.com"
  ```
- **Ne pas publier une image instable sous un tag stable**
  ```sh
  docker push mon-app:dev      # OK
  docker push mon-app:latest   # À éviter si instable
  ```

---

## 🧠 Résumé

| Bonne pratique                | Pourquoi ?                  |
| ----------------------------- | --------------------------- |
| Images officielles et taguées | Stabilité et sécurité       |
| Multi-layer optimisé          | Cache + taille réduite      |
| Non-root user                 | Réduit le risque d’attaques |
| Dockerfile commenté           | Lisibilité et maintenance   |
| Tags versionnés               | Déploiements reproductibles |

---

## 💻 Exemple – Dockerfile C# .NET (avec bonnes pratiques)

```dockerfile
# -------------------------
# 🧱 Étape 1 : Build
# -------------------------
# Utiliser une image de base officielle avec version explicite
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build

# Définir le répertoire de travail
WORKDIR /src

# Copier uniquement le fichier .csproj pour profiter du cache Docker
COPY MonApp.csproj ./
RUN dotnet restore

# Copier le reste des fichiers de code
COPY . ./
RUN dotnet publish -c Release -o /app/publish

# -------------------------
# 🏃 Étape 2 : Runtime (image plus légère)
# -------------------------
FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS runtime

# Définir un répertoire de travail
WORKDIR /app

# Copier le résultat de l'étape précédente
COPY --from=build /app/publish .

# Utilisateur non-root (facultatif mais recommandé si applicable)
# RUN adduser --disabled-password --gecos '' appuser && chown -R appuser /app
# USER appuser

# Exposer un port (optionnel selon ton appli)
EXPOSE 80

# Ajouter des métadonnées
LABEL maintainer="jody@example.com" \
    version="1.0.0"

# Utiliser ENTRYPOINT avec la syntaxe JSON recommandée
ENTRYPOINT ["dotnet", "MonApp.dll"]
```

---

### 📁 Arborescence projet (exemple)

```
MonApp/
├── Dockerfile
├── MonApp.csproj
├── Program.cs
└── ...
```

---

### 🛠️ Commandes associées

```sh
# Construction de l’image (le point = contexte actuel)
docker build -t monapp:1.0.0 .

# Lancer un conteneur
docker run -p 8080:80 monapp:1.0.0
```

---

### 🔁 Bonus – Cache Docker

Docker lit le Dockerfile de haut en bas, et reconstruit à partir de la première ligne modifiée.

Exemple :

1. Tu modifies `Program.cs` ➜ Docker reconstruit après `COPY . ./`
2. Tu modifies `MonApp.csproj` ➜ Docker reconstruit même `dotnet restore`

D’où l’intérêt de :

- copier les fichiers de projet (.csproj) avant le code source
- séparer les étapes pour maximiser le cache

---
