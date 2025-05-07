# Découverte des types de programmation possibles

## Impératif

### 🧾 Définition

La programmation impérative consiste à décrire comment faire les choses étape par étape. Elle repose sur des instructions séquentielles qui modifient un état global via des variables.

⸻

### ✨ Caractéristiques principales

- 📋 Instructions séquentielles
- 🧠 État global modifiable
- 🧮 Variables, affectations, boucles, conditions
- 🔄 Le programme contrôle directement l’exécution
- 🚧 Approche bas niveau, proche de la machine

⸻

### 🧪 Exemple en Java : Compter les livres disponibles

```java
public class Bibliotheque {
    public static void main(String[] args) {
        int totalDisponibles = 0;
        boolean[] disponibilites = {true, false, true};

        for (int i = 0; i < disponibilites.length; i++) {
            if (disponibilites[i]) {
                totalDisponibles++;
            }
        }

        System.out.println("Livres disponibles : " + totalDisponibles);
    }
}
```

⸻

### ⚔️ Comparaison avec d’autres paradigmes

Paradigme État mutable Utilise des objets Contrôle de flux Fonctions comme 1ère classe
Fonctionnel 🚫 Non 🚫 Non ✅ Oui (via recursion) ✅ Oui
Procédural ✅ Oui 🚫 Non ✅ Oui 🚫 Non
Orienté objet ✅ Oui ✅ Oui ✅ Oui 🚫 Non
Impératif ✅ Oui 🚫 Variable ✅ Oui 🚫 Non

⸻

### ✅ Avantages

- 🧱 Simple à comprendre pour les débutants
- ⚙️ Contrôle précis du flux d’exécution
- 🔧 Performances optimales dans certains contextes

⸻

### ❌ Inconvénients

- ⚠️ Risques d’erreurs avec variables globales
- ❌ Moins lisible dans les grands projets
- 🧩 Difficulté à tester à cause des effets de bord

⸻

### 🧩 Phrase technique à retenir

La programmation impérative décrit les opérations à effectuer pas à pas pour modifier l’état du programme au fil de l’exécution.

⸻

### 🧠 Test rapide : Quiz de vérification

- 1. Que signifie “impératif” ?
  - **_Donner des ordres précis à la machine sur ce qu’elle doit faire._**
- 2. Pourquoi les effets de bord sont-ils fréquents ici ?
  - **_Car l’état est modifié constamment via des variables._**
- 3. Avantage / inconvénient ?
  - ✅ Avantage :
    - **_Facile à écrire et rapide à exécuter._**
  - ❌ Inconvénient :
    - **_Moins structuré, plus sujet aux erreurs avec des programmes complexes._**
- 4. Quelle instruction contrôle le flux dans l’exemple ?
     - **_La boucle for et le if._**
- 5. Différence entre impératif et fonctionnel ?
  - **_L’impératif modifie l’état via des instructions, le fonctionnel transforme les données sans les modifier._**

⸻

## Procédural

### 🧾 Définition

La programmation procédurale est un sous-ensemble de l’impératif, structurée autour de procédures ou fonctions. Le code est organisé en blocs logiques réutilisables pour améliorer la lisibilité et la modularité.

⸻

### ✨ Caractéristiques principales

- 🧱 Découpage en procédures / fonctions
- 🔁 Réutilisation de code facilitée
- 📋 Instructions exécutées séquentiellement
- 🚫 Moins de duplication de code
- 📦 Organisation par logique métier

⸻

### 🧪 Exemple en Java : Modularisation d’une bibliothèque

```java
public class Bibliotheque {

    public static void main(String[] args) {
        boolean[] disponibilites = {true, false, true};
        int total = compterDisponibles(disponibilites);
        System.out.println("Livres disponibles : " + total);
    }

    public static int compterDisponibles(boolean[] livres) {
        int count = 0;
        for (boolean disponible : livres) {
            if (disponible) {
                count++;
            }
        }
        return count;
    }
}
```

⸻

### ⚔️ Comparaison avec d’autres paradigmes

Paradigme État mutable Utilise des objets Contrôle de flux Fonctions comme 1ère classe
Fonctionnel 🚫 Non 🚫 Non ✅ Oui (via recursion) ✅ Oui
Procédural ✅ Oui 🚫 Non ✅ Oui 🚫 Non
Orienté objet ✅ Oui ✅ Oui ✅ Oui 🚫 Non
Impératif ✅ Oui 🚫 Variable ✅ Oui 🚫 Non

⸻

### ✅ Avantages

- 🧩 Code mieux organisé que l’impératif brut
- 🔄 Réutilisation des fonctions
- 🛠️ Facile à tester par morceaux

⸻

### ❌ Inconvénients

- 📦 Moins structuré qu’un modèle objet
- ⚠️ L’état reste global s’il n’est pas bien géré
- 🚧 Difficulté à modéliser des systèmes complexes

