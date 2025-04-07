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
