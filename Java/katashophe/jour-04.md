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

## kata 39

### Consigne

Given a set of numbers, return the additive inverse of each. Each positive becomes negatives, and the negatives become positives

```bash
[1, 2, 3, 4, 5] --> [-1, -2, -3, -4, -5]
[1, -2, 3, -4, 5] --> [-1, 2, -3, 4, -5]
[] --> []
```

### My solution

```java
import java.util.*;
public class Kata {
  public static int[] invert(int[] array) {
    return Arrays.stream(array).map(x -> Math.negateExact(x)).toArray();
  }
}
```

### Best pratice

```java
public class Kata {
  public static int[] invert(int[] array) {
    return java.util.Arrays.stream(array).map(i -> -i).toArray();
  }
}
```

## kata 40

### Consigne

Write a function which calculates the average of the numbers in a given array.

Note: Empty arrays should return 0.

### My solution

```java
import java.util.*;
public class Kata {
    public static double findAverage(int[] array) {
        return Arrays.stream(array).average().orElse(Double.NaN);
    }
}
```

### Best pratice

```java
import java.util.Arrays;
public class Kata{
  public static double find_average(int[] array){
    return Arrays.stream(array).average().orElse(0);
  }
}
```

## kata 41

### Consigne

Sentence Smash

Write a function that takes an array of words and smashes them together into a sentence and returns the sentence. You can ignore any need to sanitize words or add punctuation, but you should add spaces between each word. Be careful, there shouldn't be a space at the beginning or the end of the sentence!

Example

```bash
['hello', 'world', 'this', 'is', 'great']  =>  'hello world this is great'

words = ['hello', 'world', 'this', 'is', 'great']
smash(words) # returns "hello world this is great"

```

Assumptions

    You can assume that you are only given words.
    You cannot assume the size of the array.
    You can assume that you do get an array.

What We're Testing

We're testing basic loops and string manipulation. This is for beginners who are just learning loops and string manipulation.
Disclaimer

This is for beginners so we want to test basic loops and string manipulation. Advanced users should easily be able to do this in one line.

### My solution

```java
public class SmashWords {

	public static String smash(String [] words) {
    // TODO Write your code below this comment please
    return words.toString().join(" ",words);
  }
}
```

### Best pratice

```java
public class SmashWords {
	public static String smash(String... words) {
    return String.join(" ", words);
  }
}
```

## kata 42

### Consigne

Given a non-empty array of integers, return the result of multiplying the values together in order. Example:

```bash
[1, 2, 3, 4] => 1 * 2 * 3 * 4 = 24
```

### My solution

```java
import java.util.*;
import java.util.stream.IntStream;
public class Kata{

  public static int grow(int[] x){

    return Arrays.stream(x).reduce(1, (a, b) -> a * b);

  }

}
```

### Best pratice

```java
public class Kata{

  public static int grow(int[] x){
    int result = 1;
    for (int a : x) {
      result *= a;
    }
    return result;
  }
}
```

#### Or

```java
import java.util.stream.IntStream;

public class Kata{

  public static int grow(int[] x){

    return IntStream.of(x).reduce(1, (a, b) -> a * b);

  }

}
```

## kata 43

### Consigne

There was a test in your class and you passed it. Congratulations!

But you're an ambitious person. You want to know if you're better than the average student in your class.

You receive an array with your peers' test scores. Now calculate the average and compare your score!

Return true if you're better, else false!
Note:

Your points are not included in the array of your class's points. Do not forget them when calculating the average score!

### My solution

```java
public class Kata {
  public static boolean betterThanAverage(int[] classPoints, int yourPoints) {
    int total = yourPoints;
    for (int point : classPoints) {
      total += point;
    }
    double average = (double) total / (classPoints.length + 1);
    return yourPoints > average;
  }
}
```

### Best pratice

```java
import java.util.Arrays;

class Kata {
    static boolean betterThanAverage(final int[] classPoints, final int yourPoints) {
        return Arrays.stream(classPoints).average().orElse(0) < yourPoints;
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
