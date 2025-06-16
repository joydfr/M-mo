# ✅ Checklist : Installation de Docker

- [x] **Installation de Docker**

  - [x] Installer **Docker Desktop** (pour Windows ou macOS)  
         🔗 [https://www.docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop)
  - [ ] Installer **Docker Engine** (pour Linux)  
         🔗 [https://docs.docker.com/engine/install/](https://docs.docker.com/engine/install/)

- [x] **Configuration de l’environnement**

  - [x] Démarrer Docker
  - [x] S'assurer que le service Docker tourne (ex : `docker info` sans erreur)

- [x] **Vérification de l’installation**

  - [x] Exécuter la commande :
    ```bash
    docker --version
    ```
  - [x] Vérifier que la version s'affiche correctement

- [x] **Premier test : Hello World**

  - [x] Lancer :
    ```bash
    docker run hello-world
    ```
  - [x] Confirmer que le message de succès s'affiche :

    > "Hello from Docker! This message shows that your installation appears to be working correctly."

    Pas de souci ! Le mémo précédent est déjà parfaitement compatible avec Visual Studio Code. Mais voici une version propre, simplifiée et formatée spécifiquement pour VS Code en Markdown :

⸻

# 🐳 Mémo Docker – Premiers pas sur macOS (pour VS Code)

---

## 📥 1. Installation de Docker Desktop

- Télécharger Docker Desktop pour Mac :  
  👉 https://www.docker.com/products/docker-desktop
- Choisir la version adaptée (Apple Silicon ou Intel).
- Ouvrir le `.dmg` → glisser Docker dans le dossier **Applications**.
- Lancer Docker Desktop et accorder les autorisations.
- Vérifier l’icône 🐳 en haut à droite (Docker est lancé).

---

## ✅ 2. Vérifier l'installation

Dans **le terminal** :

```bash
docker --version
```

Exemple de sortie attendue :

```bash
Docker version 24.x.x, build abcdef
```

⸻

🧪 3. Test de fonctionnement

Toujours dans le terminal :

```bash
docker run hello-world
```

Sortie attendue :

```bash
Hello from Docker! This message shows that your installation appears to be working correctly.
```

⸻

🌐 4. Lancer un conteneur Nginx

```bash
docker run -d -p 8080:80 nginx

	•	-d : mode détaché (arrière-plan)
	•	-p 8080:80 : redirige le port 80 du conteneur vers le port 8080 local
```

👉 Ouvre ton navigateur :
http://localhost:8080
→ Tu devrais voir la page d’accueil Nginx.

⸻

📦 5. Gérer les conteneurs

Lister les conteneurs actifs :

```bash
docker ps
```

Exemple de sortie :

```bash
CONTAINER ID   IMAGE   ...   PORTS                NAMES
bd3d12eafc39   nginx   ...   0.0.0.0:8080->80/tcp  reverent_kepler
```

Arrêter un conteneur :

```bash
docker stop bd3d12eafc39
# ou
docker stop reverent_kepler
```

⸻

🧹 6. Nettoyer l’environnement

```bash
docker system prune
```

⸻

🧠 Résumé des commandes utiles

# 📋 Commandes Docker – Tableau récapitulatif

| Commande                         | Fonction                                 |
| -------------------------------- | ---------------------------------------- |
| `docker --version`               | Vérifie l’installation de Docker         |
| `docker run hello-world`         | Teste que Docker fonctionne              |
| `docker run -d -p 8080:80 nginx` | Lance un serveur Nginx                   |
| `docker ps`                      | Affiche les conteneurs actifs            |
| `docker stop [id ou nom]`        | Arrête un conteneur en cours d’exécution |
| `docker system prune`            | Supprime les ressources inutilisées      |

⸻
