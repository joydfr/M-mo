# 🧑‍🏫 Cours Docker – Niveau avancé

## ✅ 1. Mise en pratique globale

### 📦 Création d’une application multi-conteneurs

**Objectif** : Comprendre comment découper une application en plusieurs conteneurs collaboratifs.

**Pourquoi ?**  
Docker favorise l’architecture microservices : chaque conteneur a un rôle précis, ce qui rend l’application modulaire, maintenable et évolutive.

**Comment faire ?**

1. Crée un dossier projet :

   ```bash
   mkdir mon-app && cd mon-app
   ```

2. Crée un fichier `docker-compose.yml` pour définir les services :
   ```yaml
   version: "3.9"
   services:
     frontend:
       build: ./frontend
     backend:
       build: ./backend
     db:
       image: postgres
     cache:
       image: redis
   ```

> 💡 **Astuce** : Ajoute un service à la fois et vérifie le fonctionnement à chaque étape.

---

### 🔧 Stack de développement

#### 🎨 Application Frontend (exemple React)

`frontend/Dockerfile` :

```dockerfile
FROM node:20-alpine AS builder
WORKDIR /app
COPY . .
RUN npm install && npm run build

FROM nginx:alpine
COPY --from=builder /app/dist /usr/share/nginx/html
```

#### ⚙️ API Backend (exemple Node.js)

`backend/Dockerfile` :

```dockerfile
FROM node:20-alpine
WORKDIR /app
COPY . .
RUN npm install
CMD ["npm", "start"]
```

#### 🛢️ Base de données (exemple PostgreSQL)

Dans `docker-compose.yml` :

```yaml
db:
  image: postgres
  environment:
    POSTGRES_USER: user
    POSTGRES_PASSWORD: pass
    POSTGRES_DB: mydb
  volumes:
    - db_data:/var/lib/postgresql/data
```

#### 🚀 Serveur de cache (exemple Redis)

```yaml
cache:
  image: redis
```

---

## ⚙️ 2. Configuration avancée

### 💾 Volumes persistants

**But** : Conserver les données même si le conteneur est supprimé.

```yaml
volumes:
  db_data:
```

> **Conseil** : Utilise des volumes nommés pour simplifier la gestion.

---

### 🌐 Configuration du réseau

Créer un réseau dédié :

```yaml
networks:
  monreseau:
    driver: bridge
```

Associer un service au réseau :

```yaml
services:
  backend:
    networks:
      - monreseau
```

> **Avantage** : Communication interne sécurisée, ports non exposés inutilement.

---

### 🧬 Variables d’environnement

**But** : Personnaliser l’application sans modifier le code.

Dans `docker-compose.yml` :

```yaml
environment:
  - DB_HOST=db
  - DB_USER=user
  - DB_PASS=pass
```

Ou via un fichier `.env` :

```
DB_HOST=db
DB_USER=user
DB_PASS=pass
```

Et dans Compose :

```yaml
env_file:
  - .env
```

---

### 🔐 Gestion des secrets

**Objectif** : Ne pas stocker les mots de passe dans le code.

**Méthodes** :

- Docker Swarm (`docker secret`)
- Fichiers montés via volumes

Exemple :

```yaml
secrets:
  db_password:
    file: ./secrets/db_pass.txt
```

---

## 🚀 3. Déploiement & maintenance

### 📁 Dockerfiles optimisés

**Bonne pratique** : Utilise le multi-stage build.

```dockerfile
# Builder
FROM node:20-alpine AS build
WORKDIR /app
COPY . .
RUN npm install && npm run build

# Runner
FROM nginx:alpine
COPY --from=build /app/dist /usr/share/nginx/html
```

---

### 🧩 Docker Compose

Fichier central `docker-compose.yml` :

- Décrit tous les services, volumes, réseaux, dépendances
- Lancement en une commande :
  ```bash
  docker-compose up -d --build
  ```

---

### 🧪 Tests et 🔍 débogage

Commandes utiles :

- Voir les logs : `docker-compose logs -f`
- Entrer dans un conteneur : `docker exec -it backend /bin/sh`
- Rebuild forcé : `docker-compose up --build`

---

### 📝 Documentation du projet

Documente au minimum :

- Les services
- Les ports utilisés
- Les volumes
- Les commandes utiles

**Exemple `README.md`** :

````markdown
## Lancer l'application

```bash
docker-compose up --build
```
````

Services :

- Frontend : http://localhost:3000
- Backend : http://localhost:5000
- DB : PostgreSQL

```

---

## 🔐 4. Bonnes pratiques de production

### 🛡️ Sécurisation des conteneurs

- Ne pas utiliser `root`
- Utiliser des images officielles ou validées
- Scanner les images : `docker scan` ou `trivy`

---

### 📈 Monitoring et logging

- Outils : **Prometheus**, **Grafana**
- Centralisation des logs : **ELK** ou **Loki**

---

### 🗂️ Stratégies de backup

- Sauvegarde des volumes avec `docker cp` ou outil dédié
- Exécution régulière (cron, CI/CD)
- Stockage externe (cloud, disque…)

---

### 📦 Procédures de mise à jour

- Mettre à jour les images : `docker pull`
- Automatiser build + déploiement : GitHub Actions, GitLab CI/CD
- Utiliser le **blue/green deployment** pour éviter les coupures
```
