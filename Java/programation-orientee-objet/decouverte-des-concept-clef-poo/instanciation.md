# 🧠 Mémo POO – L’instanciation

## 🧾 Définition

L’instanciation est le processus de création d’un objet à partir d’une classe. Une fois instancié, l’objet a sa propre existence en mémoire, avec ses attributs et ses méthodes.

⸻

## ⭐ Caractéristiques principales

• L’instanciation se fait avec le mot-clé new en Java.
• Chaque objet instancié a ses propres valeurs d’attributs.
• On peut instancier autant d’objets qu’on veut à partir d’une même classe.
• L’instanciation appelle automatiquement le constructeur de la classe.

⸻

## 📚 Exemple en Java – Instanciation d’objets

```java
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

Dans cet exemple, livre1 et livre2 sont deux instances différentes de la classe Livre.

⸻

## ✅ Avantages

• Permet de créer autant d’objets que nécessaire à partir d’un seul modèle (la classe).
• Chaque objet est indépendant : ses attributs ne dépendent pas des autres.
• L’instanciation rend possible la modélisation du monde réel dans le code.

⸻

## ❌ Inconvénients

• Peut consommer beaucoup de mémoire si trop d’objets sont instanciés inutilement.
• Une instanciation incorrecte (sans constructeur adapté) peut générer des erreurs.

⸻

## 💡 Phrase technique à retenir

Instancier une classe, c’est créer un objet réel à partir d’un modèle abstrait.

⸻

## 🧪 Récapitulatif – Quiz sur l’instanciation

1. Qu’est-ce que l’instanciation ?

Réponse correcte :
C’est la création d’un objet concret à partir d’une classe.

⸻

2. Quel mot-clé Java permet d’instancier une classe ?

Réponse correcte :
new

⸻

3. Quelle ligne instancie correctement un objet de la classe Livre ?

Réponse correcte :

Livre monLivre = new Livre("1984", "George Orwell");

⸻

4. Que se passe-t-il lors de l’instanciation ?

Réponse correcte :

Le constructeur de la classe est appelé, et l’objet est créé en mémoire avec ses attributs.

⸻

5. Peut-on instancier plusieurs objets à partir d’une même classe ?

Réponse correcte :
Oui, chaque objet est unique et indépendant même s’il vient de la même classe.

⸻
