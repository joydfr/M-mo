# 🐘 Mémo PostgreSQL – Commandes de base & utiles

## ⚙️ Connexion à PostgreSQL

```bash
psql -U nom_utilisateur -d nom_base

	•	-U : utilisateur PostgreSQL (souvent postgres)
	•	-d : nom de la base de données

Ex : psql -U postgres -d ma_base

⸻

📋 Commandes générales dans psql

Commande	Description
\l	Liste toutes les bases
\c base	Se connecter à une base
\dt	Lister les tables
\d table	Décrire une table
\du	Lister les utilisateurs
\q	Quitter
\?	Aide générale
\x	Affichage étendu (lisibilité ++ pour les gros résultats)



⸻

🧱 Commandes SQL courantes

🔧 Création

CREATE DATABASE ma_base;

CREATE TABLE utilisateurs (
    id SERIAL PRIMARY KEY,
    nom VARCHAR(100),
    email VARCHAR(100) UNIQUE
);

📥 Insertion

INSERT INTO utilisateurs (nom, email)
VALUES ('Alice', 'alice@example.com');

🔎 Lecture

SELECT * FROM utilisateurs;
SELECT nom FROM utilisateurs WHERE email LIKE '%@example.com';

✏️ Mise à jour

UPDATE utilisateurs
SET nom = 'Bob'
WHERE email = 'alice@example.com';

🗑️ Suppression

DELETE FROM utilisateurs
WHERE nom = 'Bob';



⸻

🔐 Gestion des utilisateurs et droits

-- Créer un utilisateur
CREATE USER mon_user WITH PASSWORD 'motdepasse';

-- Donner tous les droits sur une base
GRANT ALL PRIVILEGES ON DATABASE ma_base TO mon_user;

-- Donner des droits sur une table
GRANT SELECT, INSERT ON utilisateurs TO mon_user;



⸻

🔄 Autres commandes utiles dans psql

Commande	Utilité
\timing	Affiche le temps d’exécution
\conninfo	Infos de connexion
\password	Modifier son mot de passe
\! commande	Exécute une commande shell (ex : \! ls)



⸻

🚀 Bonus : Exécuter un script SQL

psql -U postgres -d ma_base -f script.sql



⸻

🧰 Modèle de script d’init de base

-- Création de la base
CREATE DATABASE exemple_db;

-- Connexion à la base (dans psql ensuite)
\c exemple_db

-- Table de démonstration
CREATE TABLE utilisateurs (
    id SERIAL PRIMARY KEY,
    nom VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    date_creation TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Ajout de données
INSERT INTO utilisateurs (nom, email) VALUES
('Alice', 'alice@example.com'),
('Bob', 'bob@example.com');



⸻

💡 Astuce : Tu peux créer un fichier init.sql avec tout ce contenu et le versionner dans Git comme base de départ pour tous tes projets PostgreSQL.

---

Si tu veux que je t’en fasse un PDF ou que je te le mette dans un fichier `.md` prêt à l’emploi, dis-le moi !
```
