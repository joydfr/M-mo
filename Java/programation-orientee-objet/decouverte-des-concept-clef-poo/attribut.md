🧠 Mémo POO – Les Attributs

🧾 Définition

Un attribut est une variable définie dans une classe, qui représente une caractéristique d’un objet. Chaque objet a ses propres valeurs pour ces attributs.

⸻

⭐ Caractéristiques principales
• Un attribut appartient à la classe, mais sa valeur est propre à chaque objet.
• Il définit l’état de l’objet.
• Il peut être public, privé ou protégé (modificateurs d’accès).
• Il est généralement déclaré en haut de la classe, avec son type.

⸻

📚 Exemple en Java

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

}

Ici, titre, auteur et estDisponible sont des attributs de la classe Livre.

⸻

✅ Avantages
• Permet de modéliser les données spécifiques à chaque objet.
• Sépare l’état des objets de leurs comportements.
• Peut être contrôlé via des méthodes (getters/setters) pour assurer l’encapsulation.

⸻

❌ Inconvénients
• Mal utilisés, ils peuvent rendre le code difficile à maintenir.
• Leur accès direct peut casser l’encapsulation si mal protégé.

⸻

💡 Phrase technique à retenir

Un attribut est une variable membre d’une classe, qui stocke l’état d’un objet.

⸻

🧪 Récapitulatif – Quiz sur les Attributs

1. Qu’est-ce qu’un attribut en POO ?

Réponse correcte :
Une variable déclarée dans une classe qui représente une propriété d’un objet.

⸻

2. Dans la classe suivante, combien y a-t-il d’attributs ?

public class Livre {
String titre;
String auteur;
boolean estDisponible;
}

Réponse correcte :
Trois attributs : titre, auteur, estDisponible.

⸻

3. Quelle est la portée par défaut d’un attribut en Java ?

Réponse correcte :
Package-private (sans modificateur d’accès) : il est accessible uniquement dans le même paquet (package).

⸻

4. Quelle est la différence entre un attribut et une variable locale ?

Réponse correcte :

Un attribut appartient à un objet (ou à la classe s’il est static), tandis qu’une variable locale est temporaire et n’existe que dans une méthode.

⸻

5. Pourquoi utilise-t-on souvent this.attribut dans les constructeurs ?

Réponse correcte :

Pour différencier l’attribut de la variable passée en paramètre (qui porte souvent le même nom).

⸻

Souhaites-tu qu’on enchaîne avec les méthodes, ou que je t’aide à relier tous ces mémos dans un seul fichier bien structuré ?
