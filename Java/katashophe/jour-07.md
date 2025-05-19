## Kata 81

### Consigne

Create a method to see whether the string is ALL CAPS.
Examples (input -> output)

```bash
"c" -> False
"C" -> True
"hello I AM DONALD" -> False
"HELLO I AM DONALD" -> True
"ACSKLDFJSgSKLDFJSKLDFJ" -> False
"ACSKLDFJSGSKLDFJSKLDFJ" -> True
```

In this Kata, a string is said to be in ALL CAPS whenever it does not contain any lowercase letter so any string containing no letters at all is trivially considered to be in ALL CAPS.

### My solution

```java
public class Kata {
    public static boolean isUpperCase(String s) {
        // your code here
      return s.matches("^([A-Z]+ ?)+$");
    }
}
```

```java
public class Kata {
    public static boolean isUpperCase(String s) {
        return s.equals(s.toUpperCase());
    }
}
```

### Best pratice

```java
interface Kata {
  static boolean isUpperCase(String s) {
    return s.toUpperCase().equals(s);
  }
}
```

#### Or

```java
interface Kata {
  static boolean isUpperCase(String s) {
    return s.matches("[^a-z]*");
  }
}
```

## Kata 82

### Consigne

Debugging sayHello function

The starship Enterprise has run into some problem when creating a program to greet everyone as they come aboard. It is your job to fix the code and get the program working again!

Example output:

```bash
Hello, Mr. Spock
```

### My solution

```java
public class GrassHopper {

    public static String sayHello(String name) {

        return "Hello, " + name;
    }
}
```

### Best pratice

```java
public class GrassHopper {

    public static String sayHello(String name) {

        return "Hello, " + name;
    }
}
```

#### Or

```java
public class GrassHopper {

    public static String sayHello(String name) {
        return String.format("Hello, %s", name);
    }
}
```

## Kata 83

### Consigne

You take your son to the forest to see the monkeys. You know that there are a certain number there (n), but your son is too young to just appreciate the full number, he has to start counting them from 1.

As a good parent, you will sit and count with him. Given the number (n), populate an array with all numbers up to and including that number, but excluding zero.

For example(Input --> Output):

```bash
10 --> [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
 1 --> [1]
```

### My solution

```java
public class MonkeyCounter {
  public static int[] monkeyCount(final int n) {
    int[] result = new int[n];
    for (int i = 0; i < n; i++) {
      result[i] = i + 1;
    }
    return result;
  }
}
```

### Best pratice

```java
import java.util.stream.*;
public class MonkeyCounter
{
  public static int[] monkeyCount(final int n) {
    return IntStream.rangeClosed(1, n).toArray();
  }
}
```

## Kata 81

### Consigne

Complete the function that takes a non-negative integer n as input, and returns a list of all the powers of 2 with the exponent ranging from 0 to n ( inclusive ).
Examples

n = 0 ==> [1] # [2^0]
n = 1 ==> [1, 2] # [2^0, 2^1]
n = 2 ==> [1, 2, 4] # [2^0, 2^1, 2^2]

### My solution

```java
import java.util.stream.*;
public class Kata{
  public static long[] powersOfTwo(int n){

    //TODO: Have fun
   return LongStream.rangeClosed(0, n)
                     .map(i -> (long) Math.pow(2, i))
                     .toArray();
  }
}
```

### Best pratice

```java
import static java.util.stream.LongStream.rangeClosed;

interface Kata {
  static long[] powersOfTwo(int n) {
    return rangeClosed(0, n).map(i -> (long) Math.pow(2, i)).toArray();
  }
}
```

#### Or

```java
public class Kata{
  public static long[] powersOfTwo(int n){
    long[] arr = new long[n + 1];
    for (int i = 0; i < arr.length; i++) {
      arr[i] = (long) (Math.pow(2, i));
      }
    //TODO: Have fun
    return arr;
  }
}
```

## Kata 81

### Consigne

### My solution

```java

```

### Best pratice

```java

```

## Kata 81

### Consigne

### My solution

```java

```

### Best pratice

```java

```

## Kata 81

### Consigne

### My solution

```java

```

### Best pratice

```java

```

## Kata 81

### Consigne

### My solution

```java

```

### Best pratice

```java

```

## Kata 81

### Consigne

### My solution

```java

```

### Best pratice

```java

```

## Kata 81

### Consigne

### My solution

```java

```

### Best pratice

```java

```

## Kata 81

### Consigne

### My solution

```java

```

### Best pratice

```java

```

## Kata 81

### Consigne

### My solution

```java

```

### Best pratice

```java

```
