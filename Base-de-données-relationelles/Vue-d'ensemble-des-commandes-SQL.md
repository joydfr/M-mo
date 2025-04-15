# Mémo : Les Langages SQL en Bases de Données Relationnelles

## DDL (Data Definition Language)

Le langage de définition de données permet de créer et de modifier la structure de la base de données.

**Commandes principales :**

- `CREATE` : Crée des objets dans la base de données (tables, vues, index, etc.)
- `ALTER` : Modifie la structure d'objets existants
- `DROP` : Supprime des objets de la base de données
- `TRUNCATE` : Vide le contenu d'une table tout en conservant sa structure
- `COMMENT` : Ajoute des commentaires au dictionnaire de données
- `RENAME` : Renomme un objet

**Exemple :**

```sql
CREATE TABLE Clients (
    client_id INT PRIMARY KEY,
    nom VARCHAR(50),
    email VARCHAR(100) UNIQUE
);

ALTER TABLE Clients ADD COLUMN telephone VARCHAR(15);
```

## DML (Data Manipulation Language)

Le langage de manipulation de données permet d'interagir avec les données stockées dans la base.

**Commandes principales :**

- `SELECT` : Récupère des données d'une ou plusieurs tables
- `INSERT` : Ajoute de nouvelles lignes dans une table
- `UPDATE` : Modifie des données existantes
- `DELETE` : Supprime des lignes d'une table
- `MERGE` : Combine opérations INSERT/UPDATE/DELETE (UPSERT)

**Exemple :**

```sql
INSERT INTO Clients (client_id, nom, email) VALUES (1, 'Dupont', 'dupont@example.com');

SELECT nom, email FROM Clients WHERE client_id = 1;

UPDATE Clients SET telephone = '0123456789' WHERE client_id = 1;
```

## DCL (Data Control Language)

Le langage de contrôle de données gère les permissions et les droits d'accès aux données.

**Commandes principales :**

- `GRANT` : Accorde des privilèges à un utilisateur
- `REVOKE` : Retire des privilèges à un utilisateur
- `DENY` : Refuse explicitement un privilège (spécifique à certains SGBD)

**Exemple :**

```sql
GRANT SELECT, INSERT ON Clients TO utilisateur1;

REVOKE DELETE ON Clients FROM utilisateur1;
```

## TCL (Transaction Control Language)

Le langage de contrôle des transactions gère les transactions et assure l'intégrité des données.

**Commandes principales :**

- `COMMIT` : Valide définitivement les modifications d'une transaction
- `ROLLBACK` : Annule les modifications d'une transaction
- `SAVEPOINT` : Définit un point de sauvegarde dans une transaction
- `SET TRANSACTION` : Définit les caractéristiques d'une transaction

**Exemple :**

```sql
BEGIN TRANSACTION;
    UPDATE Comptes SET solde = solde - 1000 WHERE compte_id = 1;
    UPDATE Comptes SET solde = solde + 1000 WHERE compte_id = 2;

    -- Si les deux opérations sont réussies
    COMMIT;

    -- En cas d'erreur
    -- ROLLBACK;
```

## Points importants à retenir

1. **DDL** modifie la structure
2. **DML** modifie les données
3. **DCL** gère les accès
4. **TCL** gère les transactions

Les instructions DDL déclenchent généralement un COMMIT implicite dans la plupart des SGBD relationnels, validant automatiquement toutes les modifications en cours avant leur exécution.
