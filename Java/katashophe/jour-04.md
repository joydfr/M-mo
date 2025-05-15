## kata 35

### Consigne

Create a function which answers the question "Are you playing banjo?".
If your name starts with the letter "R" or lower case "r", you are playing banjo!

The function takes a name as its only argument, and returns one of the following strings:

```bash
name + " plays banjo"
name + " does not play banjo"
```

Names given are always valid strings.

### My solution

```java
public class Banjo {
  public static String areYouPlayingBanjo(String name) {
    // Program me!
      if (name.toLowerCase().startsWith("r")){
        return name + " plays banjo";
      }
    else {
          return name + " does not play banjo";
    }
  }
}
```

### Best pratice

```java
public class Banjo
{
  public static String areYouPlayingBanjo(String name)
  {
    if( name.toUpperCase().startsWith("R") )
      return name + " plays banjo";
    else
      return name + " does not play banjo";
  }
}
```

#### Or

```java
public class Banjo {
  public static String areYouPlayingBanjo(String name) {
      return (name.charAt(0) == 'r' || name.charAt(0) == 'R') ? name + " plays banjo" : name + " does not play banjo";
  }
}
```

## kata 36

### Consigne

This kata is about multiplying a given number by eight if it is an even number and by nine otherwise.

### My solution

```java
public class Sid {
    public static int simpleMultiplication(int n) {
        //your code here
        return (n % 2 ==0) ? n * 8 : n * 9;
    }
}
```

### Best pratice

```java
public class Sid {
    public static int simpleMultiplication (int n) {
        return n % 2 == 0 ? n * 8 : n * 9;
    }
}
```

## kata 37

### Consigne

Write a function to convert a name into initials. This kata strictly takes two words with one space in between them.

The output should be two capital letters with a dot separating them.

It should look like this:

```bash
Sam Harris => S.H

patrick feeney => P.F
```

### My solution

```java
public class AbbreviateTwoWords {

  public static String abbrevName(String name) {
    char premierCaractere = name.charAt(0);
    String firstLettre = String.valueOf(premierCaractere);
    int indexEspace = name.indexOf(" ");
    char premierCaractereNom = name.charAt(indexEspace +1);
    String SecondeLettre = String.valueOf(premierCaractereNom);
    return firstLettre.toUpperCase() + "." +  SecondeLettre.toUpperCase();
  }
}
```

### Best pratice

```java
public class AbbreviateTwoWords {

  public static String abbrevName(String name) {
    String[] names = name.split(" ");
    return (names[0].charAt(0) + "." + names[1].charAt(0)).toUpperCase();
  }
}
```

## kata 38

### Consigne

Can you find the needle in the haystack?

Write a function findNeedle() that takes an array full of junk but containing one "needle"

After your function finds the needle it should return a message (as a string) that says:

"found the needle at position " plus the index it found the needle, so:

Example(Input --> Output)

```bash
["hay", "junk", "hay", "hay", "moreJunk", "needle", "randomJunk"] --> "found the needle at position 5"

```

Note: In COBOL, it should return "found the needle at position 6"

### My solution

```java

import java.util.Arrays;

import java.util.List;

public class Kata {
  public static String findNeedle(Object[] haystack) {
    // Your code here
    List <Object> newList = Arrays.asList(haystack);
     int indexNeedle = newList.indexOf("needle");
      return  "found the needle at position " + indexNeedle;
  }
}
```

### Best pratice

```java
public class Kata {
  public static String findNeedle(Object[] haystack) {
    return String.format("found the needle at position %d", java.util.Arrays.asList(haystack).indexOf("needle"));
  }
}
```

## kata 35

### Consigne

### My solution

```java

```

### Best pratice

```java

```

## kata 35

### Consigne

### My solution

```java

```

### Best pratice

```java

```

## kata 35

### Consigne

### My solution

```java

```

### Best pratice

```java

```

## kata 35

### Consigne

### My solution

```java

```

### Best pratice

```java

```

## kata 35

### Consigne

### My solution

```java

```

### Best pratice

```java

```

## kata 35

### Consigne

### My solution

```java

```

### Best pratice

```java

```

## kata 35

### Consigne

### My solution

```java

```

### Best pratice

```java

```
