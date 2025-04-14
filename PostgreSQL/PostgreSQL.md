# PostgreSQL

## Qu'est-ce que PostgreSQL ?

PostgreSQL est un système de gestion de base de données relationnelle et objet (SGBDRO) open source. Les origines de PostgreSQL remontent à 1986 dans le cadre du projet POSTGRES à l’Université de Californie à Berkeley. Il bénéficie de plus de 35 ans de développement actif sur la plateforme principale.

PostgreSQL s’est forgé une solide réputation grâce à son architecture éprouvée, sa fiabilité, l’intégrité de ses données, son ensemble de fonctionnalités robuste, sa grande extensibilité, et l'engagement de la communauté open source qui contribue continuellement à fournir des solutions performantes et innovantes. PostgreSQL fonctionne sur tous les principaux systèmes d’exploitation, est conforme ACID (Atomicité, Cohérence, Isolation, Durabilité) depuis 2001, et propose des modules puissants comme l’extension géospatiale populaire PostGIS.

## Différences entre PostgreSQL et les autres SGBD

PostgreSQL se distingue des autres systèmes de gestion de bases de données par plusieurs caractéristiques clés :
Voici un tableau comparatif de PostgreSQL avec d'autres SGBD en format Markdown :

| Caractéristique        | PostgreSQL                                       | MySQL/MariaDB                  | Oracle                | SQL Server                 | MongoDB                           | SQLite                           |
| ---------------------- | ------------------------------------------------ | ------------------------------ | --------------------- | -------------------------- | --------------------------------- | -------------------------------- |
| **Type**               | Relationnel                                      | Relationnel                    | Relationnel           | Relationnel                | NoSQL (documents)                 | Relationnel embarqué             |
| **Licence**            | Open source (PostgreSQL License)                 | Open source (GPL/propriétaire) | Propriétaire (payant) | Propriétaire (payant)      | Open source/Commercial            | Domaine public                   |
| **Conformité SQL**     | Très élevée                                      | Modérée                        | Très élevée           | Très élevée                | N/A (utilise JSON)                | Bonne                            |
| **Extensibilité**      | Excellente (types personnalisés, fonctions)      | Limitée                        | Bonne                 | Bonne                      | Flexible (schéma)                 | Limitée                          |
| **Performances**       | Très bonnes (optimisées pour requêtes complexes) | Excellentes (lectures simples) | Excellentes           | Très bonnes                | Excellentes (lecture)             | Bonnes (petites BD)              |
| **Concurrence**        | MVCC                                             | Verrouillage de table/ligne    | MVCC                  | Verrouillage de ligne      | Document-level                    | Verrouillage fichier             |
| **Données spatiales**  | Oui (PostGIS)                                    | Limité                         | Oracle Spatial        | SQL Spatial                | GeoJSON                           | Extensions                       |
| **Support JSON**       | Natif (JSONB)                                    | Limité                         | Oui                   | Oui                        | Natif                             | Limité                           |
| **Héritage de tables** | Oui                                              | Non                            | Non                   | Non                        | Non                               | Non                              |
| **Partitionnement**    | Natif                                            | Oui                            | Oui                   | Oui                        | Sharding                          | Non                              |
| **Réplication**        | Streaming, logique                               | Maître-esclave                 | Avancée               | Avancée                    | Réplication automatique           | N/A                              |
| **Cas d'usage idéal**  | Applications complexes, données géospatiales, BI | Applications web, OLTP         | Entreprise, OLTP/OLAP | Environnements Windows, BI | Big data, données non structurées | Applications mobiles, embarquées |
| **Complexité admin**   | Modérée                                          | Faible                         | Élevée                | Modérée                    | Faible                            | Très faible                      |

Ce tableau met en évidence les principales différences entre PostgreSQL et les autres systèmes de gestion de bases de données populaires.

## Avantages de PostgreSQL

