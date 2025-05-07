# 🧠 Mémo POO – Les Objets

## 🧾 Définition

Un objet est une instance concrète d’une classe. C’est une entité créée à partir d’un modèle (la classe), qui possède ses propres valeurs pour les attributs définis par la classe, et peut exécuter ses méthodes.

⸻

## ⭐ Caractéristiques principales

• Un objet est unique : il a son propre état (valeurs d’attributs).
• Il est créé à partir d’une classe avec le mot-clé new en Java.
• Il peut interagir avec d’autres objets.
• Il est composé :
• d’un état → les valeurs de ses attributs
• d’un comportement → les méthodes qu’il peut exécuter
• d’une identité → il est distinct des autres objets, même s’ils ont les mêmes valeurs

⸻

## 📚 Exemple en Java : Objets de livres

```Java
public class Livre {
String titre;
String auteur;

    public Livre(String titre, String auteur) {
        this.titre = titre;
        this.auteur = auteur;
    }

    public void afficherInfos() {
        System.out.println("Titre : " + titre + ", Auteur : " + auteur);
    }

}

public class Main {
public static void main(String[] args) {
Livre livre1 = new Livre("1984", "George Orwell");
Livre livre2 = new Livre("Le Petit Prince", "Antoine de Saint-Exupéry");

        livre1.afficherInfos();
        livre2.afficherInfos();
    }

}
```

⸻

## ✅ Avantages

- Représente des entités concrètes de manière claire.
- Permet de manipuler des données et des comportements ensemble.
- Favorise la réutilisation et l’organisation du code.

⸻

## ❌ Inconvénients

- Peut entraîner une consommation mémoire importante si trop d’objets sont créés.
- Leur gestion nécessite une bonne conception en amont.

⸻

## 💡 Phrase technique à retenir

Un objet est une instance vivante et indépendante d’une classe.

⸻

## 🧪 Récapitulatif – Quiz sur les Objets

1. Qu’est-ce qu’un objet en POO ?

Réponse correcte :
Un objet est une instance d’une classe, avec son propre état et ses comportements.

⸻

2. Dans l’exemple précédent, combien d’objets ont été créés ?

Réponse correcte :
Deux objets : livre1 et livre2.

⸻

3. Quelle ligne de code permet de créer un objet de la classe Livre ?

Réponse correcte :

Livre monLivre = new Livre("1984", "George Orwell");

⸻

4. Quelle est la différence entre une classe et un objet ?

Réponse correcte :

La classe est un plan, l’objet est le résultat concret de ce plan (l’instance).

⸻

5. Que contient un objet une fois créé ?

Réponse correcte :

Il contient des valeurs propres pour ses attributs et peut utiliser les méthodes définies dans la classe.

⸻

Souhaites-tu qu’on aborde ensuite l’instanciation ou l’encapsulation ?
