# 🐳 Mémo : Introduction au Stockage avec Docker

Imaginez jouer à un jeu vidéo sur votre console, progressant à travers les niveaux, recueillant des objets et des succès. Si la console ne sauvegarde pas votre progression, vous devrez recommencer depuis le début chaque fois que vous l'éteignez. C'est un peu ce qui arrive avec les conteneurs Docker sans un mécanisme de stockage persistant : sans celui-ci, toutes les modifications et les données générées dans le conteneur sont perdues lorsque celui-ci est supprimé ou redémarré. Docker propose plusieurs solutions pour sauvegarder et gérer ces données, assurant ainsi qu'elles persistent au-delà du cycle de vie des conteneurs.

## 📌 Pourquoi gérer le stockage dans Docker ?

Par défaut, les données dans un conteneur Docker sont **éphémères**.  
Quand le conteneur est supprimé, les données **le sont aussi**, sauf si on utilise un **mécanisme de stockage persistant**.

## 📦 Les types de stockage Docker

Docker propose 3 types de montages :

---

## 1. 🔗 Volumes (Recommandé pour production)

Les volumes sont comme des disques durs externes pour vos conteneurs, gérés par Docker et stockés hors du système de fichiers du conteneur. Ils permettent de conserver et de partager des données entre conteneurs et avec l'hôte, assurant leur persistance même après la suppression des conteneurs

- **Gérés automatiquement** par Docker.
- Stockés dans : `/var/lib/docker/volumes/` (sur le système hôte).
- Peut être utilisé **par plusieurs conteneurs**.
- Ne dépend pas de l’arborescence locale du projet.
- Idéal pour **les bases de données**, **les données utilisateur**, etc.

```bash
docker volume create mon_volume
docker run -v mon_volume:/app/data myimage
```

---

## 2. 📁 Bind Mounts (Montage local précis)

Pensez aux bind mounts comme à des clés USB que vous pouvez connecter à différents ordinateurs. Ils permettent de monter un dossier ou un fichier existant sur l'hôte directement dans un conteneur, offrant une manière pratique de travailler sur les fichiers de l'hôte depuis le conteneur.

### 📌 Qu’est-ce qu’un Bind Mount ?

- Tu choisis manuellement un chemin précis sur ta machine (le “host”).
- Ce dossier est monté dans un conteneur à un emplacement défini.
- Toute modification dans le conteneur modifie directement les fichiers sur ta machine (et vice versa).

### 🔍 Utilisation typique :

- Partager ton code source entre ta machine et un conteneur (ex : hot reload avec Node.js ou Flask).
- Tester un fichier de configuration local.

### ✅ Avantages :

- Très utile en développement.
- Permet d’éditer le code depuis ton éditeur local sans rebuild.

### ⚠️ Inconvénients :

- Moins portable (dépend des chemins exacts sur ta machine).
- Plus exposé à des erreurs ou des conflits de droits.

### 📦 Exemple :

```bash
docker run -v /home/jody/monprojet:/app myimage
```

Ce montage rendra `/home/jody/monprojet` visible dans le conteneur sous `/app`.

Tu peux aussi monter un fichier spécifique :

```bash
docker run -v $(pwd)/config.yml:/app/config.yml myimage
```

---

## 3. 🧪 Tmpfs Mounts (Mémoire uniquement)

Les tmpfs mounts sont comparables à des notes autocollantes que vous utilisez pour des rappels temporaires. Ils stockent des données en mémoire RAM, sans persistance sur le disque dur, idéal pour les informations temporaires ou sensibles qui ne doivent pas être conservées après l'arrêt du conteneur.

### 📌 Qu’est-ce qu’un Tmpfs Mount ?

- Stocke les données en RAM (et non sur le disque).
- Aucune trace sur le disque dur → plus rapide, plus sécurisé, mais non persistant.
- Les données sont perdues dès l’arrêt du conteneur.

### 🔍 Utilisation typique :

- Stockage temporaire ou sensible (fichiers secrets, caches).
- Réduction de l’écriture disque (ex : performances, vie d’un SSD).

### ✅ Avantages :

- Très rapide.
- Données jamais écrites sur disque = sécurité (utile pour infos sensibles).
- Réduction des I/O disque.

### ⚠️ Inconvénients :

- Données perdues au redémarrage.
- Consomme la RAM de ta machine.

### 📦 Exemple :

```bash
docker run --tmpfs /app/cache myimage
```

Cela monte un répertoire temporaire en RAM dans le conteneur, sous `/app/cache`.

Tu peux aussi définir une taille maximale :

```bash
docker run --tmpfs /app/cache:rw,size=64m myimage
```

---

## 🆚 Différence entre Volumes et Bind Mounts

### 📦 Volumes (Docker-managed)

- Crée un **espace isolé** dans Docker (`/var/lib/docker/volumes/`).
- Idéal pour les **applications en production**.
- Plus **sécurisé**, **portable** et **stable**.
- Peut être **géré avec `docker volume`** (inspect, backup, prune…).

### 📁 Bind Mounts (Host-managed)

- Lien direct entre un **dossier/fichier sur ta machine** et le conteneur.
- Parfait pour le **développement** (éditions en temps réel).
- Dépend du système de fichiers hôte (chemins absolus, permissions).
- Plus exposé aux erreurs (ex : mauvais chemin, conflits de droits).

| Critère          | Volume                      | Bind Mount                        |
| ---------------- | --------------------------- | --------------------------------- |
| Créé par Docker  | ✅ Oui                      | ❌ Non (c'est toi qui le définis) |
| Portabilité      | ✅ Élevée                   | ❌ Faible (chemins spécifiques)   |
| Accès à distance | ✅ Par Docker uniquement    | ✅ Par OS                         |
| Sécurité         | ✅ Meilleure isolation      | ❌ Moins sécurisé                 |
| Usage typique    | Production, base de données | Dev, édition de fichiers          |

---

## 🧠 Récapitulatif

| Type        | Persistant | Stockage        | Performance | Cas d’usage                       |
| ----------- | :--------: | --------------- | ----------- | --------------------------------- |
| Volume      |     ✅     | Disque (Docker) | 🔁 Moyenne  | Données applicatives, DB          |
| Bind Mount  |     ✅     | Disque (local)  | 🔁 Moyenne  | Développement local, partage code |
| Tmpfs Mount |     ❌     | RAM             | ⚡ Rapide   | Cache, fichiers sensibles         |

---

## 🧹 Commandes utiles

```bash
docker volume ls               # Lister les volumes
docker volume prune            # Supprimer les volumes inutilisés
docker inspect mon_volume      # Détails sur un volume
```

---

## 📎 Références utiles

- [Volumes - Docker Docs](https://docs.docker.com/storage/volumes/)
- [Bind Mounts - Docker Docs](https://docs.docker.com/storage/bind-mounts/)
- [Tmpfs Mounts - Docker Docs](https://docs.docker.com/storage/tmpfs/)

---
