# 🔧 Mémo Docker – Gérer les Variables d’Environnement

## 💡 Pourquoi les variables ?

Elles permettent de **paramétrer dynamiquement** un conteneur (ex : credentials, config, environnement).

---

## 🧪 Syntaxe simple :

```bash
docker run -e NOM=valeur <image>
```

**Exemple :**

```bash
docker run -e ENV=production -e DEBUG=false myapp
```

---

### 📁 Charger depuis un fichier `.env` :

```bash
docker run --env-file .env myapp
```

**Contenu du fichier `.env` :**

```
ENV=production
DEBUG=false
API_KEY=123abc
```

---

### 🔍 Voir les variables dans un conteneur :

```bash
docker exec <nom> printenv
```

---

### 🔒 Astuces :

- Ne versionne jamais un `.env` contenant des secrets.
- Utilise `.env.example` dans GitHub avec des valeurs fictives.

---
