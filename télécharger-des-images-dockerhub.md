# 📥 Mémo – Télécharger des images Docker depuis Docker Hub

## 🌐 Qu’est-ce que Docker Hub ?

Docker Hub est le **registre officiel** d’images Docker :

- **Images officielles** maintenues par Docker (ex : `nginx`, `mysql`, `ubuntu`)
- Images **communautaires** (publiées par des utilisateurs)
- Dépôts **privés ou publics**

👉 [https://hub.docker.com](https://hub.docker.com)

---

## 🔍 1. Rechercher une image

Via le site :  
[https://hub.docker.com/search](https://hub.docker.com/search)

Via le terminal :

```bash
docker search <nom>
# Exemple :
docker search nginx
```

---

## 📥 2. Télécharger (pull) une image

```bash
docker pull <image>
# Exemples :
docker pull ubuntu              # Dernière version officielle
docker pull ubuntu:22.04        # Version spécifique (tag)
docker pull nginx:alpine        # Variante légère
```

---

## 🧠 3. Structure des noms

```
<nom_utilisateur>/<nom_image>:<tag>
```

- `nginx` = `library/nginx:latest` (image officielle)
- `monuser/monimage:1.0` = image personnelle hébergée sur Docker Hub

---

## 📦 4. Lister les images téléchargées

```bash
docker images
```

---

## 🧽 5. Supprimer une image

```bash
docker rmi <image>
```

---

## 🧪 Exercice rapide

1. Recherche une image (ex : Redis)
2. Télécharge-la
3. Lance-la avec `docker run`
4. Vérifie avec `docker images`

---

## 💡 Astuces

- Si aucun tag n’est précisé → Docker utilise `:latest`
- Utilise `docker pull` pour forcer la mise à jour d’une image
- Privilégie les images officielles (avec ✅ sur Docker Hub)

---

## 🔐 Bonus : Se connecter à Docker Hub

Pour accéder à des dépôts privés :

```bash
docker login
```

Puis :

```bash
docker pull moncompte/image-privee:tag
```

---

# 🧠 Mémo – Lancer et quitter un conteneur Redis sur Docker (macOS)

## 📦 Situation : Redis lancé avec

```bash
docker run redis
```

→ Cette commande lance Redis au premier plan (foreground), dans le terminal courant.

---

❓ **Problème rencontré**

❌ Impossible de “sortir” du terminal  
✅ Le terminal affiche des logs de Redis, mais on ne peut plus taper d’autres commandes

---

✅ **Solutions pour sortir proprement**

### 🛑 1. Quitter et arrêter Redis (le conteneur se termine)

**Ctrl + C**

- Coupe Redis
- Arrête le conteneur

---

### 🧲 2. Quitter sans arrêter Redis (mode détaché)

**Ctrl + P** puis **Ctrl + Q**

- Redis continue de tourner en fond
- Tu récupères la main dans le terminal
- Le conteneur reste en cours d’exécution

---

### 🧭 Pour vérifier l’état ensuite

- **Voir les conteneurs actifs :**
  ```bash
  docker ps
  ```
- **Arrêter Redis :**
  ```bash
  docker stop <id>
  # ou
  docker stop monredis
  ```
- **Revenir dans le conteneur :**
  ```bash
  docker attach <nom|id>
  ```

---

✅ **Bonne pratique : lancer Redis en arrière-plan dès le départ**

```bash
docker run -d -p 6379:6379 --name monredis redis
```

- `-d` → daemon (arrière-plan)
- `-p 6379:6379` → Redis exposé sur localhost:6379
- `--name monredis` → nom plus lisible que l’ID

---

### 🔍 Bonus : Inspecter, logs et nettoyage

- **Voir les logs :**
  ```bash
  docker logs monredis
  ```
- **Supprimer un conteneur (après arrêt) :**
  ```bash
  docker rm monredis
  ```

---

## 📦 Résumé rapide des raccourcis clavier

| Action                    | Raccourci              |
| ------------------------- | ---------------------- |
| Quitter et arrêter        | Ctrl + C               |
| Détacher (sans arrêter)   | Ctrl + P puis Ctrl + Q |
| Revenir dans un conteneur | docker attach <nom>    |

---

🧠 Redis tourne sur le port 6379 par défaut. Tu peux maintenant l’utiliser avec n’importe quel client Redis (CLI, Node.js, Python, etc.) depuis ton Mac.
