## Kata 68

### consigne

You ask a small girl,"How old are you?" She always says, "x years old", where x is a random number between 0 and 9.

Write a program that returns the girl's age (0-9) as an integer.

Assume the test input string is always a valid string. For example, the test input may be "1 year old" or "5 years old". The first character in the string is always a number.

### My solution

```java
public class CharProblem {
  public static int howOld(final String herOld) {

  //your code here, return correct age as int ; )
  return Character.getNumericValue(herOld.charAt(0));
  }
}
```

### Best pratice

```java
public class CharProblem {
  public static int howOld(final String herOld) {

  return Character.getNumericValue(herOld.charAt(0));
  }
}
```

## Kata 69

### consigne

This function should test if the factor is a factor of base.

Return true if it is a factor or false if it is not.
About factors

Factors are numbers you can multiply together to get another number.

2 and 3 are factors of 6 because: 2 \* 3 = 6

    You can find a factor by dividing numbers. If the remainder is 0 then the number is a factor.
    You can use the mod operator (%) in most languages to check for a remainder

For example 2 is not a factor of 7 because: 7 % 2 = 1

Note: base is a non-negative number, factor is a positive number.

### My solution

```java
public class Kata {
    public static boolean checkForFactor(int base, int factor) {
        // your code here
      return base % factor == 0 ? true : false;
    }
}
```

### Best pratice

```java
public class Kata {
    public static boolean checkForFactor(int base, int factor) {
        return base % factor == 0;
    }
}
```

## Kata 70

### consigne

I'm new to coding and now I want to get the sum of two arrays... Actually the sum of all their elements. I'll appreciate for your help.

P.S. Each array includes only integer numbers. Output is a number too.

### My solution

```java
import java.util.Arrays;
public class Sum {

  public static int arrayPlusArray(int[] arr1, int[] arr2) {
    // arr1 + arr2 is not working...
    int result1 = Arrays.stream(arr1).sum();
    int result2 = Arrays.stream(arr2).sum();
    return result1 + result2;
  }

}
```

### Best pratice

```java
import java.util.stream.*;

public class Sum {

  public static int arrayPlusArray(int[] arr1, int[] arr2) {
    return IntStream.of(arr1).sum() + IntStream.of(arr2).sum();
  }

}
```

## Kata 71

### consigne

The cockroach is one of the fastest insects. Write a function which takes its speed in km per hour and returns it in cm per second, rounded down to the integer (= floored).

For example:

```bash
1.08 --> 30
```

Note! The input is a Real number (actual type is language dependent) and is >= 0. The result should be an Integer.

### My solution

```java
public class Cockroach{
  public int cockroachSpeed(double x){
    // Good Luck!
    double result = x * 100000 / 3600 ;
    int resultInt = (int) result;
    return resultInt ;
  }
}
```

### Best pratice

```java
public class Cockroach{
  public int cockroachSpeed(double kph){
    int secondsInHour = 3600;
    int cmInKm = 100000;
    int centimetresPerSecond = (int) (kph * cmInKm / secondsInHour);
    return centimetresPerSecond;
  }
}
```

#### Or

```java
public class Cockroach{
  public int cockroachSpeed(double x){
    return (int)(x / 0.036);
  }
}
```

## Kata 72

### consigne

When provided with a number between 0-9, return it in words. Note that the input is guaranteed to be within the range of 0-9.

Input: 1

Output: "One".

If your language supports it, try using a switch statement.

### My solution

```java
public class Kata
{
  public static String switchItUp(int number)
  {
    switch (number){
           case 0 : return "Zero";
      case 1 : return "One";
      case 2 : return "Two";
      case 3 : return "Three";
      case 4 : return "Four";
      case 5 : return "Five";
      case 6 : return "Six";
      case 7 : return "Seven";
      case 8 : return "Eight";
      case 9 : return "Nine";

    }
  return "";
  }
}
```

### Best pratice

```java
public class Kata
{
  public static String switchItUp(int number)
  {
    switch (number)
    {
      case 0: return "Zero";
      case 1: return "One";
      case 2: return "Two";
      case 3: return "Three";
      case 4: return "Four";
      case 5: return "Five";
      case 6: return "Six";
      case 7: return "Seven";
      case 8: return "Eight";
    }
    return "Nine";
  }
}
```

#### Or

```java
public class Kata {
  public static String switchItUp(int number) {
    return new String[] {"Zero", "One", "Two", "Three", "Four", "Five", "Six", "Seven", "Eight", "Nine"}[number];
  }
}
```

## Kata 73

### consigne

Now you have to write a function that takes an argument and returns the square of it.

### My solution

```java
public class Kata
 {
  public static int square(int n){
    return n*n;
       //Your Code
  }
 }
```

### Best pratice

```java
public class Kata {
public static int square(int n) {
return n*n;
}
}
```

#### Or

```java
public class Kata
 {
  public static int square(int n){
    return (int) Math.pow(n, 2);
  }
 }
```

## Kata 74

### consigne

Take an array and remove every second element from the array. Always keep the first element and start removing with the next element.
Example:

["Keep", "Remove", "Keep", "Remove", "Keep", ...] --> ["Keep", "Keep", "Keep", ...]

None of the arrays will be empty, so you don't have to worry about that!

### My solution

```java
public class Kata {

  public static Object[] removeEveryOther(Object[] arr) {
    // happy coding
    Object[] result = new Object[(arr.length + 1) / 2];
      int j= 0;
    for (int i = 0; i < arr.length; i += 2)
    {
      result[j] = arr[i];
       j++;
    }

    return result;
  }
}
```

### Best pratice

```java
public class Kata {

  public static Object[] removeEveryOther(Object[] arr) {
    Object[] output = new Object[(arr.length + 1) / 2];

    for (int i = 0; i < output.length; i++) {
        output[i] = arr[i * 2];
    }

    return output;
  }
}
```

#### Or

```java
import java.util.Arrays;
import java.util.stream.IntStream;
public class Kata {

  public static Object[] removeEveryOther(Object[] arr) {
    return IntStream.range(0, arr.length).filter(n -> n % 2 == 0).mapToObj(i->arr[i]).toArray();
  }
}
```

## Kata 75

### consigne

Your function takes two arguments:

    current father's age (years)
    current age of his son (years)

Сalculate how many years ago the father was twice as old as his son (or in how many years he will be twice as old). The answer is always greater or equal to 0, no matter if it was in the past or it is in the future

### My solution

```java
public class TwiceAsOld {

    public static int twiceAsOld(int dadYears, int sonYears) {
        //TODO: Add code here
        return Math.abs(dadYears - 2 * sonYears);
    }

}
```

### Best pratice

```java
public class TwiceAsOld{

  public static int TwiceAsOld(int dadYears, int sonYears){
    return Math.abs((sonYears*2)-dadYears);

  }

}
```

## Kata 76

### consigne

### My solution

```java

```

### Best pratice

```java

```

## Kata 77

### consigne

### My solution

```java

```

### Best pratice

```java

```

## Kata 78

### consigne

### My solution

```java

```

### Best pratice

```java

```

## Kata 79

### consigne

### My solution

```java

```

### Best pratice

```java

```

## Kata 80

### consigne

### My solution

```java

```

### Best pratice

```java

```
