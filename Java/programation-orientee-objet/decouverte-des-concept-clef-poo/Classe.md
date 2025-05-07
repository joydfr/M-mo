# 🧠 Mémo POO – Les Classes

## 🧾 Définition

Une classe est un modèle (ou plan de construction) permettant de créer des objets. Elle définit les attributs (état) et les méthodes (comportements) que possèdent ses objets.

⸻

## ⭐ Caractéristiques principales

- Modélise un concept du monde réel ou abstrait.
- Peut contenir :
  - des attributs (variables membres)
  - des méthodes (fonctions membres)
  - Sert à créer des objets (instances).
  - Permet l’encapsulation des données.

⸻

## 📚 Exemple en Java : Gestion d’une bibliothèque

```java
public class Livre {
    // Attributs
    String titre;
    String auteur;
    boolean estDisponible;

    // Constructeur
    public Livre(String titre, String auteur) {
        this.titre = titre;
        this.auteur = auteur;
        this.estDisponible = true;
    }

    // Méthode pour emprunter un livre
    public void emprunter() {
        if (estDisponible) {
            estDisponible = false;
            System.out.println(titre + " a été emprunté.");
        } else {
            System.out.println(titre + " n'est pas disponible.");
        }
    }

    // Méthode pour retourner un livre
    public void retourner() {
        estDisponible = true;
        System.out.println(titre + " a été retourné.");
    }
}

```

⸻

## ✅ Avantages

- Réutilisation du code avec l’instanciation.
- Modularité : chaque classe a une responsabilité claire.
- Maintenance facilitée.
- Favorise la modélisation fidèle du réel.

⸻

## ❌ Inconvénients

- Peut être complexe à concevoir au départ.
- Moins adapté aux petits scripts simples.
- Nécessite une bonne compréhension des relations entre objets.

⸻

💡 Phrase technique à retenir

Une classe est un plan, un objet est une construction à partir de ce plan.

⸻

📝 Récapitulatif – Quiz sur les Classes en Java

1. Qu’est-ce qu’une classe en POO ?

Réponse correcte :
b) Un modèle qui permet de créer des objets

Une classe sert de plan pour définir les attributs et comportements des objets à créer.

⸻

2. Dans l’exemple de gestion de bibliothèque, quel est l’état initial de l’attribut estDisponible d’un livre ?

Réponse correcte :
true

Bien que estDisponible soit un booléen, sa valeur initiale est explicitement définie dans le constructeur :

this.estDisponible = true;

⸻

3. Comment appelle-t-on une classe dans un programme Java pour créer un objet ?

Donne un exemple de syntaxe en une ligne.

Réponse correcte :

Livre monLivre = new Livre("1984", "George Orwell");

On utilise le mot-clé new pour instancier un objet à partir d’une classe.

⸻

4. Dans la méthode emprunter, que se passe-t-il si le livre n’est pas disponible ?

Réponse correcte :

La méthode affiche simplement un message :

System.out.println(titre + " n'est pas disponible.");

L’état de l’objet ne change pas, il reste indisponible.

⸻

5. Pourquoi utilise-t-on des classes au lieu de tout écrire dans la méthode main ?

Réponse correcte (exemple) :

On utilise des classes pour structurer le code, permettre la réutilisation, et créer plusieurs objets distincts avec les mêmes propriétés.

⸻