PostgreSQL présente de nombreux avantages qui en font un choix privilégié pour les développeurs et les entreprises. Voici quelques-uns des principaux avantages :

| Catégorie                        | Avantages                                                                                                                                                                                                                                           |
| -------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Robustesse et fiabilité**      | • Conformité ACID complète garantissant l'intégrité des données<br>• Système de journalisation WAL pour la récupération après panne<br>• Stabilité prouvée en environnement de production critique                                                  |
| **Extensibilité et flexibilité** | • Création de types de données personnalisés<br>• Système d'extensions riche (PostGIS, pgVector, TimescaleDB, etc.)<br>• Support natif des formats JSON/JSONB, XML, Hstore<br>• Fonctions stockées dans multiples langages (PL/pgSQL, Python, etc.) |
| **Fonctionnalités avancées**     | • Requêtes complexes avec CTE et expressions récursives<br>• Indexation variée (B-tree, Hash, GiST, GIN, BRIN)<br>• Contraintes d'exclusion pour règles métiers avancées<br>• Héritage de tables et vues matérialisées                              |
| **Performance**                  | • Optimiseur de requêtes sophistiqué<br>• Partitionnement natif des tables<br>• Exécution parallèle des requêtes<br>• Système MVCC efficace pour la concurrence                                                                                     |
| **Compatibilité et standards**   | • Conformité SQL parmi les plus strictes du marché<br>• Portabilité cross-platform (Linux, Windows, macOS)<br>• Migration facilitée depuis d'autres SGBD<br>• Interopérabilité avec nombreux langages et frameworks                                 |
| **Écosystème et support**        | • Communauté mondiale active et réactive<br>• Documentation exhaustive et de qualité<br>• Nombreux outils d'administration (pgAdmin, DBeaver)<br>• Support commercial disponible via plusieurs entreprises                                          |
| **Coût et licence**              | • Gratuit et open source<br>• Licence PostgreSQL permissive<br>• Absence de coûts de licence contrairement aux solutions propriétaires<br>• Coût total de possession (TCO) réduit sur le long terme                                                 |
| **Sécurité**                     | • Gestion fine des privilèges et des rôles<br>• Chiffrement des données au repos et en transit<br>• Authentification forte et diversifiée<br>• Audits et journalisation des activités                                                               |

Ces caractéristiques font de PostgreSQL un choix idéal pour des applications allant des petits projets aux systèmes d'entreprise critiques nécessitant fiabilité, extensibilité et performances.

## Cas d'usage adaptés

PostgreSQL est adapté à une variété de cas d'usage, notamment :

# Cas d'usage adaptés à PostgreSQL

| Catégorie                      | Cas d'usage                                                                                                                                 | Raisons                                                                                  |
| ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- |
| **Applications géospatiales**  | • Systèmes d'information géographique (SIG)<br>• Applications de cartographie<br>• Services basés sur la localisation<br>• Analyse spatiale | Extension PostGIS offrant des fonctionnalités géospatiales complètes et performantes     |
| **Applications financières**   | • Systèmes bancaires<br>• Trading et marchés financiers<br>• Assurances<br>• Comptabilité et facturation                                    | Intégrité transactionnelle ACID, précision des calculs, contraintes d'intégrité avancées |
| **Big Data et analyse**        | • Entrepôts de données<br>• Applications BI/Analytics<br>• Systèmes de reporting<br>• Data lakes hybrides                                   | Capacité à gérer de grands volumes, fonctions analytiques avancées, partitionnement      |
| **Applications critiques**     | • Systèmes médicaux<br>• Télécommunications<br>• Systèmes gouvernementaux<br>• Infrastructure critique                                      | Haute disponibilité, réplication robuste, récupération après sinistre                    |
| **Commerce électronique**      | • Places de marché en ligne<br>• Gestion d'inventaire<br>• Systèmes de recommandation<br>• Panier d'achat & paiements                       | Performance pour les charges mixtes (lecture/écriture), gestion avancée du stock         |
| **Applications web complexes** | • Réseaux sociaux<br>• Plateformes de contenu<br>• SaaS complexes<br>• Sites à fort trafic                                                  | Modèle flexible, JSONB pour données variables, mise à l'échelle horizontale              |
| **IoT et télémétrie**          | • Applications industrielles<br>• Domotique<br>• Suivi de flotte<br>• Collecte de données de capteurs                                       | Ingestion de données à haut débit, partitionnement par temps, fonctions d'agrégation     |
| **Recherche scientifique**     | • Analyses génomiques<br>• Modélisation environnementale<br>• Physique des particules<br>• Traitement d'images médicales                    | Types de données complexes, opérateurs personnalisés, indexation avancée                 |
| **CRM et ERP**                 | • Gestion de la relation client<br>• Planification des ressources<br>• Systèmes de billetterie<br>• Gestion de projets                      | Modèle relationnel robuste, contraintes d'intégrité, transactions complexes              |
| **Applications multi-tenant**  | • SaaS avec isolation des données<br>• Plateformes mutualisées<br>• Services cloud                                                          | Schémas multiples, Row-Level Security, vues pour isolation logique                       |

