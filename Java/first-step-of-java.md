# 📝 Mémo Java – Notions de base

## 🌱 Syntaxe de base

### ✅ Classe minimale

```java
public class HelloWorld {
    public static void main(String[] args) {
        // code ici
    }
}



⸻

🖨️ Affichage en console

✅ Utiliser System.out.println

System.out.println("Bonjour Jody !");
System.out.println("Bienvenue sur Java !");



⸻

🎤 Saisie utilisateur

✅ Avec la classe Scanner

import java.util.Scanner;

Scanner clavier = new Scanner(System.in);
System.out.print("Ton plat préféré : ");
String plat = clavier.nextLine();
System.out.println("Tu aimes " + plat + " ! C’est noté.");



⸻

🔀 Structures conditionnelles

✅ if, else if, else

System.out.print("Entrez votre âge : ");
int age = clavier.nextInt();

if (age < 18) {
    System.out.println("Vous ne pouvez pas voter");
} else if (age == 18) {
    System.out.println("Vous venez tout juste d’avoir le droit de voter !");
} else {
    System.out.println("Vous pouvez voter");
}



⸻

🔁 Boucles

✅ Boucle for

for (int i = 1; i <= 10; i++) {
    System.out.println(i);
}

✅ Boucle while (compte à rebours)

System.out.print("Entrez un nombre : ");
int nombre = clavier.nextInt();

while (nombre >= 0) {
    System.out.println(nombre);
    nombre--;
}



⸻

🔢 Types primitifs

✅ Déclaration de types

int entier = 42;
double virgule = 3.14;
boolean vraiOuFaux = true;
char lettre = 'A';
String texte = "Bonjour";



⸻

🔁 Conversions

✅ Conversion implicite (int → double)

int a = 5;
double b = 2.5;
double result = a + b;
System.out.println(result); // 7.5

✅ Conversion explicite (cast double → int)

double d = 7.9;
int i = (int) d;
System.out.println(i); // 7

✅ Conversion String → int

System.out.print("Entrez un nombre : ");
int valeur = clavier.nextInt(); // ou Integer.parseInt(clavier.nextLine())
double result = (double) valeur;
System.out.println(result * 2);



⸻

📦 Wrappers Java

Primitif	Wrapper
int	Integer
double	Double
char	Character
boolean	Boolean

✅ Exemple

int x = 5;
Integer y = x;      // autoboxing
int z = y;          // unboxing



⸻

✅ Concepts validés
	•	Classe Java minimale
	•	Méthode main
	•	Affichage console
	•	Saisie clavier (Scanner)
	•	Structures conditionnelles (if / else)
	•	Boucles for et while
	•	Types primitifs (int, double, etc.)
	•	Conversions implicites et explicites
	•	Wrappers (Integer, Double, etc.)

⸻
```
