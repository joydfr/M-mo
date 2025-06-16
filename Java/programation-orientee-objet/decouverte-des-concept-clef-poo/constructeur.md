

🧠 Mémo POO – Les Constructeurs

🧾 Définition

Un constructeur est une méthode spéciale d’une classe, appelée automatiquement lors de l’instanciation d’un objet. Il sert à initialiser les attributs de l’objet nouvellement créé.

⸻

⭐ Caractéristiques principales
	•	Il porte exactement le même nom que la classe.
	•	Il n’a pas de type de retour, pas même void.
	•	Il peut accepter des paramètres ou être sans paramètre (constructeur par défaut).
	•	Il est souvent utilisé pour donner une valeur initiale aux attributs.

⸻

📚 Exemple en Java – Constructeur dans une classe Livre

public class Livre {
    String titre;
    String auteur;

    // Constructeur
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
        livre1.afficherInfos();
    }
}

Le constructeur public Livre(String titre, String auteur) est appelé automatiquement à l’instanciation avec new.

⸻

✅ Avantages
	•	Permet de forcer l’initialisation correcte d’un objet.
	•	Donne la liberté de créer plusieurs versions d’un objet grâce à la surcharge de constructeurs.
	•	Améliore la lisibilité et la sécurité du code.

⸻

❌ Inconvénients
	•	Si mal conçu, il peut imposer trop de paramètres et rendre l’instanciation lourde.
	•	Peut complexifier le code si trop de constructeurs sont définis.

⸻

💡 Phrase technique à retenir

Le constructeur initialise un objet : c’est la première méthode appelée lors de l’instanciation.

⸻

🧪 Récapitulatif – Quiz sur les Constructeurs

1. À quoi sert un constructeur ?

Réponse correcte :
À initialiser un objet lors de sa création.

⸻

2. Quelle est la particularité syntaxique d’un constructeur ?

Réponse correcte :

Il porte le même nom que la classe et n’a pas de type de retour.

⸻

3. Quelle ligne définit un constructeur valide dans une classe Livre ?

Réponse correcte :

public Livre(String titre) {
    this.titre = titre;
}


⸻

4. Que se passe-t-il si aucun constructeur n’est défini dans une classe ?

Réponse correcte :

Java ajoute automatiquement un constructeur par défaut sans paramètre.

⸻

5. Peut-on avoir plusieurs constructeurs dans une même classe ?

Réponse correcte :
Oui, grâce à la surcharge : ils doivent avoir des signatures différentes (nombres/types d’arguments).

⸻

Souhaites-tu enchaîner sur un autre concept de la POO comme l’encapsulation, l’héritage, ou le polymorphisme ?