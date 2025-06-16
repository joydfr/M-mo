# 📚 Les registres Docker

---

## 📦 Qu’est-ce qu’un registre Docker ?

Un **registre Docker** est un service qui **stocke** et **distribue** des images Docker.  
Il permet de partager facilement des applications conteneurisées entre développeurs, équipes ou environnements (local, cloud, CI/CD…).

🔁 **Il sert d’intermédiaire** entre la création d’une image Docker et son exécution sur un serveur.

---

### 🎲 Analogie :

> Un registre Docker est comme une **bibliothèque**.  
> Les **images Docker** sont les **livres** que vous pouvez **emprunter (pull)** ou **ajouter (push)**.

---

## 🤔 Pourquoi utiliser un registre Docker ?

Les registres Docker (comme **Docker Hub**, **GitHub Container Registry**, ou **GitLab Container Registry**) sont essentiels pour :

| 🛠️ Fonctionnalité           | 📋 Description                                                                  |
| --------------------------- | ------------------------------------------------------------------------------- |
| 🔄 **Partage d’images**     | Facilite la collaboration entre équipes                                         |
| 🗂️ **Versioning**           | Permet de gérer plusieurs versions d’une même image (`:v1`, `:latest`, etc.)    |
| 🔐 **Sécurité**             | Stocke des images **publiques ou privées**, avec gestion des accès              |
| ⚙️ **Automatisation**       | S’intègre dans les **pipelines CI/CD** pour déployer automatiquement les images |
| ☁️ **Multi-environnements** | Utilisable en **local**, dans le **cloud**, ou sur des **clusters Kubernetes**  |

---

## 🧰 Exemples de registres populaires

| 🌐 Registre                                   | 📌 Description rapide                                |
| --------------------------------------------- | ---------------------------------------------------- |
| [Docker Hub](https://hub.docker.com)          | Registre public officiel par Docker Inc.             |
| GitHub Container Registry                     | Intégré à GitHub, utile pour les projets open-source |
| GitLab Container Registry                     | Pour les pipelines DevOps internes GitLab            |
| Amazon ECR (AWS)                              | Registre Docker dans le cloud AWS                    |
| Google Container Registry / Artifact Registry | Pour projets GCP                                     |

---

## 🧪 Commandes utiles avec un registre Docker

| 🧾 Commande                      | 🧩 Description                             |
| -------------------------------- | ------------------------------------------ |
| `docker pull nom/image`          | Télécharger une image depuis un registre   |
| `docker push nom/image`          | Pousser une image vers un registre         |
| `docker login`                   | Se connecter à un registre Docker sécurisé |
| `docker tag image nom/image:tag` | Renommer/taguer une image pour l’envoi     |

---

## 🏁 En conclusion

- 📚 Un **registre Docker** est un **service de stockage et de distribution** d’images Docker.
- 🔁 Il permet le **partage**, le **versioning**, la **sécurité** et l’**automatisation** autour des images.
- 🧠 C’est un **élément central dans un workflow DevOps moderne**, garantissant que tout le monde déploie **la même version** de l’application.

> 📌 **Résumé :** Le registre Docker est à l’image ce que Git est au code source.

---
