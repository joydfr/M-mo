# Mémo PostgreSQL - Gestion des Utilisateurs

## 1. Création d'utilisateurs

PostgreSQL utilise le concept de "rôles" pour gérer les autorisations. Un utilisateur est simplement un rôle avec le privilège de connexion.

### CREATE USER

La commande `CREATE USER` permet de créer un nouvel utilisateur dans PostgreSQL.

**Syntaxe de base:**

```sql
CREATE USER nom_utilisateur WITH options;
```

**Options courantes:**

- `PASSWORD 'mot_de_passe'` : Définit le mot de passe
- `SUPERUSER` / `NOSUPERUSER` : Accorde ou non les privilèges administrateur
- `CREATEDB` / `NOCREATEDB` : Permet ou non la création de bases de données
- `CREATEROLE` / `NOCREATEROLE` : Permet ou non la création d'autres rôles
- `LOGIN` / `NOLOGIN` : Autorise ou non la connexion

**Exemples:**

```sql
-- Utilisateur simple avec mot de passe
CREATE USER alice WITH PASSWORD 'secret123';

-- Utilisateur avec plus de privilèges
CREATE USER admin WITH
    PASSWORD 'admin123'
    SUPERUSER
    CREATEDB
    CREATEROLE;
```

### Alternative avec CREATE ROLE

La commande `CREATE ROLE` est identique à `CREATE USER`, mais par défaut, `CREATE ROLE` crée un rôle sans droit de connexion (`NOLOGIN`).

```sql
-- Équivalent à CREATE USER alice...
CREATE ROLE alice WITH LOGIN PASSWORD 'secret123';
```

## 2. Modification d'utilisateurs

### ALTER USER

La commande `ALTER USER` permet de modifier les attributs d'un utilisateur existant.

**Syntaxe de base:**

```sql
ALTER USER nom_utilisateur WITH options;
```

**Exemples:**

```sql
-- Modifier le mot de passe
ALTER USER alice WITH PASSWORD 'nouveau_mot_de_passe';

-- Ajouter des privilèges
ALTER USER alice WITH CREATEDB;

-- Retirer des privilèges
ALTER USER alice WITH NOCREATEDB;

-- Définir une date d'expiration
ALTER USER alice VALID UNTIL '2025-12-31';

-- Renommer un utilisateur
ALTER USER alice RENAME TO alice_smith;
```

### Changement de mot de passe

En plus de `ALTER USER`, il existe d'autres méthodes pour changer un mot de passe:

**Pour l'utilisateur courant:**

```sql
-- Méthode directe
\password

-- Avec une commande SQL
ALTER USER CURRENT_USER WITH PASSWORD 'nouveau_mot_de_passe';
```

**Pour un autre utilisateur (nécessite des privilèges):**

```sql
ALTER USER nom_utilisateur WITH PASSWORD 'nouveau_mot_de_passe';
```

## 3. Suppression d'utilisateurs

### DROP USER

La commande `DROP USER` permet de supprimer un utilisateur.

**Syntaxe de base:**

```sql
DROP USER [IF EXISTS] nom_utilisateur;
```

**Exemples:**

```sql
-- Supprimer un utilisateur
DROP USER alice;

-- Éviter l'erreur si l'utilisateur n'existe pas
DROP USER IF EXISTS bob;
```

### Précautions à prendre

Avant de supprimer un utilisateur, il faut faire attention à:

1. **Vérifier la propriété des objets**:

   - Un utilisateur ne peut pas être supprimé s'il possède des objets (tables, fonctions, etc.)
   - Il faut d'abord transférer la propriété ou supprimer ces objets

2. **Gestion des dépendances**:

   - Vérifier si l'utilisateur est mentionné dans des politiques de sécurité
   - Vérifier si des autorisations (`GRANT`) ont été accordées à l'utilisateur

3. **Alternative avec `CASCADE`**:

   ```sql
   -- Supprime l'utilisateur et tous ses objets (ATTENTION: destructif!)
   DROP OWNED BY alice CASCADE;
   DROP USER alice;
   ```

4. **Révoquer les privilèges d'abord**:

   ```sql
   -- Révoquer toutes les autorisations sur une base de données
   REVOKE ALL ON DATABASE ma_base FROM alice;

   -- Révoquer tous les privilèges sur un schéma
   REVOKE ALL ON SCHEMA public FROM alice;
   ```
