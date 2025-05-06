## 🧠 Exercice : Devinette (niveau débutant)

### Objectif :

- Créer un petit jeu de devinette où l’utilisateur doit trouver un nombre secret.

### Consigne

- 1. Le programme choisit un nombre entier aléatoire entre 1 et 100 (inclus).
- 2. L’utilisateur a un nombre limité de tentatives (ex : 10) pour deviner le nombre.
- 3. Après chaque tentative, le programme affiche :
  - • "Trop petit !" si le nombre proposé est inférieur au nombre secret.
  - • "Trop grand !" si le nombre proposé est supérieur au nombre secret.
  - • "Bravo ! Tu as trouvé le nombre en X tentatives." si l’utilisateur trouve le bon nombre.
- 4.  Si l’utilisateur dépasse le nombre de tentatives sans trouver, le programme affiche "Perdu ! Le nombre était : X".

#### Bonus :

- Ajouter la possibilité de rejouer après la fin de la partie.

## Ma réponse

```java
import java.util.Scanner;

public class devinette {
    public static void main (String[]arg)
    {
        boolean devinette = true;
        int goodnumber = (int)(Math.random() * (101 - 1));
        int compteur = 1;
        while (devinette){

            System.out.println("Bonjour, veuillez choisir un nombre entre 1 et 100");
            Scanner keybord = new Scanner(System.in);
            int answer = keybord.nextInt();
            if (answer >= 1 && answer <= 100) {
                if (goodnumber == answer) {
                    System.out.println("Bravo ! Tu as trouvé le nombre en "+ compteur + "tentatives.");
                    devinette = false;
                } else {

                    System.out.println("Perdu retente ta chance ");
                    if(answer > goodnumber)
                    {
                        System.out.println("Ton nombre est plus grand que le bon numéro");
                    }
                    else
                    {
                        System.out.println("Ton nombre est plus petit que le bon numéro");
                    }


                }

                if (compteur > 10)
                {
                    System.out.println("💥 Perdu ! Le nombre était : " + goodnumber);

                }
                System.out.print("🔁 Veux-tu rejouer ? (oui/non) : ");
                String reponse = keybord.next().toLowerCase();
                if (!reponse.equals("oui")) {
                    devinette = false;
                    System.out.println("👋 Merci d’avoir joué !");
                }
                System.out.println(compteur);
            }
            else
            {
                System.out.println("le nombre doit être compris entre 1 et 100");
            }
            compteur++;
        }
    }
}
// exit console                 if (compteur > 10) {System.exit(0);}
```

## Correction possible

```java
import java.util.Scanner;

public class Devinette {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        boolean rejouer = true;

        while (rejouer) {
            int nombreSecret = (int)(Math.random() * 100) + 1;
            int tentatives = 0;
            final int MAX_TENTATIVES = 10;
            boolean trouve = false;

            System.out.println("🔢 J'ai choisi un nombre entre 1 et 100. À toi de deviner !");

            while (tentatives < MAX_TENTATIVES && !trouve) {
                System.out.print("Essai " + (tentatives + 1) + " : ");
                int proposition = scanner.nextInt();
                tentatives++;

                if (proposition < 1 || proposition > 100) {
                    System.out.println("❌ Nombre invalide. Entre 1 et 100 !");
                    continue;
                }

                if (proposition < nombreSecret) {
                    System.out.println("🔽 Trop petit !");
                } else if (proposition > nombreSecret) {
                    System.out.println("🔼 Trop grand !");
                } else {
                    System.out.println("🎉 Bravo ! Tu as trouvé en " + tentatives + " tentative(s).");
                    trouve = true;
                }
            }

            if (!trouve) {
                System.out.println("💥 Perdu ! Le nombre était : " + nombreSecret);
            }

            System.out.print("🔁 Veux-tu rejouer ? (oui/non) : ");
            String reponse = scanner.next().toLowerCase();
            if (!reponse.equals("oui")) {
                rejouer = false;
                System.out.println("👋 Merci d’avoir joué !");
            }
        }

        scanner.close();
    }
}
```
