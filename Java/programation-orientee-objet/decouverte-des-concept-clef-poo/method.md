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

🔐 Les modificateurs d’accès (public, private, protected)

Les modificateurs d’accès contrôlent la visibilité d’une méthode ou d’un attribut, c’est-à-dire depuis où ils peuvent être utilisés.

🔹 public
• Accès autorisé partout : dans toutes les classes, peu importe le package.
• À utiliser pour : les méthodes destinées à être utilisées en dehors de la classe (API, interface publique d’un objet).

Exemple :

public void afficherInfos() {
System.out.println("Titre : " + titre);
}

On peut appeler cette méthode depuis le programme principal ou d’autres classes.

⸻

🔸 private
• Accès limité à la classe elle-même.
• À utiliser pour : protéger l’intérieur d’un objet, comme les attributs ou les méthodes utilitaires internes.
• Oblige à passer par des méthodes publiques (getters/setters) → encapsulation.

Exemple :

private boolean estDisponible;

public boolean isDisponible() {
return estDisponible;
}

estDisponible ne peut être lu que via isDisponible().

⸻

🟢 protected
• Accès autorisé à la classe elle-même, ses sous-classes, et les classes du même package.
• À utiliser pour : préparer une classe à l’héritage, tout en protégeant l’accès externe.

Exemple :

protected void verifierDisponibilite() {
System.out.println("Vérification de la disponibilité...");
}

Cette méthode pourra être appelée dans une classe qui hérite de Livre, même si elle est dans un autre fichier.

⸻

🗂️ Résumé en tableau

Modificateur Visible depuis… Utilisation recommandée
public Toutes les classes (même autres packages) Interface publique (API)
private Classe elle-même uniquement Sécurisation des données, encapsulation
protected Classe + sous-classes + classes du même package Héritage, accès contrôlé aux extensions

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
