# 📘 Mémo des commandes Docker 🐳

---

## 🔍 1. Images

| Commande              | Description                  |
| --------------------- | ---------------------------- |
| `docker pull <image>` | 📥 Télécharger une image     |
| `docker images`       | 📦 Lister les images locales |
| `docker rmi <image>`  | 🧹 Supprimer une image       |

---

## 🚀 2. Conteneurs

| Commande                      | Description                         |
| ----------------------------- | ----------------------------------- |
| `docker run <image>`          | ▶️ Lancer un conteneur              |
| `docker run -d <image>`       | 🚀 Lancer en arrière-plan (détaché) |
| `docker run -it <image> bash` | 💬 Mode interactif avec terminal    |
| `docker ps`                   | 📋 Lister les conteneurs en cours   |
| `docker ps -a`                | 📋 Lister tous les conteneurs       |
| `docker stop <id>`            | 🛑 Stopper un conteneur             |
| `docker start <id>`           | 🔁 Redémarrer un conteneur          |
| `docker rm <id>`              | 🧽 Supprimer un conteneur           |

---

## 🛠️ 3. Images personnalisées

| Commande                                 | Description                           |
| ---------------------------------------- | ------------------------------------- |
| `docker build -t mon-image .`            | 🏗️ Construire une image (Dockerfile)  |
| `docker commit <id> mon-image`           | 💾 Sauver un conteneur comme image    |
| `docker tag mon-image user/mon-image:v1` | 🏷️ Tagger une image                   |
| `docker push user/mon-image:v1`          | 📤 Envoyer une image vers un registry |

---

## 🧰 4. Inspecter / Debugger

| Commande                    | Description                     |
| --------------------------- | ------------------------------- |
| `docker logs <id>`          | 📄 Voir les logs d’un conteneur |
| `docker exec -it <id> bash` | 🛠️ Entrer dans un conteneur     |
| `docker inspect <id>`       | 🔍 Détails d’un conteneur/image |

---

## 🌐 5. Réseaux & volumes

| Commande                    | Description                |
| --------------------------- | -------------------------- |
| `docker network ls`         | 🌐 Voir les réseaux Docker |
| `docker volume ls`          | 💾 Lister les volumes      |
| `docker volume rm <volume>` | 🧹 Supprimer un volume     |

---

## 🧼 6. Nettoyage

| Commande                 | Description                           |
| ------------------------ | ------------------------------------- |
| `docker system prune`    | 🧽 Nettoyer tout ce qui est inutilisé |
| `docker image prune`     | 🧹 Supprimer les images non utilisées |
| `docker container prune` | 🗑️ Supprimer les conteneurs stoppés   |

---
