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

## Kata 68

### consigne

### My solution

```java

```

### Best pratice

```java

```

## Kata 68

### consigne

### My solution

```java

```

### Best pratice

```java

```

## Kata 68

### consigne

### My solution

```java

```

### Best pratice

```java

```

## Kata 68

### consigne

### My solution

```java

```

### Best pratice

```java

```
