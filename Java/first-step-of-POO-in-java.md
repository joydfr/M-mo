# 🧠 Mémo Java – Premiers pas en POO

## 🌟 Qu’est-ce que la POO ?

La **Programmation Orientée Objet** est un paradigme qui repose sur l’idée de modéliser des **objets** du monde réel en informatique.  
En Java, **tout est objet** (ou presque) !

---

## 🧩 Concepts fondamentaux

### 🧱 1. Classe

Une **classe** est un modèle ou un plan de construction.  
Elle définit les **attributs** (état) et **méthodes** (comportements) d’un objet.

```java
public class Personne {
    String nom;
    int age;
}



⸻

🧍 2. Objet

Un objet est une instance concrète d’une classe.

Personne p = new Personne();



⸻

🧬 3. Attributs

Ce sont les données stockées dans l’objet.
Ils sont déclarés comme des variables dans la classe.

String nom;
int age;



⸻

🛠️ 4. Méthodes

Ce sont les comportements que l’objet peut effectuer.
Elles sont comme des fonctions internes à l’objet.

public String sePresenter() {
    return "Bonjour, je m'appelle " + this.nom + " et j'ai " + this.age + " ans.";
}



⸻

🚪 5. Constructeur

Le constructeur est une méthode spéciale qui permet d’initialiser un objet au moment de sa création.

public Personne(String nom, int age) {
    this.nom = nom;
    this.age = age;
}



⸻

📚 Correction des exercices

✅ Exercice 10 : Définir une classe

public class Personne {
    String nom;
    int age;
}



⸻

✅ Exercice 11 : Créer une instance

public class Main {
    public static void main(String[] args) {
        Personne p = new Personne();
        p.nom = "Jody";
        p.age = 28;
    }
}



⸻

✅ Exercice 12 : Appeler une méthode d’instance

public class Personne {
    String nom;
    int age;

    public String sePresenter() {
        return "Bonjour, je m'appelle " + nom + " et j'ai " + age + " ans.";
    }
}

public class Main {
    public static void main(String[] args) {
        Personne p = new Personne();
        p.nom = "Jody";
        p.age = 28;
        System.out.println(p.sePresenter());
    }
}



⸻

✅ Exercice 13 : Ajouter un constructeur

public class Personne {
    String nom;
    int age;

    public Personne(String nom, int age) {
        this.nom = nom;
        this.age = age;
    }

    public String sePresenter() {
        return "Bonjour, je m'appelle " + nom + " et j'ai " + age + " ans.";
    }
}



⸻

✅ Exercice 14 : Utiliser le constructeur

public class Main {
    public static void main(String[] args) {
        Personne p = new Personne("Jody", 28);
        System.out.println(p.sePresenter());
    }
}



⸻

📝 Récapitulatif visuel

Élément	Déclaration / Exemple
Classe	public class MaClasse {}
Attribut	int age;
Méthode	public void parler() { ... }
Constructeur	public MaClasse(...) { ... }
Instanciation	MaClasse objet = new MaClasse();

```
