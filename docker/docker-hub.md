# 🐳 Docker Hub

---

## 📌 Qu'est-ce que Docker Hub ?

**Docker Hub** est le **registre officiel public** proposé par Docker Inc.  
Il permet de **partager, héberger et distribuer** des images Docker, en facilitant la collaboration et le déploiement d'applications conteneurisées.

🧰 Il contient :

- Des **images officielles** maintenues par les éditeurs de logiciels
- Des **images communautaires**
- Des **images privées** (selon le niveau d'abonnement)

---

## 🚀 Fonctionnalités clés

| 🧩 Fonctionnalité              | 📋 Description                                                      |
| ------------------------------ | ------------------------------------------------------------------- |
| 📤 Partage d’images            | Publier et partager des images avec la communauté ou en privé       |
| 🔍 Recherche                   | Moteur de recherche intégré pour trouver des images                 |
| ⚙️ Automatisation              | Déclencheurs (webhooks) pour automatiser les builds et déploiements |
| 🏷️ Gestion des versions        | Utilisation de tags pour gérer plusieurs versions d’une image       |
| 🔐 Sécurité                    | Gestion des accès, images privées, et signature des images          |
| 🔄 Intégration CI/CD           | S’intègre avec les pipelines pour automatiser les push/pull         |
| 👥 Organisations & Teams       | Gérer les images et les autorisations en équipe                     |
| 📈 Statistiques                | Voir le nombre de pulls, étoiles, mises à jour                      |
| 💻 Intégration Docker Desktop  | Accès direct depuis Docker Desktop                                  |
| 🔒 Support pour images privées | Stockage sécurisé d’images non publiques                            |

---

## 👤 Création de compte & Connexion

📝 Pour utiliser Docker Hub :

1. Crée un compte sur [hub.docker.com](https://hub.docker.com)
2. Connecte ton terminal :

```bash
docker login
```

Cela permet de pousser (push) ou tirer (pull) des images depuis/vers ton compte.

⸻

## 💳 Niveaux d’abonnement Docker Hub

| 🆓 Gratuit                       | 💰 Payant                         |
| -------------------------------- | --------------------------------- |
| ✅ Tirer des images              | ✅ Plus d’images privées          |
| ✅ Pousser des images publiques  | ✅ Priorité support et ressources |
| ✅ Limite sur les images privées | ✅ Meilleure gestion des équipes  |

⸻

🏷️ Gestion des Tags dans Docker Hub

- 📌 À quoi servent les tags ?

Les tags permettent d’identifier différentes versions ou configurations d’une image. Par défaut, latest est utilisé, mais tu peux en définir d’autres.

- 🔧 Comment taguer une image ?

docker tag mon_apache mon_utilisateur/mon_apache:version1

Tu peux ensuite pousser cette version :

docker push mon_utilisateur/mon_apache:version1

- 🗂️ Sur Docker Hub

Dans l’interface, tu peux voir et gérer tous les tags associés à une image, utile pour suivre les mises à jour ou restaurer une version.

⸻

🌐 Registres Docker Alternatifs

## 🔁 Registres Docker et leurs utilisations

| 🔁 Registre                  | 💡 Utilisation principale              |
| ---------------------------- | -------------------------------------- |
| 🐳 Docker Hub                | Registre public par défaut             |
| ☁️ Google Container Registry | Pour projets Google Cloud              |
| 🛡️ Amazon ECR                | Registre Docker intégré à AWS          |
| 🐙 GitHub Container Registry | Déploiement continu via GitHub Actions |
| 🦊 GitLab Container Registry | CI/CD GitLab intégré                   |

⸻

## 🧠 Résumé

- 🐳 Docker Hub est le registre Docker public le plus utilisé, avec des images officielles et communautaires.
- 📤 Il permet le partage, le versioning, la sécurité, et l’intégration CI/CD autour des images Docker.
- 🧾 Tags : Outil essentiel pour suivre les différentes versions d’une image.
- 🔐 Nécessite une connexion (docker login) pour interagir avec tes images privées ou pour en publier de nouvelles.
- 🌍 Il existe aussi d’autres registres selon ton cloud provider ou ton workflow CI/CD.

📚 Pour plus d’infos : Documentation Docker Hub

---
