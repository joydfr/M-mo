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
