# découverte des types de programmation posssible

## Impérative

### Définition

La programmation impérative est un paradigme de programmation qui décrit les calculs comme une séquence d'instructions qui modifient l'état du programme. Elle se caractérise par des affectations de variables et des structures de contrôle séquentielles qui définissent comment le programme s'exécute étape par étape.

### Caractéristiques principales

- **Séquentielle**: Les instructions sont exécutées dans un ordre prédéfini
- **État mutable**: Les variables peuvent changer de valeur au cours de l'exécution
- **Structures de contrôle**: Utilisation de boucles et conditions pour diriger l'exécution
- **Accent sur le "comment"**: Décrit précisément comment arriver au résultat

### Exemple en Java

```java
public class SommeEntiers {
    // Fonction qui calcule la somme des entiers de 1 à n
    public static int calculerSomme(int n) {
        int somme = 0;  // Initialisation de la variable somme

        for (int i = 1; i <= n; i++) {  // Boucle qui parcourt les entiers de 1 à n
            somme = somme + i;  // Modification de l'état de la variable somme
        }

        return somme;  // Retour du résultat final
    }

    public static void main(String[] args) {
        int nombre = 10;
        int resultat = calculerSomme(nombre);
        System.out.println("La somme des entiers de 1 à " + nombre + " est " + resultat);
    }
}
```

### Avantages

- Proche de la machine, souvent plus efficace en termes de performances
- Intuitive pour les débutants car proche de la pensée procédurale humaine
- Adaptée pour les tâches algorithmiques séquentielles
- Plus facile à optimiser au niveau machine

### Inconvénients

- Peut devenir difficile à maintenir sur de grands projets
- Risque élevé d'effets de bord dus à la mutabilité des variables
- Moins adaptée aux problèmes complexes nécessitant des abstractions
- Difficulté à représenter certaines relations complexes entre données

## Phrase technique à retenir

**"La programmation impérative manipule l'état du programme à travers une séquence d'instructions qui modifient explicitement les données en mémoire, par opposition aux paradigmes déclaratifs qui décrivent ce qui doit être calculé plutôt que comment le calculer."**

## Procédurale

### Définition

La programmation procédurale est un paradigme de programmation qui étend la programmation impérative en organisant le code en procédures (ou fonctions/sous-programmes) qui peuvent être appelées à tout moment. Elle met l'accent sur la décomposition d'un programme en modules réutilisables, chacun accomplissant une tâche spécifique.

### Caractéristiques principales

- **Décomposition fonctionnelle** : Division du programme en procédures/fonctions
- **Réutilisation du code** : Les procédures peuvent être appelées plusieurs fois
- **Portée des variables** : Introduction de variables locales et globales
- **Abstraction procédurale** : Cache les détails d'implémentation derrière des interfaces de fonction
- **Modularité** : Organisation du code en modules logiques

### Exemple en Java

```java
public class CalculMathematique {
    // Variable globale accessible par toutes les méthodes de la classe
    public static final double PI = 3.14159;

    // Procédure principale
    public static void main(String[] args) {
        // Appel de différentes procédures
        int somme = calculerSomme(10);
        afficherResultat("Somme des entiers de 1 à 10", somme);

        double aire = calculerAireCercle(5);
        afficherResultat("Aire d'un cercle de rayon 5", aire);

        int factorielle = calculerFactorielle(6);
        afficherResultat("Factorielle de 6", factorielle);
    }

    // Procédure qui calcule la somme des entiers de 1 à n
    public static int calculerSomme(int n) {
        int somme = 0;
        for (int i = 1; i <= n; i++) {
            somme += i;
        }
        return somme;
    }

    // Procédure qui calcule l'aire d'un cercle
    public static double calculerAireCercle(double rayon) {
        return PI * rayon * rayon;
    }

    // Procédure qui calcule la factorielle d'un nombre
    public static int calculerFactorielle(int n) {
        if (n <= 1) {
            return 1;
        }
        return n * calculerFactorielle(n - 1);  // Appel récursif
    }

    // Procédure pour afficher un résultat avec un libellé
    public static void afficherResultat(String libelle, double valeur) {
        System.out.println(libelle + " : " + valeur);
    }
}
```

### Différences avec la programmation impérative pure

- La programmation procédurale organise les instructions en blocs réutilisables (procédures), alors que la programmation impérative pure se concentre sur la séquence d'instructions.
- Elle encourage une meilleure structuration du code et facilite la maintenance.
- Elle permet une abstraction plus élevée en cachant les détails d'implémentation.

### Avantages

- Meilleure organisation du code que la programmation impérative pure
- Réutilisation des fonctions, réduction de la duplication
- Facilité de débogage (chaque fonction peut être testée séparément)
- Meilleure lisibilité et maintenabilité
- Abstraction qui simplifie la résolution de problèmes complexes

### Inconvénients

- Partage potentiel d'état global entre fonctions
- Moins flexible que la programmation orientée objet pour modéliser des systèmes complexes
- Séparation moins claire entre données et comportements
- Peut devenir difficile à gérer pour de très grands projets

## Phrase technique à retenir

**"La programmation procédurale décompose un problème en procédures modulaires et réutilisables qui encapsulent des séquences d'instructions, permettant ainsi une abstraction fonctionnelle tout en conservant le flux de contrôle impératif sous-jacent."**
