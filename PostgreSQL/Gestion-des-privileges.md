# Mémo PostgreSQL - Gestion des Droits et Privilèges

## 1. Privilèges de Base

PostgreSQL propose plusieurs types de privilèges qui contrôlent les actions qu'un utilisateur peut effectuer sur les objets de la base de données.

### SELECT

- Permet de lire/consulter les données d'une table ou vue
- Ne permet pas de modifier les données

```sql
-- Attribution du privilège SELECT sur une table
GRANT SELECT ON table_name TO user_name;

-- Attribution du privilège SELECT uniquement sur certaines colonnes
GRANT SELECT (column1, column2) ON table_name TO user_name;
```

### INSERT

- Permet d'ajouter de nouvelles lignes dans une table
- Ne permet pas de modifier les données existantes

```sql
-- Attribution du privilège INSERT sur une table
GRANT INSERT ON table_name TO user_name;

-- Attribution du privilège INSERT uniquement sur certaines colonnes
GRANT INSERT (column1, column2) ON table_name TO user_name;
```

### UPDATE

- Permet de modifier les données existantes dans une table
- Ne permet pas d'ajouter de nouvelles lignes

```sql
-- Attribution du privilège UPDATE sur une table
GRANT UPDATE ON table_name TO user_name;

-- Attribution du privilège UPDATE uniquement sur certaines colonnes
GRANT UPDATE (column1, column2) ON table_name TO user_name;
```

### DELETE

- Permet de supprimer des lignes dans une table
- Ne permet pas de modifier les données existantes

```sql
-- Attribution du privilège DELETE sur une table
GRANT DELETE ON table_name TO user_name;
```

## 2. Attribution des Droits (GRANT)

### Sur les Tables

```sql
-- Attribution d'un privilège spécifique
GRANT SELECT ON table_name TO user_name;

-- Attribution de plusieurs privilèges
GRANT SELECT, INSERT, UPDATE ON table_name TO user_name;

-- Attribution de tous les privilèges
GRANT ALL PRIVILEGES ON table_name TO user_name;

-- Attribution de privilèges sur toutes les tables d'un schéma
GRANT SELECT ON ALL TABLES IN SCHEMA schema_name TO user_name;

-- Configuration des privilèges par défaut pour les futures tables
ALTER DEFAULT PRIVILEGES IN SCHEMA schema_name
GRANT SELECT, INSERT, UPDATE, DELETE ON TABLES TO user_name;
```

### Sur les Bases de Données

```sql
-- Droit de connexion à une base de données
GRANT CONNECT ON DATABASE db_name TO user_name;

-- Droit de créer des objets dans un schéma
GRANT CREATE ON SCHEMA schema_name TO user_name;

-- Droit d'utiliser un schéma (accéder à ses objets)
GRANT USAGE ON SCHEMA schema_name TO user_name;
```

### Options Additionnelles

```sql
-- Permettre à l'utilisateur de transférer les privilèges à d'autres
GRANT SELECT ON table_name TO user_name WITH GRANT OPTION;

-- Attribuer des privilèges à tous les utilisateurs
GRANT SELECT ON table_name TO PUBLIC;
```

## 3. Révocation des Droits (REVOKE)

```sql
-- Révocation d'un privilège spécifique
REVOKE SELECT ON table_name FROM user_name;

-- Révocation de plusieurs privilèges
REVOKE INSERT, UPDATE ON table_name FROM user_name;

-- Révocation de tous les privilèges
REVOKE ALL PRIVILEGES ON table_name FROM user_name;

-- Révocation des privilèges sur toutes les tables d'un schéma
REVOKE SELECT ON ALL TABLES IN SCHEMA schema_name FROM user_name;

-- Révocation en cascade (inclut les privilèges accordés par l'utilisateur)
REVOKE SELECT ON table_name FROM user_name CASCADE;

-- Révocation sans cascade (conserve les privilèges accordés par l'utilisateur)
REVOKE SELECT ON table_name FROM user_name RESTRICT;
```

## 4. Impact sur les Utilisateurs

- Les utilisateurs ne peuvent effectuer que les actions pour lesquelles ils ont reçu des privilèges
- La révocation d'un privilège prend effet immédiatement (sauf pour les connexions actives)
- La suppression d'un utilisateur ne supprime pas automatiquement les objets qu'il possède
- Utiliser `REASSIGN OWNED` et `DROP OWNED` avant de supprimer un utilisateur

## 5. Vérification des Privilèges

```sql
-- Voir les privilèges sur une table
\dp table_name
-- ou
SELECT * FROM information_schema.role_table_grants
WHERE table_name = 'your_table';

-- Voir les privilèges d'un utilisateur sur toutes les tables
SELECT table_schema, table_name, privilege_type
FROM information_schema.role_table_grants
WHERE grantee = 'user_name'
ORDER BY table_schema, table_name;

-- Voir les rôles et leurs attributs
SELECT rolname, rolsuper, rolcreatedb, rolcreaterole
FROM pg_roles;
```
