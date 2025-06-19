# 🧱 Mémo – Structure d’un Dockerfile (avec exemple C# / ASP.NET Core)

Un `Dockerfile` est un fichier texte qui décrit **étape par étape** comment construire une **image Docker personnalisée**.

---

## 📐 Structure typique d’un Dockerfile

```dockerfile
# 1️⃣ Image de base
FROM <image-de-base>

# 2️⃣ Mainteneur (optionnel)
LABEL maintainer="votre.nom@email.com"

# 3️⃣ Variables d’environnement (optionnel)
ENV ENV_VAR=value

# 4️⃣ Ajout de fichiers dans l’image
COPY <src> <dest>
ADD <src> <dest>

# 5️⃣ Exécution de commandes dans l’image
RUN <commande shell>

# 6️⃣ Définir le dossier de travail
WORKDIR /chemin

# 7️⃣ Exposer un port
EXPOSE <port>

# 8️⃣ Définir la commande par défaut
CMD ["exécutable", "arg1", "arg2"]

# (alternative à CMD)
ENTRYPOINT ["exécutable"]
```

---

🧪 **Exemple concret – Application ASP.NET Core**

```dockerfile
# Étape 1 : Build
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /app

# Copier les fichiers .csproj et restaurer les dépendances
COPY *.csproj ./
RUN dotnet restore

# Copier le reste des fichiers et compiler l'app
COPY . ./
RUN dotnet publish -c Release -o out

# Étape 2 : Runtime
FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS runtime
WORKDIR /app
COPY --from=build /app/out .

# Exposer le port (ex. 5000)
EXPOSE 5000

# Démarrer l'application
ENTRYPOINT ["dotnet", "MonApp.dll"]
```

🗂 Remplace `MonApp.dll` par le nom de ton projet .NET compilé.

---

🧠 **Différences clés**

| Instruction | Description                                                |
| ----------- | ---------------------------------------------------------- |
| RUN         | Exécute une commande pendant le build                      |
| CMD         | Définit la commande par défaut à l’exécution               |
| ENTRYPOINT  | Définit la commande principale (non remplaçable)           |
| COPY vs ADD | ADD peut extraire une archive .tar.gz, COPY non            |
| WORKDIR     | Définit le répertoire de travail pour les étapes suivantes |

---

🔥 **Bonnes pratiques pour .NET**

- ✅ Utiliser un build multi-étapes pour réduire la taille finale
- ✅ Garder la phase runtime aussi légère que possible
- ✅ Utiliser des images officielles de Microsoft (mcr.microsoft.com)
- ✅ Ajouter un fichier `.dockerignore` :

```
bin/
obj/
*.user
```

---

🧪 **Tester votre Dockerfile**

```sh
docker build -t monapp-dotnet .
docker run -d -p 5000:5000 --name appdotnet monapp-dotnet
```

👉 Ensuite, accède à ton app via http://localhost:5000

---

📚 **Pour aller plus loin**

- 🐳 Docker + .NET : https://learn.microsoft.com/dotnet/core/docker/
- 🎓 Labs interactifs Docker : https://labs.play-with-docker.com/

---
