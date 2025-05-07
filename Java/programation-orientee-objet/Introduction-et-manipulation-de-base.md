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

## Orientée Objet

### Définition

La programmation orientée objet (POO) est un paradigme de programmation qui se base sur le concept d'objets, qui peuvent contenir des données et du code. Les objets contiennent des attributs (données) et des méthodes (procédures). La POO classe et catégorise les données et les comportements en utilisant des modèles appelés classes.

### Caractéristiques principales

#### Les quatre piliers de la POO

1. **Encapsulation**

   - Regroupe les données (attributs) et les comportements (méthodes) dans une seule unité (la classe)
   - Protège les données en limitant l'accès direct (modificateurs d'accès : public, private, protected)
   - Expose une interface publique tout en cachant les détails d'implémentation

2. **Héritage**

   - Permet à une classe (sous-classe) d'hériter des propriétés et méthodes d'une autre classe (super-classe)
   - Favorise la réutilisation du code et établit une relation "est un" entre classes
   - Permet de créer une hiérarchie de classes

3. **Polymorphisme**

   - Capacité d'un objet à prendre plusieurs formes
   - Permet d'appeler une méthode sur des objets de différentes classes, mais produisant des comportements appropriés à chaque classe
   - Types: surcharge (overloading) et redéfinition (overriding)

4. **Abstraction**
   - Simplification d'un système complexe en le réduisant à ses composants essentiels
   - Cache les détails complexes et expose uniquement les fonctionnalités nécessaires
   - Utilise des classes abstraites et des interfaces pour définir des contrats

### Exemple en Java - Système de gestion de bibliothèque

```java
// Classe abstraite représentant un document de bibliothèque
abstract class Document {
    // Attributs communs à tous les documents
    protected String titre;
    protected String auteur;
    protected String reference;
    protected boolean emprunte;

    // Constructeur
    public Document(String titre, String auteur, String reference) {
        this.titre = titre;
        this.auteur = auteur;
        this.reference = reference;
        this.emprunte = false;
    }

    // Méthodes d'accès (getters)
    public String getTitre() { return titre; }
    public String getAuteur() { return auteur; }
    public String getReference() { return reference; }
    public boolean estEmprunte() { return emprunte; }

    // Méthodes communes à tous les documents
    public void emprunter() {
        if (!emprunte) {
            emprunte = true;
            System.out.println("Le document " + titre + " a été emprunté.");
        } else {
            System.out.println("Le document " + titre + " est déjà emprunté.");
        }
    }

    public void retourner() {
        if (emprunte) {
            emprunte = false;
            System.out.println("Le document " + titre + " a été retourné.");
        } else {
            System.out.println("Le document " + titre + " n'est pas emprunté.");
        }
    }

    // Méthode abstraite que les sous-classes doivent implémenter
    public abstract void afficherDetails();

    // Méthode abstraite pour calculer la durée de prêt
    public abstract int getDureePretJours();
}

// Sous-classe représentant un livre
class Livre extends Document {
    // Attributs spécifiques aux livres
    private int nombrePages;
    private String editeur;

    // Constructeur
    public Livre(String titre, String auteur, String reference, int nombrePages, String editeur) {
        super(titre, auteur, reference);  // Appel au constructeur de la classe parente
        this.nombrePages = nombrePages;
        this.editeur = editeur;
    }

    // Implémentation de la méthode abstraite
    @Override
    public void afficherDetails() {
        System.out.println("=== LIVRE ===");
        System.out.println("Titre: " + titre);
        System.out.println("Auteur: " + auteur);
        System.out.println("Référence: " + reference);
        System.out.println("Éditeur: " + editeur);
        System.out.println("Nombre de pages: " + nombrePages);
        System.out.println("Statut: " + (emprunte ? "Emprunté" : "Disponible"));
    }

    // Implémentation de la méthode abstraite pour la durée de prêt
    @Override
    public int getDureePretJours() {
        return 21;  // 3 semaines pour les livres
    }
}

// Sous-classe représentant un DVD
class DVD extends Document {
    // Attributs spécifiques aux DVD
    private int dureeMinutes;
    private String categorie;

    // Constructeur
    public DVD(String titre, String auteur, String reference, int dureeMinutes, String categorie) {
        super(titre, auteur, reference);  // Appel au constructeur de la classe parente
        this.dureeMinutes = dureeMinutes;
        this.categorie = categorie;
    }

    // Implémentation de la méthode abstraite
    @Override
    public void afficherDetails() {
        System.out.println("=== DVD ===");
        System.out.println("Titre: " + titre);
        System.out.println("Réalisateur: " + auteur);
        System.out.println("Référence: " + reference);
        System.out.println("Durée: " + dureeMinutes + " minutes");
        System.out.println("Catégorie: " + categorie);
        System.out.println("Statut: " + (emprunte ? "Emprunté" : "Disponible"));
    }

    // Implémentation de la méthode abstraite pour la durée de prêt
    @Override
    public int getDureePretJours() {
        return 7;  // 1 semaine pour les DVD
    }
}

// Classe principale qui démontre l'utilisation
public class Bibliotheque {
    public static void main(String[] args) {
        // Création d'objets
        Livre livre = new Livre("Le Petit Prince", "Antoine de Saint-Exupéry", "L12345", 96, "Gallimard");
        DVD dvd = new DVD("Inception", "Christopher Nolan", "D54321", 148, "Science-Fiction");

        // Utilisation du polymorphisme - même méthode, différents comportements
        Document[] documents = {livre, dvd};

        for (Document doc : documents) {
            // Affichage des détails de chaque document (polymorphisme)
            doc.afficherDetails();

            // Affichage de la durée de prêt (polymorphisme)
            System.out.println("Durée de prêt: " + doc.getDureePretJours() + " jours");

            // Emprunt du document
            doc.emprunter();

            System.out.println();
        }

        // Tentative d'emprunt d'un document déjà emprunté
        livre.emprunter();

        // Retour d'un document
        dvd.retourner();

        // Nouvelle tentative d'emprunt après retour
        dvd.emprunter();
    }
}
```

