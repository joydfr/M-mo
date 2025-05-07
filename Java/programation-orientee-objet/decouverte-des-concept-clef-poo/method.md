Parfait Jody ! Voici le mémo en Markdown sur les méthodes en POO, avec un exemple en Java, les avantages, les inconvénients, une phrase technique à retenir et un quiz corrigé — tout prêt à être ajouté à ton document.

⸻

🧠 Mémo POO – Les Méthodes

🧾 Définition

Une méthode est une fonction définie dans une classe qui décrit un comportement que peuvent exécuter les objets créés à partir de cette classe.

⸻

⭐ Caractéristiques principales
• Elle peut utiliser ou modifier les attributs de l’objet.
• Elle peut être :
• publique (public), privée (private), etc.
• statique (static) ou d’instance (liée à un objet).
• Une méthode a souvent :
• un nom
• un type de retour (ou void)
• des paramètres (ou aucun)
• Elle peut être appelée via un objet (ex. monObjet.maMethode();).

⸻

📚 Exemple en Java

public class Livre {
String titre;
String auteur;
boolean estDisponible;

    public Livre(String titre, String auteur) {
        this.titre = titre;
        this.auteur = auteur;
        this.estDisponible = true;
    }

    public void afficherInfos() {
        System.out.println("Titre : " + titre + ", Auteur : " + auteur);
    }

    public void emprunter() {
        if (estDisponible) {
            estDisponible = false;
            System.out.println(titre + " a été emprunté.");
        } else {
            System.out.println(titre + " n'est pas disponible.");
        }
    }

}

⸻

✅ Avantages
• Permet de réutiliser le comportement à plusieurs endroits.
• Rend le code plus lisible et structuré.
• Permet de cacher l’implémentation (principe d’encapsulation).

⸻

❌ Inconvénients
• Trop de méthodes mal nommées = code difficile à lire.
• Des méthodes trop longues ou mal organisées nuisent à la maintenabilité.

⸻

💡 Phrase technique à retenir

Une méthode est un comportement que peut exécuter un objet, souvent en lien avec ses attributs.

⸻

🧪 Récapitulatif – Quiz sur les Méthodes

1. Qu’est-ce qu’une méthode en POO ?

Réponse correcte :
Une fonction définie dans une classe, utilisée pour décrire une action ou un comportement d’un objet.

⸻

2. Dans l’extrait suivant, combien y a-t-il de méthodes ?

public class Livre {
public void afficher() { ... }
public void emprunter() { ... }
}

Réponse correcte :
Deux méthodes : afficher() et emprunter().

⸻

3. Quelle est la syntaxe correcte pour appeler une méthode d’un objet ?

Réponse correcte :

livre1.afficherInfos();

⸻

4. Que signifie le mot-clé void ?

Réponse correcte :

Cela signifie que la méthode ne retourne aucune valeur.

⸻

5. Quelle est la différence entre une méthode et une fonction classique ?

Réponse correcte :

Une méthode est liée à un objet (ou à une classe), alors qu’une fonction peut être utilisée seule, hors du contexte d’une classe.

⸻

Souhaites-tu que je regroupe tous les mémos (classe, objet, attribut, méthode) en un seul document bien structuré ?
