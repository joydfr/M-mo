# 🧠 MÉMO DOCKER – Exercice de base

## 📁 Structure du projet

```
~/testdocker/
├── Dockerfile
├── hello.txt
└── fichier.tar.gz
```

---

## 🛠️ Fichier Dockerfile utilisé

```dockerfile
FROM alpine                           # Utilise une image de base (Alpine Linux)
WORKDIR /app                          # Définit le répertoire de travail dans l'image
COPY hello.txt /app/                  # Copie un fichier depuis le contexte vers l'image
ADD fichier.tar.gz /app/              # Ajoute et extrait automatiquement une archive
RUN apk add --no-cache curl           # Exécute une commande (ici : installation de curl)
ENV NOM=Jody                          # Définit une variable d'environnement
EXPOSE 8080                           # Documente un port exposé (pas obligatoire)
ENTRYPOINT ["echo"]                   # Commande principale lancée (non modifiable par `docker run`)
CMD ["Bonjour Docker"]                # Paramètre par défaut passé à ENTRYPOINT (modifiable)
```

---

## 🧪 Commandes Terminal utilisées

### 1. Créer le dossier de travail

```sh
mkdir ~/testdocker
cd ~/testdocker
```

### 2. Créer les fichiers nécessaires

```sh
echo "Bonjour depuis hello.txt" > hello.txt
touch fichier.tar.gz
```

### 3. Créer un Dockerfile

```sh
nano Dockerfile  # ou `code Dockerfile` si tu es dans VS Code
```

### 4. Construire l’image Docker

```sh
docker build -t mon-image-test .
```

- `-t mon-image-test` : nomme l’image mon-image-test
- `.` : indique que le contexte de build est le répertoire courant

### 5. Lancer un conteneur depuis l’image

```sh
docker run mon-image-test
```

**Résultat attendu :**

```
Bonjour Docker
```

---

## 🧾 Récap des instructions Dockerfile

| Instruction  | Rôle                                                                       |
| ------------ | -------------------------------------------------------------------------- |
| `FROM`       | Spécifie l’image de base utilisée                                          |
| `WORKDIR`    | Définit le dossier courant dans l’image (équivaut à `cd`)                  |
| `COPY`       | Copie un fichier depuis ton disque dans l’image                            |
| `ADD`        | Comme COPY mais peut décompresser les archives (.tar.gz)                   |
| `RUN`        | Exécute une commande pendant la construction de l’image                    |
| `ENV`        | Définit une variable d’environnement disponible dans l’image               |
| `EXPOSE`     | Documente un port que le conteneur écoutera (optionnel)                    |
| `ENTRYPOINT` | Commande principale du conteneur (non surchargée sauf avec `--entrypoint`) |
| `CMD`        | Arguments par défaut pour ENTRYPOINT, modifiables par `docker run`         |

---
