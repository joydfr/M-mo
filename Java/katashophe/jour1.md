## Kata 1

## Consigne

- This code does not execute properly. Try to figure out why.

### Problème

```java
public class Multiply {
    public static Double multiply(Double a, Double b) {
        return a * b
    }
}
```

### Solution

```java
public class Multiply {
    public static Double multiply(Double a, Double b) {
        return a * b;
    }
}
```

## Kata 2

## Consigne

- Create a function that takes an integer as an argument and returns "Even" for even numbers or "Odd" for odd numbers.

### My Solution

```java
public class Kata {
    public static String evenOrOdd(int number) {
      if (number %  2 == 0 )
        return "Even";
      else return "Odd";
    }
}
```

### Best pratique

```java
public class EvenOrOdd {
    public static String even_or_odd(int number) {
        return (number % 2) != 0 ? "Odd" : "Even";
    }
}
```

## Kata 3

## Consigne

- We need a function that can transform a number (integer) into a string.

What ways of achieving this do you know?

```bash
123  --> "123"
999  --> "999"
-100 --> "-100"
```

### My Solution

```java
class Kata {
  public static String numberToString(int num) {
    String newNum =Integer.toString(num);
    return newNum; // Return a string of the number here!
  }
}
```

### Best pratique

```java
class Kata {
  public static String numberToString(int num) {
    return String.valueOf(num);
  }
}
```

## ✅ Pourquoi c’est une best practice :

- 1 Utilisation de String.valueOf(num) plutôt que "" + num ou Integer.toString(num)
- String.valueOf(num) est robuste : il gère aussi bien les primitifs (int, float, etc.) que les objets, y compris null (en retournant "null" plutôt qu’une exception).
- C’est une méthode claire et lisible : elle exprime exactement l’intention de conversion d’un nombre en chaîne de caractères.
- Elle est recommandée par Oracle dans la doc officielle Java.

## Kata 4

### Consigne

- Complete the solution so that it reverses the string passed into it.

```bash
'world'  =>  'dlrow'
'word'   =>  'drow'
```

### My solution

```java
public class Kata {

  public static String solution(String str) {
    // Your code here...
    String reversedStr ="";

    for (int i = 0; i < str.length(); i++){
      reversedStr = str.charAt(i) + reversedStr;
    }

    return reversedStr;
  }

}
```

### Best pratique

```java
public class Kata {

  public static String solution(String str) {
    return new StringBuilder(str).reverse().toString();
  }

}
```

## kata 5

### Consigne

In this simple assignment you are given a number and have to make it negative. But maybe the number is already negative?

```bash
Kata.makeNegative(1);  // return -1
Kata.makeNegative(-5); // return -5
Kata.makeNegative(0);  // return 0
```

### Notes

- The number can be negative already, in which case no change is required.
- Zero (0) is not checked for any specific sign. Negative zeros make no mathematical sense.

### My solution

```java

public class Kata {

  public static int makeNegative(final int x) {

    if (x >= 0)
    {
      return x * -1;

    }
    else return x;
  }

}
```

### Best pratice

```java
import static java.lang.Math.abs;

public class Kata {

  public static int makeNegative(final int x) {
    return -abs(x);
  }

}
```

#### Or

```java
public class Kata {

  public static int makeNegative(final int x) {
      return (x < 0) ? x : -x;
  }

}
```
