# Mémo PostgreSQL - Gestion des Utilisateurs

## Exercice 1: Création d'utilisateur

**Consigne:** Créez un utilisateur nommé 'stagiaire' avec un mot de passe, qui peut se connecter mais ne peut pas créer de bases de données.

**Solution:**

```sql
CREATE USER stagiaire WITH
    PASSWORD 'mot_de_passe_securise'
    NOCREATEDB
    LOGIN;
```

## Exercice 2: Modification d'utilisateur

**Consigne:** Modifiez l'utilisateur 'stagiaire' pour lui permettre de créer des bases de données et définir une date d'expiration au 31 décembre 2025.

**Solution:**

```sql
ALTER USER stagiaire
    CREATEDB
    VALID UNTIL '2025-12-31';
```

## Exercice 3: Gestion des privilèges

**Consigne:** Créez un utilisateur 'analyste' qui peut se connecter à la base 'statistiques' mais ne peut que lire (SELECT) les tables du schéma 'public'.

**Solution:**

```sql
-- Création de l'utilisateur
CREATE USER analyste WITH PASSWORD 'mot_de_passe_securise';

-- Attribution des privilèges de connexion à la base
GRANT CONNECT ON DATABASE statistiques TO analyste;

-- Attribution des privilèges de lecture sur le schéma public
GRANT USAGE ON SCHEMA public TO analyste;

-- Attribution des privilèges SELECT sur toutes les tables existantes
GRANT SELECT ON ALL TABLES IN SCHEMA public TO analyste;

-- Pour garantir les mêmes privilèges sur les futures tables
ALTER DEFAULT PRIVILEGES IN SCHEMA public
    GRANT SELECT ON TABLES TO analyste;
```

## Exercice 4: Suppression sécurisée

**Consigne:** Écrivez les commandes pour supprimer proprement un utilisateur 'ancien_employe' qui possède des objets dans la base de données.

**Solution:**

```sql
-- Étape 1 (optionnelle): Identifier les objets appartenant à l'utilisateur
SELECT * FROM pg_catalog.pg_tables WHERE tableowner = 'ancien_employe';
SELECT * FROM pg_catalog.pg_proc WHERE proowner = 'ancien_employe';

-- Étape 2: Forcer la déconnexion si l'utilisateur est connecté
SELECT pg_terminate_backend(pid)
FROM pg_stat_activity
WHERE usename = 'ancien_employe';

-- Étape 3: Réattribuer la propriété des objets à un autre utilisateur
REASSIGN OWNED BY ancien_employe TO nouvel_utilisateur;

-- Étape 4: Supprimer les privilèges et objets restants
DROP OWNED BY ancien_employe;

-- Étape 5: Supprimer l'utilisateur
DROP USER ancien_employe;
```

## Exercice 5: Gestion avancée

**Consigne:** Créez un utilisateur 'reporting' qui ne peut se connecter qu'entre 8h et 18h les jours ouvrables et qui a un mot de passe qui expire après 60 jours.

**Solution:**

```sql
-- Création de l'utilisateur avec restriction horaire
CREATE USER reporting WITH
    PASSWORD 'mot_de_passe_securise'
    CONNECTION LIMIT 5
    LOGIN;

-- Restriction des horaires de connexion (du lundi au vendredi de 8h à 18h)
ALTER USER reporting
    CONNECTION LIMIT 5
    PASSWORD VALID UNTIL CURRENT_DATE + INTERVAL '60 days';

-- Configuration de la règle d'authentification dans pg_hba.conf
-- Ajoutez cette ligne dans le fichier pg_hba.conf:
-- host  all  reporting  0.0.0.0/0  md5 clientcert=1
-- Map=reporting_map

-- Création d'un fichier pg_ident.conf pour définir les plages horaires
-- (Nécessite une configuration personnalisée avec un script externe ou une extension)
```

> Note: PostgreSQL n'a pas de fonctionnalité native pour restreindre les connexions par heure/jour. Cette limitation pourrait nécessiter une solution externe (proxy d'authentification, trigger, etc.).

## Exercice 6: Audit des utilisateurs

**Consigne:** Écrivez une requête SQL qui liste tous les utilisateurs de votre système PostgreSQL avec leurs principaux attributs.

**Solution:**

```sql
SELECT
    usename AS nom_utilisateur,
    usesysid AS id_utilisateur,
    CASE WHEN usesuper THEN 'oui' ELSE 'non' END AS superutilisateur,
    CASE WHEN usecreatedb THEN 'oui' ELSE 'non' END AS peut_creer_bd,
    CASE WHEN uselogin THEN 'oui' ELSE 'non' END AS peut_se_connecter,
    CASE WHEN userepl THEN 'oui' ELSE 'non' END AS peut_repliquer,
    passwd AS mot_de_passe_hache,
    valuntil AS date_expiration,
    description
FROM pg_catalog.pg_user
JOIN pg_catalog.pg_roles ON usename = rolname
LEFT JOIN pg_catalog.pg_shdescription ON pg_roles.oid = pg_shdescription.objoid
ORDER BY usename;
```