⸻

### 🧩 Phrase technique à retenir

La programmation procédurale décompose un programme en fonctions pour structurer l’exécution tout en gardant le modèle impératif sous-jacent.

⸻

### 🧠 Test rapide : Quiz de vérification

- 1.Quelle est la différence entre procédural et impératif ?
  - **_Le procédural structure le code en fonctions réutilisables, l’impératif pur reste linéaire._**
- 2.Qu’est-ce qu’une procédure ?
  - **_Une fonction qui exécute une série d’instructions._**
- 3.Avantage / inconvénient ?
  - ✅ Avantage :
    - **_Code modulaire, plus lisible et réutilisable._**
  - ❌ Inconvénient : - **_Moins adapté à la modélisation d’entités complexes._**
- 4.Quelle est la fonction principale dans l’exemple ?
  - **_compterDisponibles._**
- 5.Différence avec l’objet ?
  - **_Le procédural n’unit pas données et comportements, contrairement à la POO._**

## Orientée Objet

### 🧾 Définition

La programmation orientée objet (POO) est un paradigme qui organise le code autour d’objets représentant des entités du monde réel. Ces objets combinent état (attributs) et comportement (méthodes) et interagissent entre eux pour exécuter la logique d’un programme.

⸻

### ✨ Caractéristiques principales

- 🧱 Objets : entités combinant données et fonctions.
- 🧬 Encapsulation : les données sont protégées dans des classes.
- 🧩 Héritage : possibilité de créer des classes filles à partir de classes mères.
- 🔁 Polymorphisme : possibilité d’utiliser le même nom de méthode avec des comportements différents.
- 🧠 Abstraction : masquage de la complexité via des interfaces ou classes abstraites.

⸻

### 🧪 Exemple en Java : Gestion d’une bibliothèque

```java
public class Livre {
    private String titre;
    private String auteur;
    private boolean disponible;

    public Livre(String titre, String auteur, boolean disponible) {
        this.titre = titre;
        this.auteur = auteur;
        this.disponible = disponible;
    }

    public void emprunter() {
        if (disponible) {
            disponible = false;
            System.out.println(titre + " emprunté.");
        } else {
            System.out.println(titre + " non disponible.");
        }
    }

    public String getTitre() { return titre; }
}

public class Bibliotheque {
    public static void main(String[] args) {
        Livre livre = new Livre("1984", "George Orwell", true);
        livre.emprunter();
    }
}
```

⸻

### ⚔️ Comparaison avec d’autres paradigmes

Paradigme État mutable Utilise des objets Contrôle de flux Fonctions comme 1ère classe
Fonctionnel 🚫 Non 🚫 Non ✅ Oui (via recursion) ✅ Oui
Procédural ✅ Oui 🚫 Non ✅ Oui 🚫 Non
Orienté objet ✅ Oui ✅ Oui ✅ Oui 🚫 Non
Impératif ✅ Oui 🚫 Variable ✅ Oui 🚫 Non

⸻

### ✅ Avantages

    •	🌍 Modélisation proche du monde réel
    •	🔐 Séparation claire des responsabilités via les classes
    •	🔄 Réutilisation du code avec héritage et polymorphisme

⸻

### ❌ Inconvénients

    •	⚙️ Complexité potentielle avec surabondance de classes
    •	🧱 Couplage fort si mal structuré
    •	🐘 Peut être lourd pour de petits scripts simples

⸻

### 🧩 Phrase technique à retenir

En programmation orientée objet, tout est objet : chaque entité possède un état et des comportements encapsulés, favorisant la modularité et la réutilisabilité du code.

⸻

### 🧠 Test rapide : Quiz de vérification

- 1 Qu’est-ce qu’un objet ?
  - **_Une instance d’une classe, regroupant des données (attributs) et des fonctions (méthodes)._**
- 2 À quoi sert l’encapsulation ?
  - **_À protéger l’accès aux données internes d’un objet et à imposer des règles d’interaction via des méthodes._**
- 3.Avantage et inconvénient du paradigme orienté objet ?
  - ✅ Avantage :
    - **_Structure claire facilitant la maintenance et la réutilisation._**
  - ❌ Inconvénient :
    - **_Surcharge inutile pour des programmes très simples ou scripts._**
- 4.Dans l’exemple Java, quelle méthode modifie l’état interne ?
  - **_La méthode emprunter() modifie l’attribut disponible._**
- 5.Différence entre POO et fonctionnel ?
  - **_La POO structure le code autour d’objets avec états, alors que le fonctionnel repose sur des fonctions sans état mutable._**

⸻

## Fonctionnelle

### 🧾 Définition

La programmation fonctionnelle est un paradigme de programmation basé sur l’utilisation de fonctions pures et l’absence d’effets de bord. Elle considère les calculs comme l’évaluation de fonctions mathématiques et évite l’état mutable et les données partagées.

⸻

