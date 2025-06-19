# 🐳 Mémo – Dockeriser une Application Node.js

## 📦 1. Créer une image Docker

### Fichiers de base

**app.js**

```js
const express = require("express");
const app = express();

app.get("/", (req, res) => res.send("Hello from Docker!"));

const PORT = process.env.PORT || 3000;
app.listen(PORT, () => console.log(`Server running on port ${PORT}`));
```

**package.json**

```json
{
  "name": "node-docker-app",
  "version": "1.0.0",
  "main": "app.js",
  "scripts": {
    "start": "node app.js"
  },
  "dependencies": {
    "express": "^4.18.2"
  }
}
```

**Dockerfile simple**

```dockerfile
FROM node:20

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .

EXPOSE 3000
CMD ["npm", "start"]
```

### Commandes

```sh
docker build -t jody/node-app .
docker run -p 3000:3000 jody/node-app
```

---

## 🧪 2. Optimisation avec Multi-stage Build

```dockerfile
# Étape 1 : build
FROM node:20 AS build

WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .

# Étape 2 : image légère pour exécution
FROM node:20-slim

WORKDIR /app
COPY --from=build /app .

EXPOSE 3000
CMD ["node", "app.js"]
```

✅ **Avantage** : image plus légère, plus rapide à déployer.

---

## ☁️ 3. Publier l’image sur Docker Hub

### Étapes

1. **Connexion :**

   ```sh
   docker login
   ```

2. **Tag de l’image :**

   ```sh
   docker tag jody/node-app jodydufour/node-app:latest
   ```

3. **Push vers Docker Hub :**
   ```sh
   docker push jodydufour/node-app:latest
   ```

🔗 **Accès** : [https://hub.docker.com/r/jodydufour/node-app](https://hub.docker.com/r/jodydufour/node-app)
