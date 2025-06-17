# Comprendre la structure des images Docker

---

## 🧱 Qu’est-ce qu’une image Docker ?

Une image Docker est un empilement de couches immuables, construites étape par étape à partir d’un Dockerfile.  
Elle est en lecture seule et sert de modèle pour créer des conteneurs.

---

## 🧬 Structure interne d’une image

```
Image Docker
├── Couches (layers) empilées (UnionFS)
│   ├── FROM (image de base)
│   ├── RUN (exécute des commandes)
│   ├── COPY / ADD (ajoute des fichiers)
│   ├── ENV, EXPOSE, etc.
│   └── CMD / ENTRYPOINT (définit l'action)
└── Manifest & métadonnées
```

---

## 🔄 Exemple de construction via Dockerfile

```dockerfile
FROM ubuntu:22.04        # → Couche 1
RUN apt update           # → Couche 2
RUN apt install -y curl  # → Couche 3
COPY . /app              # → Couche 4
CMD ["bash"]             # → Instruction finale
```

Chaque instruction = 🧱 une couche ➜ superposées dans l’image.

---

## 📂 Où sont stockées les couches ?

- Identifiées par un digest SHA256 (unique)
- Réutilisables entre plusieurs images (caching)
- Stockées dans `/var/lib/docker/overlay2/` (sur Linux)

---

## 🧠 Particularités

| Propriété            | Description                                   |
| -------------------- | --------------------------------------------- |
| 🔒 Immuables         | Chaque couche est en lecture seule            |
| 📦 Couches partagées | Plusieurs images peuvent partager des couches |
| 🔁 Cache intelligent | Docker ne reconstruit que ce qui change       |

---

## 🛠 Lorsqu’un conteneur démarre :

- Docker superpose toutes les couches de l’image
- Il ajoute une couche en lecture/écriture temporaire
- Toutes les modifs (fichiers, logs…) vont dans cette couche

---

## 🧪 Pour voir les couches d’une image

```bash
docker history <nom_image>
```

Exemple :

```bash
docker history ubuntu
```

Tu verras l’historique de construction de l’image, couche par couche.

---

## 🧬 Schéma de la structure interne

```
Docker Image (ex: myapp:latest)
┌─────────────────────────────┐
│ 🧱 Couche 5 : CMD            │
│  CMD ["node", "index.js"]   │
├─────────────────────────────┤
│ 🧱 Couche 4 : COPY           │
│  COPY . /app                │
├─────────────────────────────┤
│ 🧱 Couche 3 : RUN            │
│  RUN npm install            │
├─────────────────────────────┤
│ 🧱 Couche 2 : RUN            │
│  RUN apt-get update         │
├─────────────────────────────┤
│ 🧱 Couche 1 : FROM           │
│  FROM node:18-alpine        │
└─────────────────────────────┘
```

Chaque couche est en **lecture seule** et identifiée par un digest SHA256.  
Plusieurs images peuvent partager des couches (caching).

---

## 🧠 Bonnes pratiques & astuces

| Astuce                 | Pourquoi ?                               |
| ---------------------- | ---------------------------------------- |
| Grouper les RUN        | Réduit le nombre de couches              |
| Utiliser .dockerignore | Évite d’ajouter des fichiers inutiles    |
| Privilégier alpine     | Images plus petites, builds plus rapides |

---

## 🎯 À retenir

- Une image = 📚 empilement de couches immuables
- Chaque instruction du Dockerfile crée une nouvelle couche
- Les images sont optimisées, réutilisables et économisent du stockage
- Le conteneur ajoute une couche writable temporaire au démarrage
