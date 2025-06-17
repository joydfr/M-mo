# 🌐 Mémo Docker – Comprendre le Mapping des Ports

## 🔄 Pourquoi mapper des ports ?

Les conteneurs Docker sont isolés. Pour accéder à un service à l’intérieur (ex. : un serveur web), il faut **exposer un port** du conteneur vers le système hôte.

---

## 🧪 Syntaxe

```bash
docker run -p <port_hôte>:<port_conteneur> <image>
```

**Exemples :**

```bash
docker run -p 8080:80 nginx
```

- Le port 80 du conteneur (nginx) devient accessible via `localhost:8080`

---

### 🧠 Notes :

- Tu peux mapper vers le même port : `-p 80:80`
- Plusieurs ports peuvent être mappés : `-p 8080:80 -p 443:443`
- Utilise `docker ps` pour voir quels ports sont exposés

---

### 🔒 Cas avancé :

- Restreindre à une IP spécifique :
  ```bash
  docker run -p 127.0.0.1:8080:80 nginx
  ```
  (n’est accessible que depuis localhost)

---
