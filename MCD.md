# MCD

## Introduction

Dans la méthodologie Merise destinée à créer des bases de données, il existe des outils dédiés aux traitements et aux données. Le **MCD(Modèle Conceptuel des Données)** est un des outils majeurs concernant les données.

## définition de MCD (Modèle Conceptuel des Données)

Le **MCD** est une représentation graphique de haut niveau qui permet facilement et simplement de comprendre comment les différents éléments sont liés entre eux. Il décrit les données utilisées par le système d'information et leurs relations. Les informations sont représentées logiquement en utilisant un ensemble de règles et de diagrammes codifiés :

- Les **entités** (1 rectangle = 1 objet)
- Les **propriétés** (la liste des données de l'entité)
- Les **Relations** qui expliquent et précisent comment les entités sont reliées entre elles (les ovales avec leurs "pattes" qui se rattachent aux entités)
- Les **Cardinalités** (les petits chiffres)

Le MCD est la base de travail et sera ensuite utilisé par les autres outils de Merise à savoir le **MLD** et le **MPD**. Le MCD constitue une étape très importante de la modélisation. Si elle est mal réalisée, des erreurs en cascade se produiront et rejailliront sur le MLD, le MPD et enfin sur la base de données.

## Étapes de création d'un MCD

- 1 Obtenir les règles de gestion du besoin à informatiser \*_Exemple : un client a un numéro et une adresse email. Un devis ne peut pas être émis si aucun client ne lui est rattaché_
- 2 Ensuite recenser toutes les données à informatiser dans un dictionnaire des données;
- 3 Comprendre les relations et les dépendances entre les données
- 4 Constructuion du MCD

## Différentes Cardinalités

- **0,1** : au minimum 0, au maximum 1 seule valeur (CIF)
- **1,1** : au minimum 1, au maximum 1 seule valeur (CIF)
- **0,n** : au minimum 0, au maximum plusieurs valeurs ou aucunes (CIM)
- **1,n** : au minimum 1, au maximum plusieurs valeurs (CIM)

### CIM

Une **CIM** ou **Contrainte d'Intégrité Multiple** est un type d'assocation entre 2 entités minimum. Sur un MCD, elle se caractérise par l'absence de 1 en cardinalité maximale. Par déduction, on ne peut avoir que 0,n ou 1,n en cardinalité. À ne pas confondre avec le **CIF**.

Concrètement, une CIM représente un couple unique auquel on peut affecter des propriétés particulières. On dit alors que la CIM est porteuse de propriétés (ou de données). Non hiérarchique, la CIM est construite à partir des **identifiants** des entités qui lui sont liées.

### CIF

Une **CIF** ou **Contrainte d'Intégrité Fonctionnelle** est un type d'association entre 2 entités.

Elle se caractérise par un 1 en cardinalité supérieur (0,1 ou 1,1) sur une des pattes de la relation. On dit alors que la relation est **porteuse d'une dépendence fonctionnelle**. Une CIF indique donc une dépendance. Une des entités de l'association est déterminée pas la connaissance d'une ou plusieurs autres entité présente dans l'association. Cette association forte et hiérarchique. Sans entité parent, il ne peut pas y avoir d'entité enfant. À ne pas confondre avec une **CIM**.

Une CIF se tranforme alors lors du passage en MLD/MPD en une **clé étrangère**. Cette clé étrangère est un **champ** ajouté à la table située du côté du 1 en cardinalité maximale qui reprend le champ **clé primaire** de la table située de l’autre côté de la relation.

## Cardinalités et associations CIF/CIM

Les cardinalités sont des caractères (0,1,n) qui fonctionnent par couple et qui sont présents de chaque côté d'une association. Même si on l'utilise surtout au pluriel, il reste quand même possible de parler d'une cardinalité lorsqu'on évoque un côté de l'association. Grâce aux cardinalités on peut obtenir des indications très intéressantes et permettent par la suite de construire la base de données :

- avec la création de clés étrangères dans le cas d'une **CIF**
- avec la création d'une table intermédiaire dans le cas d'une **CIM**

## Cardinalités et types d'associations

- **Association hiérarchique** : Lorsqu'une association à une cardinalité maximale à 1 d'un côté et une cardianalité maximale à n de l'autre côté. On a une dépendance fonctionnelle (une CIF)
- **Association non hiérachique** : Lorsqu'une association à n en cardinalité maximale de chaque côté de l'association.


