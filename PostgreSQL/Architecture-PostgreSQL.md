# Architecture de PostgreSQL

## Structure Fondamentale

L’architecture PostgreSQL est une architecture multiprocessus et non multithread.
Cela signifie que chaque processus de PostgreSQL s’exécute dans un contexte mémoire isolé, et
que la communication entre ces processus repose sur des mécanismes systèmes inter‑processus :
sémaphores, zones de mémoire partagée, sockets. Ceci s’oppose à l’architecture multithread,
où l’ensemble du moteur s’exécute dans un seul processus, avec plusieurs threads (contextes)
d’exécution, où tout est partagé par défaut.
Le principal avantage de cette architecture multiprocessus est la stabilité : un processus, en cas de problème, ne corrompt que sa mémoire (ou la mémoire partagée), le plantage d’un processus n’affecte pas directement les autres. Son principal défaut est une allocation statique des ressources de mémoire partagée : elles ne sont pas redimensionnables à chaud.
Tous les processus de PostgreSQL accèdent à une zone de « mémoire partagée ». Cette zone contient
les informations devant être partagées entre les clients, comme un cache de données, ou des infor‑
mations sur l’état de chaque session par exemple.
PostgreSQL utilise une architecture client‑serveur. Nous ne nous connectons à PostgreSQL qu’à travers d’un protocole bien défini, nous n’accédons jamais aux fichiers de données.

# Mémo : Architecture de PostgreSQL

## Structure Fondamentale

PostgreSQL fonctionne sur une architecture multi-processus où un processus principal (postmaster) gère plusieurs processus backend, chacun traitant une connexion client spécifique.

## Composants Principaux

1. **Processus**

   - **Postmaster** : processus principal qui démarre les autres composants
   - **Backend** : processus dédié à chaque connexion cliente
   - **Background Writer** : écrit les données modifiées du cache vers le disque
   - **WAL Writer** : gère l'écriture des journaux de transactions
   - **Autovacuum** : nettoie automatiquement les tuples morts
   - **Stats Collector** : collecte les statistiques d'activité de la base
   - **Checkpointer** : coordonne les points de contrôle réguliers

2. **Stockage**

   - **Tablespaces** : emplacements physiques pour stocker les données
   - **Relations** : tables, index et autres objets
   - **Pages** : blocs de stockage de taille fixe (généralement 8Ko)
   - **WAL** (Write-Ahead Log) : journal des modifications pour la récupération

3. **Mémoire**

   - **Shared Buffers** : cache principal des données en mémoire partagée
   - **Work Mem** : allouée pour les opérations de tri et de hachage
   - **Maintenance Work Mem** : pour les opérations de maintenance
   - **WAL Buffers** : cache temporaire pour les entrées de journal
   - **Temp Buffers** : mémoire pour les tables temporaires

4. **Contrôle de Concurrence**
   - **MVCC** (Multi-Version Concurrency Control) : permet l'accès simultané sans verrous
   - **Niveaux d'isolation** : READ COMMITTED, REPEATABLE READ, SERIALIZABLE
   - **Verrous** : à différents niveaux (relation, page, tuple)

## Système de Fichiers

PostgreSQL organise ses données en plusieurs répertoires et fichiers :

1. **Répertoire de données (PGDATA)**

   - Le répertoire principal contenant tous les fichiers de la base de données
   - Défini lors de l'initialisation avec `initdb`

