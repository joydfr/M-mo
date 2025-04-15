## Introduction

### Quest-ce qu'une base de données ?

Une base de données est un ensemble d'informations organisées de manière à faciliter l'accès, la gestion et la mise à jour des données. Elle permet de stocker, de récupérer et de manipuler des données de manière efficace. Les bases de données sont utilisées dans de nombreux domaines, tels que la gestion d'entreprise, le commerce électronique, la recherche scientifique et bien d'autres.

### Pourquoi utiliser une base de données ?

Les bases de données sont utilisées pour plusieurs raisons :

- **Stockage structuré** : Les bases de données permettent de stocker des données de manière structurée, ce qui facilite leur gestion et leur récupération.
- **Intégrité des données** : Les bases de données garantissent l'intégrité des données en imposant des contraintes et des règles sur les données stockées.

### Les contraintes du modèle relationnel

**Les contraintes d'intégrité relationnelle** se réfèrent aux conditions qui doivent être présentes pour qu'une relation soit valide. Il existe de nombreux types de contraintes d'intégrité. Les contraintes sur le système de gestion de base de données relationnelles sont principalement divisées en trois catégories principales : contraintes clés, contraintes de domaine et contraintes d'intégrité référentielle.

**Une contrainte de clé** : qui indiquent qu'une table doit toujours avoir une clé primaire. La valeur de l'attribut pour les différents enregistrements de la relation doit être unique. Les contraintes clés sont également connues sous le nom de contraintes d'entité.

**Les contraintes de domaine** limitent la plage des valeurs de domaine d'un attribut. Ils spécifient également l'individualité et si un attribut peut avoir une valeur nulle. Il peut également spécifier une valeur par défaut pour un attribut lorsque aucune valeur n'est fournie.

Les contraintes du domaine peuvent être violées si une valeur d'attribut n'apparaît pas dans le domaine correspondant ou si elle n'est pas du type de données approprié.

**La contrainte d'intégrité référentielle** indique que les relations entre les tables doivent toujours être cohérentes. En d'autres termes, la zone de clé étrangère doit correspondre à la clé primaire référencée par la clé étrangère. Tout changement de champ de clé primaire doit être appliqué à toutes les clés étrangères, ou pas du tout.

# 🗄️ Concepts Fondamentaux des Bases de Données Relationnelles 🗄️

## 📊 Structures de Données

- **Table/Relation** 📋 - Structure fondamentale qui organise les données en lignes et colonnes
- **Colonne/Attribut** 📝 - Élément individuel de données avec un type défini (nombre, texte, date...)
- **Ligne/Tuple/Enregistrement** 📄 - Ensemble complet de valeurs pour tous les attributs d'une table
- **Domaine** 🎯 - Ensemble de valeurs autorisées pour un attribut

## 🔑 Clés et Relations

- **Clé Primaire** 🔐 - Attribut(s) identifiant de façon unique chaque ligne d'une table
- **Clé Étrangère** 🔗 - Attribut établissant une relation avec la clé primaire d'une autre table
- **Clé Candidate** 🎲 - Attribut(s) pouvant servir de clé primaire
- **Clé Composite** 🧩 - Clé formée de plusieurs attributs combinés
- **Clé Surrogate** 🏷️ - Identifiant artificiel (souvent auto-incrémenté) utilisé comme clé primaire

## 🛡️ Intégrité des Données

- **Contraintes** ⚠️ - Règles garantissant la validité des données
  - **NOT NULL** ❗ - Exige une valeur
  - **UNIQUE** 🦄 - Garantit l'unicité des valeurs
  - **CHECK** ✅ - Vérifie une condition
  - **DEFAULT** 🔄 - Définit une valeur par défaut
- **Intégrité Référentielle** 🤝 - Assure la cohérence des relations entre tables
- **Intégrité d'Entité** 🛡️ - Garantit l'unicité de chaque entité (via clé primaire)

## 📈 Optimisation et Performance

- **Index** 📖 - Structure accélérant la recherche de données
  - **B-Tree** 🌳 - Index standard équilibré
  - **Hash** # - Index basé sur des fonctions de hachage
  - **GiST/GIN** 🌐 - Index pour types de données complexes