### Différences avec la programmation procédurale

- **Organisation** : La POO organise le code autour des objets et de leurs interactions, tandis que la programmation procédurale l'organise autour des fonctions
- **Liaison données-fonctions** : En POO, les données et les fonctions qui les manipulent sont regroupées dans des classes, alors qu'en programmation procédurale, elles sont généralement séparées
- **État** : En POO, l'état est encapsulé dans des objets, en programmation procédurale, il est souvent représenté par des variables globales ou passé en arguments
- **Réutilisation** : La POO favorise la réutilisation via l'héritage et la composition, la programmation procédurale via les appels de fonctions

### Avantages

- **Modularité** : Le code est divisé en classes autonomes et réutilisables
- **Réutilisabilité** : L'héritage et la composition permettent de réutiliser le code existant
- **Extensibilité** : Facilité pour ajouter de nouvelles fonctionnalités sans modifier le code existant
- **Maintenabilité** : Organisation qui facilite la maintenance et les évolutions
- **Modélisation** : Représentation plus naturelle du monde réel

### Inconvénients

- **Complexité** : Courbe d'apprentissage plus élevée que la programmation procédurale
- **Performance** : Peut être légèrement moins efficace en termes de performance pour certaines applications
- **Surconception** : Risque de créer des hiérarchies de classes trop complexes
- **Taille** : Les programmes orientés objet peuvent être plus volumineux

## Phrase technique à retenir

**"La programmation orientée objet encapsule les données et les comportements dans des entités cohésives appelées objets, permettant ainsi de modéliser les relations du monde réel à travers l'héritage, le polymorphisme et l'abstraction, ce qui favorise la réutilisation du code et réduit la complexité des systèmes."**

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
