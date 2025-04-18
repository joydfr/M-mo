# 🔐 Utilisateur `reporting` — Accès sécurisé et restreint

## 🎯 Objectifs

- ✅ Lecture seule sur la base `exo1_db`, schéma `public`
- ⏰ Accès **limité de 08h à 18h**, **du lundi au vendredi**
- 🔁 Expiration automatique du mot de passe **tous les 60 jours**

---

## 🧱 Étape 1 — Création de l’utilisateur

```sql
CREATE ROLE reporting
  WITH LOGIN
  PASSWORD 'SuperSecure123@'
  VALID UNTIL '2025-06-17'; -- Expiration dans 60 jours
```

---

## 📊 Étape 2 — Accès lecture seule sur la base `exo1_db`

```sql
-- Connexion à la base
GRANT CONNECT ON DATABASE exo1_db TO reporting;

-- Accès au schéma 'public'
GRANT USAGE ON SCHEMA public TO reporting;

-- Lecture sur toutes les tables existantes
GRANT SELECT ON ALL TABLES IN SCHEMA public TO reporting;

-- Lecture automatique sur futures tables
ALTER DEFAULT PRIVILEGES IN SCHEMA public
GRANT SELECT ON TABLES TO reporting;
```

---

## ⏰ Étape 3 — Restreindre l'accès à une plage horaire (08h–18h, jours ouvrés)

### ✅ Solution : Utiliser `cron` pour activer/désactiver le compte

**Activer à 8h tous les jours ouvrés :**

```bash
0 8 * * 1-5 psql -U postgres -d exo1_db -c "ALTER ROLE reporting VALID UNTIL 'infinity';"
```

**Désactiver à 18h tous les jours ouvrés :**

```bash
0 18 * * 1-5 psql -U postgres -d exo1_db -c "ALTER ROLE reporting VALID UNTIL '2025-04-18 18:00:00';"
```

> 📝 À adapter avec la date du jour à chaque exécution.  
> Tu peux aussi automatiser avec un petit script shell.

---

## 🔁 Étape 4 — Rotation du mot de passe tous les 60 jours

### ✅ Méthode recommandée : mot de passe expirant avec `VALID UNTIL`

```sql
ALTER ROLE reporting VALID UNTIL '2025-06-17';
```

### ⏳ Automatisation possible :

- Utiliser un `cron` mensuel pour envoyer une alerte ou régénérer le mot de passe
- Ou combiner avec une gestion externe (Vault, Ansible, etc.)

---

## 🧪 Vérification

### Voir les rôles :

```sql
\du
```

### Tester la connexion :

```bash
psql -U reporting -d exo1_db
```

### Vérifier les droits :

```sql
SELECT * FROM une_table;       -- ✅ autorisé
INSERT INTO une_table VALUES ...; -- ❌ interdit
```

---

## 🧼 Bonnes pratiques

- Utiliser un mot de passe fort et unique
- Ne jamais donner `CREATEDB`, `CREATEROLE`, ou `SUPERUSER`
- Documenter les `crons` et rotations dans un README

---