- **Partition** 🧱 - Division d'une grande table en segments plus petits
- **Cluster** 📦 - Réorganisation physique des données selon un index

## 🧰 Objets et Structures

- **Vue** 🪟 - Table virtuelle basée sur une requête
- **Vue Matérialisée** 💾 - Vue dont le résultat est stocké physiquement
- **Procédure Stockée** 📜 - Code SQL précompilé et stocké dans la base
- **Fonction** 🧮 - Routine retournant une valeur ou un ensemble de résultats
- **Déclencheur/Trigger** ⚡ - Code exécuté automatiquement en réponse à des événements
- **Séquence** 🔢 - Générateur de nombres séquentiels
- **Schéma** 📁 - Conteneur logique organisant les objets de la base

## 🔄 Transactions et Concurrence

- **Transaction** 🔄 - Ensemble d'opérations formant une unité atomique
- **Propriétés ACID** 💊
  - **Atomicité** ⚛️ - Tout ou rien
  - **Cohérence** 📐 - La base reste dans un état cohérent
  - **Isolation** 🏝️ - Les transactions sont isolées les unes des autres
  - **Durabilité** 💎 - Les modifications sont permanentes
- **Verrou** 🔒 - Mécanisme contrôlant l'accès concurrent aux données
- **MVCC** 📚 - Contrôle de concurrence multi-version évitant les blocages

## 🧠 Théorie et Conception

- **Normalisation** 📏 - Processus d'organisation des données pour réduire la redondance

  ### 📐 Les 5 Formes Normales

  - **1NF (Première Forme Normale)** 🥇

    - Chaque attribut contient une valeur atomique (non divisible)
    - Pas de groupes répétitifs ou de colonnes multivaluées
    - Table avec une clé primaire identifiée

  - **2NF (Deuxième Forme Normale)** 🥈

    - Déjà en 1NF
    - Tous les attributs non-clés dépendent de la totalité de la clé primaire
    - Élimine les dépendances partielles (pertinent si la clé primaire est composite)

  - **3NF (Troisième Forme Normale)** 🥉

    - Déjà en 2NF
    - Pas de dépendances transitives (un attribut non-clé ne dépend pas d'un autre attribut non-clé)
    - Chaque attribut non-clé dépend directement de la clé primaire

  - **BCNF (Forme Normale de Boyce-Codd)** 🏅

    - Forme plus stricte de la 3NF
    - Pour chaque dépendance fonctionnelle X → Y, X doit être une super-clé
    - Élimine toutes les anomalies basées sur les dépendances fonctionnelles

  - **4NF (Quatrième Forme Normale)** 🏆

    - Déjà en BCNF
    - Pas de dépendances multivaluées non-triviales
    - Traite les relations many-to-many sans attributs redondants

  - **5NF (Cinquième Forme Normale)** 👑
    - Déjà en 4NF
    - Pas de dépendances de jointure non-triviales
    - Une table ne peut pas être décomposée en plusieurs tables plus petites sans perte d'information

- **Dénormalisation** 🔄 - Introduction contrôlée de redondance pour optimiser les performances
- **Modèle Entité-Relation** 🔀 - Représentation graphique de la structure de la base de données
- **Algèbre Relationnelle** 🧪 - Fondement théorique des opérations sur les tables

## 🛠️ Opérations SQL

- **SELECT** 🔍 - Récupération de données
- **INSERT** ➕ - Ajout de données
- **UPDATE** 🔄 - Modification de données
- **DELETE** ❌ - Suppression de données
- **Jointure** 🤝 - Combinaison de lignes de différentes tables
  - **INNER JOIN** ⚪ - Intersection
  - **LEFT/RIGHT JOIN** ◀️▶️ - Inclusion à gauche/droite
  - **FULL JOIN** ⭕ - Union complète
  - **CROSS JOIN** ✖️ - Produit cartésien
- **Agrégation** 📊 - Calculs sur des groupes de lignes (SUM, AVG, COUNT...)
- **Sous-requête** 🪆 - Requête imbriquée dans une autre
