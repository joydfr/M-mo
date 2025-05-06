Bien sûr ! Voici un mémo complet avec tes réponses incluses ainsi que les corrigés et des suggestions supplémentaires.

# 📝 **Mémo des Exercices de Java avec Corrigés et Réponses**

## 1. Affichage d'une chaîne - **Exercice 1** 🌍

### Objectif

Afficher le texte `"Hello World"` dans la console.

### Ta réponse

```java
public class Exercice1 {
    public static void main(String[] args) {
        System.out.println("Hello World");
    }
}

Corrigé

public class Exercice1 {
    public static void main(String[] args) {
        System.out.println("Hello World");
    }
}



⸻

2. Utilisation de Variables - Exercice 2 🧑‍💻

Objectif

Reprendre l’exercice 1 en utilisant une variable.

Ta réponse

public class Exercice2 {
    public static void main(String[] args) {
        String message = "Hello World";
        System.out.println(message);
    }
}

Corrigé

public class Exercice2 {
    public static void main(String[] args) {
        String message = "Hello World";
        System.out.println(message);
    }
}



⸻

3. Calcul Arithmétique - Exercice 3 ➗

Objectif

Afficher le périmètre d’un cercle dont le rayon est une variable.

Ta réponse

public class Exercice3 {
    public static void main(String[] args) {
        double rayon = 5.0;
        double perimetre = 2 * rayon;
        System.out.println("Le périmètre du cercle est : " + perimetre);
    }
}

Corrigé

public class Exercice3 {
    public static void main(String[] args) {
        double rayon = 5.0;
        double perimetre = 2 * rayon;
        System.out.println("Le périmètre du cercle est : " + perimetre);
    }
}



⸻

4. Saisie de Valeur - Exercice 4 📝

Objectif

Afficher le périmètre d’un cercle dont le rayon est demandé à l’utilisateur.

Ta réponse

import java.util.Scanner;

public class exercice4 {

    public static void main(String[] args) {
        Scanner clavier = new Scanner(System.in);
        System.out.println("Saissez votre rayon ");
        int Newrayon = clavier.nextInt();
        System.out.println("Le diamètre de votre cercle est de : " + Newrayon * 2);
    }
}

Corrigé

import java.util.Scanner;

public class Exercice4 {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Entrez le rayon du cercle : ");
        double rayon = scanner.nextDouble();
        double perimetre = 2 * Math.PI * rayon;
        System.out.println("Le périmètre du cercle est : " + perimetre);
        scanner.close();
    }
}



⸻

5. Test Simple (Majeur/Mineur) - Exercice 5 ⚖️

Objectif

Vérifier si l’utilisateur est majeur ou mineur à partir d’une valeur saisie.

Ta réponse

import java.util.Scanner;

public class Exercice5 {
    public static void main (String[]arg)
    {
        Scanner clavier = new Scanner(System.in);
        System.out.println("Veuillez saissir votre age");
        int age = clavier.nextInt();
        if (age > 18){
            System.out.println("Vous êtes majeur ");
        }
        else
        {
        System.out.println("Vous êtes mineur");
        }
    }
}

Corrigé

import java.util.Scanner;

public class Exercice5 {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Entrez votre âge : ");
        int age = scanner.nextInt();
        if (age >= 18) {
            System.out.println("Vous êtes majeur.");
        } else {
            System.out.println("Vous êtes mineur.");
        }
        scanner.close();
    }
}



⸻

6. Test Simple (Pair/Impair) - Exercice 6 🔢

Objectif

Indiquer si un nombre saisi est pair ou impair.

Ta réponse

import java.util.Scanner;

public class Exercice6 {
    public static void main (String [] args)
    {
        Scanner clavier = new Scanner(System.in);
        System.out.println("Veuilez saissir votre nombre");
        int number = clavier.nextInt();
        if(number%2 == 0)
        {
           System.out.println("Votre nombre est pair ");
        }
        else
        {
            System.out.println("Votre nombre est impair");
        }
    }
}

Corrigé

import java.util.Scanner;

public class Exercice6 {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Entrez un nombre : ");
        int nombre = scanner.nextInt();
        if (nombre % 2 == 0) {
            System.out.println("Le nombre est pair.");
        } else {
            System.out.println("Le nombre est impair.");
        }
        scanner.close();
    }
}



⸻

7. Test Avancé (Année Bissextile) - Exercice 7 📅

Objectif

Vérifier si une année est bissextile.

Ta réponse

import java.util.Scanner;

public class Exercice7 {
    public static void main (String[]arg)
    {
        Scanner clavier =  new Scanner(System.in);
        System.out.println("Veuillez saisir l'année");
        int year =clavier.nextInt();
        if ((year % 4 == 0 ) && (year % 100 != 0)||(year % 400 == 0)){
            System.out.println("C'est une année bissextile");
        }
        else{
            System.out.println("Ce n'est pas une année bissextile");
        }
    }
}

Corrigé

import java.util.Scanner;

public class Exercice7 {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Entrez une année : ");
        int annee = scanner.nextInt();
        if ((annee % 4 == 0 && annee % 100 != 0) || annee % 400 == 0) {
            System.out.println("L'année " + annee + " est bissextile.");
        } else {
            System.out.println("L'année " + annee + " n'est pas bissextile.");
        }
        scanner.close();
    }
}



⸻

8. Test Avancé (Nombre de jours d’un mois) - Exercice 8 📆

Objectif

Afficher le nombre de jours d’un mois en fonction du numéro du mois saisi.

Ta réponse

import java.util.Scanner;

public class Exercice8 {
    public static void main (String[]args)
    {
        Scanner clavier = new Scanner(System.in);
        System.out.println("Veuillez saissir votre mois en chiffre ");
        int month =1;
        month = clavier.nextInt();
        if ((month == 1) || (month ==3 ) ||(month == 5) ||(month == 7) || (month == 8) || (month == 10) || month == 12)
        {
            System.out.println("Le mois à 31 jours");
        } else if (month == 2) {
            System.out.println("Le mois à 28 jours ou 29 selon l'année");
        }
        else
        {
            System.out.println("Le mois à 30 jours ");
        }
    }
}
Corrigé

import java.util.Scanner;

public class Exercice8 {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Entrez le numéro du mois (1-12) : ");
        int mois = scanner.nextInt();
        int jours;

        switch (mois) {
            case 1: case 3: case 5: case 7: case 8: case 10: case 12:
                jours = 31;
                break;
            case 4: case 6: case 9: case 11:
                jours = 30;
                break;
            case 2:
                jours = 28; // Vous pouvez ajouter une vérification pour l'année bissextile ici
                break;
            default:
                jours = 0; // Mois invalide
                break;
        }

        if (jours == 0) {
            System.out.println("Numéro de mois invalide.");
        } else {
            System.out.println("Le mois " + mois + " a " + jours + " jours.");
        }
        scanner.close();
    }
}

8 Bis. Test Avancé (Chaine de caractères) - Exercice 8 bis 🔤
Objectif

Reprendre l’exercice précédent, mais avec une chaîne de caractères pour le mois.

Ta réponse

import java.util.Scanner;

public class Exercice8bis {
    public static void main (String[]args)
    {
        Scanner clavier = new Scanner(System.in);
        System.out.println("Veuillez saisir votre mois  ");
        String month = clavier.next();

        if ((month.equalsIgnoreCase("janvier")) || (month.equalsIgnoreCase("mars" )) ||(month.equalsIgnoreCase("mai" )) ||(month.equalsIgnoreCase("juillet" )) || (month.equalsIgnoreCase("août" )) || (month.equalsIgnoreCase("octobre" )) || month.equalsIgnoreCase("décembre" ))
        {
            System.out.println("Le mois à 31 jours");
        } else if (month.equalsIgnoreCase("février" )) {
            System.out.println("Le mois à 28 jours ou 29 selon l'année");
        }
        else
        {
            System.out.println("Le mois à 30 jours ");
        }
    }
}

Corrigé

import java.util.Scanner;

public class Exercice8bis {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Entrez le mois (en texte) : ");
        String mois = scanner.nextLine().toLowerCase();
        int jours;

        switch (mois) {
            case "janvier": case "mars": case "mai": case "juillet": case "août": case "octobre": case "décembre":
                jours = 31;
                break;
            case "avril": case "juin"

⸻
## 8 Ter. Fonctions - Vérification de l'année bissextile 🗓️

### Objectif
Reprendre l'exercice 7 et créer une fonction qui vérifie si une année est bissextile ou non.
Ta réponse

9. Boucle (Nombres de 1 à 100) - Exercice 9 🔄

Objectif

Afficher les nombres de 1 à 100.

Ta réponse
import java.util.Scanner;

public class Exercice8TER {
    public static void main (String[]arg)
    {
        Scanner clavier =  new Scanner(System.in);
        System.out.println("Veuillez saisir l'année");
        int year =clavier.nextInt();
        Scanner clavierbis = new Scanner(System.in);
        System.out.println("Veuillez saisir votre mois  ");
        String month = clavier.next();
        if ((year % 4 == 0 ) && (year % 100 != 0)||(year % 400 == 0)){
            System.out.println("C'est une année bissextile");
            if ((month.equalsIgnoreCase("janvier")) || (month.equalsIgnoreCase("mars" )) ||(month.equalsIgnoreCase("mai" )) ||(month.equalsIgnoreCase("juillet" )) || (month.equalsIgnoreCase("août" )) || (month.equalsIgnoreCase("octobre" )) || month.equalsIgnoreCase("décembre" ))
            {
                System.out.println("Le mois à 31 jours");
            }
            else if (month.equalsIgnoreCase("février" )) {
            System.out.println("Le mois à 29 jours");
        }
            else
            {
                System.out.println("Le mois à 30 jours ");
            }
        }
        else{
            System.out.println("Ce n'est pas une année bissextile");
            if (month.equalsIgnoreCase("février" ))
            {
                System.out.println("Le mois à 28 jours");
            }
        }
    }
}
Corrigé
import java.util.Scanner;

public class Exercice8Ter {

    // Fonction pour vérifier si une année est bissextile
    public static boolean estBissextile(int annee) {
        if ((annee % 4 == 0 && annee % 100 != 0) || (annee % 400 == 0)) {
            return true;
        }
        return false;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Demander le mois et l'année
        System.out.print("Entrez un mois sous forme de texte (janvier, février, etc.) : ");
        String moisTexte = scanner.nextLine().toLowerCase();

        System.out.print("Entrez une année : ");
        int annee = scanner.nextInt();

        // Vérification du mois et de l'année
        switch (moisTexte) {
            case "janvier":
            case "mars":
            case "mai":
            case "juillet":
            case "août":
            case "octobre":
            case "décembre":
                System.out.println("31 jours");
                break;
            case "avril":
            case "juin":
            case "septembre":
            case "novembre":
                System.out.println("30 jours");
                break;
            case "février":
                if (estBissextile(annee)) {
                    System.out.println("29 jours (année bissextile)");
                } else {
                    System.out.println("28 jours");
                }
                break;
            default:
                System.out.println("Mois invalide");
                break;
        }

        scanner.close();
    }
}

public class Exercice9 {
    public static void main(String[] args) {
        for (int i = 1; i <= 100; i++) {
            System.out.println(i);
        }
    }
}

Corrigé

public class Exercice9 {
    public static void main(String[] args) {
        for (int i = 1; i <= 100; i++) {
            System.out.println(i);
        }
    }
}



⸻

10. Boucle (Codes des caractères ASCII) - Exercice 11 🅰️

Objectif

Afficher les codes des caractères des nombres de 1 à 255.

Ta réponse

public class Exercice11 {
    public static void main(String[] args) {
        for (int i = 1; i <= 255; i++) {
            System.out.println("Code " + i + " : " + (char) i);
        }
    }
}

Corrigé

public class Exercice11 {
    public static void main(String[] args) {
        for (int i = 1; i <= 255; i++) {
            System.out.println("Code " + i + " : " + (char) i);
        }
    }
}



⸻

11. Échanger les valeurs de deux variables - Exercice 12 🔄

Objectif

Échanger les valeurs de deux variables.

Ta réponse

public class Exercice12 {
    public static void main(String[] args) {
        int nombre1 = 5;
        int nombre2 = 6;

        // Échange des valeurs
        int temp = nombre1;
        nombre1 = nombre2;
        nombre2 = temp;

        // Afficher les résultats
        System.out.println("Nombre1 après l'échange : " + nombre1);
        System.out.println("Nombre2 après l'échange : " + nombre2);
    }
}

Corrigé

public class Exercice12 {
    public static void main(String[] args) {
        int nombre1 =
```