### ✨ Caractéristiques principales

- 📌 Fonctions pures : même entrée → même sortie, sans effet de bord.
- 🔁 Immutabilité : les données ne changent pas après leur création.
- 🔄 Recursion : préférée aux boucles classiques (for, while).
- 🧱 First-class functions : les fonctions sont des valeurs (on peut les passer en paramètres, les retourner, etc.).
- 📚 Évaluation paresseuse (lazy evaluation) : calcul des résultats uniquement lorsque nécessaire.

⸻

### 🧪 Exemple en Java : Gestion d’une bibliothèque

Java n’est pas un langage purement fonctionnel, mais il permet un style fonctionnel depuis Java 8 avec les lambdas et les streams :

```java
import java.util.*;
import java.util.stream.*;

public class Bibliotheque {

    public static void main(String[] args) {
        List<Livre> livres = Arrays.asList(
            new Livre("1984", "George Orwell", true),
            new Livre("Le Meilleur des mondes", "Aldous Huxley", false),
            new Livre("Fahrenheit 451", "Ray Bradbury", true)
        );

        List<String> titresDisponibles = livres.stream()
            .filter(Livre::isDisponible)  // fonction pure
            .map(Livre::getTitre)         // transformation immuable
            .collect(Collectors.toList());

        titresDisponibles.forEach(System.out::println);
    }
}

class Livre {
    private String titre;
    private String auteur;
    private boolean disponible;

    public Livre(String titre, String auteur, boolean disponible) {
        this.titre = titre;
        this.auteur = auteur;
        this.disponible = disponible;
    }

    public String getTitre() { return titre; }
    public boolean isDisponible() { return disponible; }
}


```

⸻

### ⚔️ Comparaison avec d’autres paradigmes

Paradigme État mutable Utilise des objets Contrôle de flux Fonctions comme 1ère classe
Fonctionnel 🚫 Non 🚫 Non ✅ Oui (via recursion) ✅ Oui
Procédural ✅ Oui 🚫 Non ✅ Oui 🚫 Non
Orienté objet ✅ Oui ✅ Oui ✅ Oui 🚫 Non
Impératif ✅ Oui 🚫 Variable ✅ Oui 🚫 Non

⸻

### ✅ Avantages

- 🔒 Moins de bugs liés aux effets de bord
- 🔁 Code plus prévisible et testable
- 🧩 Programmation modulaire et composable
- 🚀 Parallélisation facilitée

⸻

❌ Inconvénients

- 🧠 Courbe d’apprentissage plus élevée
- 🐌 Moins performant dans certains cas (recursion vs boucles)
- 📏 Moins naturel en Java, langage non-fonctionnel pur

⸻

### 🧩 Phrase technique à retenir

En programmation fonctionnelle, le code est une suite de transformations immuables sur des données, exprimées par des fonctions pures sans effet de bord.

⸻

### 🧠 Test rapide : Quiz de vérification

- 1. Qu’est-ce qu’une fonction pure ?
  - **_Oui, Livre::isDisponible est bien une fonction pure :
    Elle ne modifie rien, elle lit simplement une donnée (la disponibilité).
    Elle respecte donc le principe “même entrée → même sortie”._**
- 2. Pourquoi la programmation fonctionnelle facilite-t-elle la programmation parallèle ?
  - **_La programmation fonctionnelle facilite la parallélisation car les fonctions pures ne modifient pas l’état global, ce qui permet d’exécuter plusieurs fonctions en parallèle sans risque de conflit ou de bug lié à des accès concurrents._**
- 3. Donne un avantage et un inconvénient de ce paradigme.

  - ✅ Avantage :

    - **_Code plus prévisible et testable
      Les fonctions pures permettent d’isoler facilement la logique et de tester sans configuration complexe, car elles ne dépendent pas d’un état externe._**

  - ❌ Inconvénient :

  - **_Moins performant dans certains cas
    Par exemple, la récursion (souvent utilisée à la place des boucles) peut consommer plus de mémoire et être moins efficace, surtout sans optimisation comme la récursion terminale._**

- 4. Dans l’exemple Java, quelle méthode assure l’absence d’effet de bord ?

  - **_La méthode qui assure l’absence d’effet de bord, c’est Livre::isDisponible._**

    - 👉 Pourquoi ?
      - Elle ne modifie rien.
      - Elle renvoie toujours la même valeur pour un livre donné.
      - Elle n’interagit pas avec le monde extérieur (pas d’affichage, pas de fichiers, pas de saisie utilisateur, etc.).

- 5. Quelle différence majeure entre la programmation fonctionnelle et orientée objet ?
  - **_La programmation orientée objet repose sur la modélisation du monde avec des objets qui possèdent des états (attributs) et des comportements (méthodes)._**
  - **_La programmation fonctionnelle, elle, modélise le programme comme une suite de fonctions qui transforment des données immuables, sans modifier l’état._**

⸻
