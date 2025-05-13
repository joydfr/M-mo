# kata 6

## Consigne

Very simple, given a number (integer / decimal / both depending on the language), find its opposite (additive inverse).

Examples:

```bash
1: -1
14: -14
-34: 34
```

### My solution

```java

public class Kata
    {
        public static int opposite(int number)
        {
            // your code here

            return -number;
        }
    }

```

### Best pratice

```java
public class Kata
    {
        public static int opposite(int number)
        {
            return -number;
        }
    }
```

## kata 7

### Consigne

Complete the method that takes a boolean value and return a "Yes" string for true, or a "No" string for false.

### My solution

```java
class YesOrNo
{
  public static String boolToWord(boolean b)
  {
    //TODO
   return (b == true) ? "Yes": "No";

  }

}
```

### Best pratice

```java

class YesOrNo
{
  public static String boolToWord(boolean b)
  {
    return b ? "Yes" : "No";
  }

}
```

## Kata 8

### Consigne

You get an array of numbers, return the sum of all of the positives ones.
Example

    [1, -4, 7, 12] => 1+7+12=20 1 + 7 + 12 = 20 1+7+12=20

Note

If there is nothing to sum, the sum is default to 0.

### My solution

```java
public class Positive{

  public static int sum(int[] arr){
  int sum = 0;
   for ( int i : arr) {

     if (i >= 0)
     {
       sum = sum + i;

     }
      }
     return sum;
  }

}
```

### Best pratice

```java
import java.util.Arrays;
public class Positive{
    public static int sum(int[] arr){
        return Arrays.stream(arr).filter(v -> v > 0).sum();
    }
}
```

## Kata 9

### Consigne

Write a function that accepts a non-negative integer n and a string s as parameters, and returns a string of s repeated exactly n times.

Write a function that accepts a non-negative integer n and a string s as parameters, and returns a string of s repeated exactly n times.

```bash
6, "I"     -> "IIIIII"
5, "Hello" -> "HelloHelloHelloHelloHello"
```

### My solution

```java
class Solution {
  static String repeatStr(int repeat, String string) {
    return string.repeat(repeat);
  }
}
```

### Best pratice

```java
class Solution {
  static String repeatStr(int repeat, String string) {
    return string.repeat(repeat);
  }
}
```

#### Or

```java
public class Solution {
    public static String repeatStr(final int repeat, final String string) {
        StringBuilder sb = new StringBuilder();

        for (int i = 0; i < repeat; i++) {
            sb.append(string);
        }

        return sb.toString();
    }
}
```

## Kata 10

### Consigne

It's pretty straightforward. Your goal is to create a function that removes the first and last characters of a string. You're given one parameter, the original string. You don't have to worry about strings with less than two characters.

### My solution

```java
public class RemoveChars {
    public static String remove(String str) {

        // your code here
      return str.substring(1, str.length() - 1);
    }
}
```

### Best pratice

```java
public class RemoveChars {
    public static String remove(String str) {
        return str.substring(1, str.length() - 1);
    }
}
```
