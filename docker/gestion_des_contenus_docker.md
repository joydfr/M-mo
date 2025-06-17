# 🚀 Le cycle de vie Docker expliqué

## 🧠 1. Dev : build → test → release

- Build : création d’une image via pull+run+modify+commit (manuelle) ou via un Dockerfile (automatisée) ￼.
- Un Dockerfile typique inclut : FROM, COPY, RUN, EXPOSE, CMD, ENTRYPOINT ￼.
- Test : exécution de conteneurs en environnement isolé, répétitif et stable, intégré à de l’intégration continue (CI) ￼.
- Release (Ship) : push de l’image vers un registry (Docker Hub, Docker Trusted Registry…) pour la suite ￼.

⸻

## ⚙️ 2. Ops : pull → run → monitor → rollback

- Pull de l’image depuis le registry, exécution (docker run) en production ￼.
- Automatisation possible des déploiements après la publication de nouvelles images .
- Monitoring : performance, logs, expérience utilisateur.
  - En cas de dysfonctionnement : rollback automatique vers la version antérieure ￼.

⸻

## 🌐 3. Réseaux & isolation

- Docker Network via LibNetwork permet :
  - Connecter les conteneurs sur le même hôte ou plusieurs hôtes.
  - Segmentation logique (bridge, overlay, création de réseaux FRONTEND / BACKEND) ￼.
  - Exemple :
    • WEB exposé à l’extérieur
    • WORKER communiquant avec WEB et DB
    • DB isolé, inaccessible directement depuis l’extérieur .

⸻

## 🧩 4. Écosystème Docker

- Build : Docker Machine, Docker Toolbox, Docker for Windows/Mac — création d’environnements Docker.
- Ship : Docker Hub, Trusted Registry.
- Run : Docker Swarm (SwarmKit intégré), Compose, intégrations cloud (Azure, AWS Bêta) ￼.

⸻

## 🌱 5. Docker Machine & hosts

    •	Outil de provisioning automatique d’hôtes Docker, local ou dans le cloud : VirtualBox, Hyper‑V, AWS, Azure, DigitalOcean .

⸻

## 🤝 6. Orchestration & alternatives

- Outre Swarm, l’écosystème inclut Kubernetes (via RedHat/OpenShift), Rancher, Azure/AWS ECS, Google Cloud Run .
- Orchestration = gestion de clusters, scalabilité automatisée, haute disponibilité.

⸻

## 📦 7. Cycle de vie des conteneurs

### 🌀 1. Cycle de vie basique (éphémère)

    •	🔄 Création & exécution : docker run alpine → un conteneur démarre, exécute /bin/sh puis s’arrête.
    •	🛑 Fin : status Exited — conteneur supprimé ou laissé en état arrêté.
    •	🎯 Idéal pour des tâches ponctuelles (scripts, test rapide).

⸻

### 🔁 2. Cycle de vie avancé (service)

    •	🧱 Service persistant : ex. docker run nginx lance un processus qui reste vivant, prêt à répondre.
    •	➕ Accessibilité : exposé sur un port, disponible en continu.
    •	🎯 Convient aux apps Web, APIs, bases de données.

⸻

### 🔍 3. Comparaison

- Aspect Basique (éphémère) Avancé (service)
- Durée Quelques secondes/minutes Long terme (jours, semaines)
- Persistance ❌ Non persistante ✅ Persistante
- Accessibilité Locale/éphémère Client/serveur via réseau
- Usage Tâches rapides Services continus

⸻

### 📦 4. Persistance des données

    •	Volumes : stockés hors du conteneur, survivent à sa suppression  ￼ ￼ ￼
    •	Bind mount : fichiers hôtes montés dans le conteneur, persistant aussi  ￼
    •	Pratique pour bases de données, logs ou partages de données.

⸻

### 🧩 5. Cycle complet avec Docker Compose

- 📁 Un fichier docker-compose.yml définit plusieurs services (+ réseaux, volumes) ￼
- Commandes :
  - docker-compose up → tout démarre
  - docker-compose down → tout stoppe
- ✅ Orchestration, mise à l’échelle et gestion centralisée.

⸻

### 🛡️ 6. Sécurité & bonnes pratiques

    •	🧯 Utiliser images officielles/fiables, activer DOCKER_CONTENT_TRUST=1  ￼ ￼ ￼ ￼.
    •	🙅‍♂️ Éviter le mode privileged, limiter les capacités.
    •	🔐 Activer SELinux/AppArmor/cgroups pour isoler  ￼.

⸻

### ✅ Pourquoi maîtriser ces cycles ?

- 💡 Flexibilité : choix adapté selon task/service.
- 🔧 Optimisation : ressources allouées selon besoin.
- 🚀 Scalabilité : faciliter montée en charge et fiabilité.
- 🔄 Reproductibilité : infrastructure déclarative avec Compose.

⸻

### 📘 Résumé visuel

```text
[Créer image] → [docker run]
       ↓             ↘
   Conteneur     conteneur
   éphémère   service
       ↓             ↓
 Arrêt / delete   Exposé / persistant
```

⸻

### Pour aller plus loin

    •	📚 Volumes pour l’état persistant  ￼ ￼
    •	⚙️ Docker Compose pour orchestrer des apps multi-conteneurs  ￼
    •	🛡️ Sécurité conteneurs : isolation, images signées, SELinux/AppArmor  ￼

⸻

## 💡 À retenir

- Docker structure l’intégralité du cycle DevOps.
- Automatisation à chaque étape : build, push, pull, run, monitor.
- Réseaux & registry comme piliers pour isolation et déploiement.
- L’écosystème s’étend bien au-delà du simple container, jusqu’à l’orchestration serveur/cloud.

⸻