2. **Structure des fichiers**

   - **base/** : contient les sous-répertoires pour chaque base de données (un répertoire par OID de base)
   - **global/** : contient les tables partagées (pg_database, pg_authid, etc.)
   - **pg_wal/** (anciennement pg_xlog) : contient les fichiers WAL
   - **pg_multixact/** : données pour les verrous multi-transactions
   - **pg_subtrans/** : données de sous-transactions
   - **pg_commit_ts/** : timestamps de commit
   - **pg_dynshmem/** : fichiers utilisés pour la mémoire partagée dynamique
   - **pg_tblspc/** : liens symboliques vers les tablespaces externes
   - **pg_replslot/** : données des slots de réplication

3. **Fichiers de configuration**

   - **postgresql.conf** : paramètres généraux de configuration
   - **pg_hba.conf** : contrôle d'accès client (Host-Based Authentication)
   - **pg_ident.conf** : mappage des identités pour l'authentification

4. **Segmentation des fichiers**
   - Les tables et index de grande taille sont divisés en segments de 1 Go
   - Chaque segment est nommé avec le format `relation.filenode.segment`

## Catalogues Système

Les catalogues système sont des tables spéciales qui contiennent les métadonnées de la base de données :

1. **Tables système principales**

   - **pg_class** : information sur les tables, index, vues, etc.
   - **pg_attribute** : information sur les colonnes des tables
   - **pg_type** : définition des types de données
   - **pg_proc** : information sur les fonctions et procédures
   - **pg_namespace** : définition des schémas
   - **pg_constraint** : contraintes sur les tables
   - **pg_database** : liste des bases de données
   - **pg_authid** : information sur les rôles et utilisateurs

2. **Vues système**

   - **pg_tables** : information sur les tables
   - **pg_indexes** : information sur les index
   - **pg_stats** : statistiques sur les colonnes
   - **pg_roles** : information sur les rôles
   - **information_schema** : schéma standard SQL contenant des vues sur les métadonnées

3. **Fonctionnement**
   - Accessibles comme des tables ordinaires via SQL
   - Stockés dans le répertoire global/ ou dans chaque base de données
   - Fortement inter-reliés via des références OID
   - Essentiels pour le fonctionnement du planificateur de requêtes

## Lexique

| Terme                 | Définition                                                                                      |
| --------------------- | ----------------------------------------------------------------------------------------------- |
| **ACID**              | Propriétés d'une transaction fiable : Atomicité, Cohérence, Isolation, Durabilité               |
| **Autovacuum**        | Processus qui nettoie automatiquement les tuples obsolètes et récupère l'espace                 |
| **Backend**           | Processus serveur dédié à une connexion client                                                  |
| **Catalogue système** | Ensemble de tables qui stockent les métadonnées sur la base de données                          |
| **Checkpoint**        | Point où toutes les données modifiées sont écrites sur disque, créant un point de cohérence     |
| **Extension**         | Module qui ajoute des fonctionnalités à PostgreSQL sans modifier le code noyau                  |
| **Filenode**          | Identifiant numérique associé à un objet de base de données et utilisé pour nommer les fichiers |
| **Index**             | Structure de données qui accélère la récupération des données                                   |
| **MVCC**              | Technique permettant l'accès simultané aux données sans utiliser de verrous bloquants           |
| **OID**               | Object IDentifier, identifiant unique attribué aux objets de la base de données                 |
| **PGDATA**            | Variable d'environnement ou paramètre indiquant le répertoire de données principal              |
| **Postmaster**        | Processus principal qui démarre et gère les autres processus PostgreSQL                         |
| **Relation**          | Terme générique pour désigner tables, index, vues et autres objets                              |
| **Schéma**            | Espace de noms contenant des objets de base de données (tables, vues, etc.)                     |
| **Segment**           | Partie d'un fichier de table ou d'index, généralement limité à 1 Go                             |
| **Tablespace**        | Emplacement physique où sont stockées les données des tables et des index                       |
| **Transaction**       | Séquence d'opérations traitée comme une unité indivisible                                       |
| **Tuple**             | Terme technique pour une ligne dans une table PostgreSQL                                        |
| **Vacuum**            | Opération qui récupère l'espace occupé par des données obsolètes                                |
| **WAL**               | Write-Ahead Log, journal qui enregistre les modifications avant qu'elles ne soient appliquées   |
| **XID**               | Transaction IDentifier, identifiant unique pour chaque transaction                              |