PostgreSQL est particulièrement adapté aux cas d'usage nécessitant une combinaison de fiabilité, flexibilité et capacité à gérer des données complexes tout en maintenant d'excellentes performances.

### Lexique

- **ACID** : ACID (atomicité, cohérence, isolation et durabilité) sont un ensemble de propriétés qui garantissent qu'une transaction informatique est exécutée de façon fiable. Dans le domaine des bases de données, une opération sur les données est appelée une transaction ou transaction informatique. Par exemple, un transfert de fonds d'un compte de banque à un autre, même s'il implique plusieurs actions comme le débit d'un compte et le crédit d'un autre, est une seule transaction.
- **SGBD** : Un système de gestion de base de données (SGBD) est un logiciel qui permet de créer, gérer et manipuler des bases de données. Il fournit une interface pour interagir avec les données, effectuer des requêtes, et garantir l'intégrité et la sécurité des informations stockées.
- **SGBDRO** : Un système de gestion de base de données relationnelle et objet (SGBDRO) est un type de SGBD qui combine les caractéristiques des bases de données relationnelles et des bases de données orientées objet. Il permet de stocker des données sous forme d'objets, tout en offrant des fonctionnalités relationnelles telles que les jointures et les transactions.
- **PostGIS** : PostGIS est une extension de PostgreSQL qui ajoute le support des données géospatiales. Elle permet de stocker, interroger et manipuler des données géographiques dans une base de données PostgreSQL, offrant ainsi des fonctionnalités avancées pour les applications géospatiales.
- **MVCC** : MVCC (Multi-Version Concurrency Control) est une méthode de gestion de la concurrence dans les bases de données qui permet à plusieurs transactions d'accéder simultanément aux données sans se bloquer mutuellement. Cela améliore les performances et la réactivité des systèmes de gestion de bases de données.
- **Partitionnement** : Le partitionnement est une technique de gestion des données qui divise une table en plusieurs segments appelés partitions. Cela permet d'améliorer les performances des requêtes et de faciliter la gestion des données en répartissant la charge sur plusieurs unités de stockage.
- **Réplication** : La réplication est le processus de copie et de distribution des données d'une base de données vers une ou plusieurs autres bases de données. Cela permet d'assurer la disponibilité, la redondance et la sauvegarde des données, ainsi que d'améliorer les performances en répartissant la charge entre plusieurs serveurs.
- **Sharding** : Le sharding est une technique de partitionnement horizontal des données dans une base de données distribuée. Il consiste à diviser les données en segments appelés shards, qui sont stockés sur différents serveurs. Cela permet d'améliorer les performances et la scalabilité des systèmes de gestion de bases de données.
