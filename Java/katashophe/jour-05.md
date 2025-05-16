## kata 48

### Consigne

Write function bmi that calculates body mass index (bmi = weight / height2).

if bmi <= 18.5 return "Underweight"

if bmi <= 25.0 return "Normal"

if bmi <= 30.0 return "Overweight"

if bmi > 30 return "Obese"

### My solution

```java
public class Calculate {
  public static String bmi(double weight, double height) {
    double bmi = weight / (height * height);
    return  bmi <= 18.5 ? "Underweight" :
    bmi <= 25.0 ? "Normal" :
    bmi <= 30.0 ? "Overweight" : "Obese";
  }
}
```

### Best pratice

```java
public class Calculate {
  public static String bmi(double weight, double height) {

		  double bmi = weight / (height * height);

			if ( bmi <= 18.5) return "Underweight";
			if ( bmi <= 25) return "Normal";
			if ( bmi <= 30) return "Overweight";
			return "Obese";

	}
}
```

## kata 49

### Consigne

Your task is to make two functions ( max and min, or maximum and minimum, etc., depending on the language ) that receive a list of integers as input, and return the largest and lowest number in that list, respectively. Each function returns one number.
Examples (Input -> Output)

```java
* [4,6,2,1,9,63,-134,566]         -> max = 566, min = -134
* [-52, 56, 30, 29, -54, 0, -110] -> min = -110, max = 56
* [42, 54, 65, 87, 0]             -> min = 0, max = 87
* [5]                             -> min = 5, max = 5
```

Notes

    You may consider that there will not be any empty arrays/vectors.

### My solution

```java
import java.util.*;
public class Kata {

  public int min(int[] list) {
    return Arrays.stream(list).min().getAsInt();
  }

  public int max(int[] list) {
    return Arrays.stream(list).max().getAsInt();
  }
}
```

### Best pratice

```java
import java.util.Arrays;

public class Kata {

  public int min(int[] list) {
    return Arrays.stream(list).min().getAsInt();
  }

  public int max(int[] list) {
    return Arrays.stream(list).max().getAsInt();
  }
}
```

## kata 50

### Consigne

You will be given an array a and a value x. All you need to do is check whether the provided array contains the value.

a can contain numbers or strings. x can be either.

Return true if the array contains the value, false if not.

### My solution

```java
import java.util.Arrays;
public class Solution {

    public static boolean check(Object[] a, Object x) {
        // Your code here
        return a == null || Arrays.asList(a).contains(x) ? true: false;
    }

}
```

### Best pratice

```java
import java.util.Arrays;

public class Solution {

    public static boolean check(Object[] a, Object x) {
        return Arrays.asList(a).contains(x);
    }

}
```

## kata 51

### Consigne

Given a string of digits, you should replace any digit below 5 with '0' and any digit 5 and above with '1'. Return the resulting string.

Note: input will never be an empty string

### My solution

```java
public class FakeBinary {
    public static String fakeBin(String numberString) {
      StringBuilder newNumberString = new StringBuilder();
      for (int i = 0 ; i < numberString.length(); i++){
        int digit = Character.getNumericValue(numberString.charAt(i));
        if (digit < 5){
          newNumberString.append('0');
        }
        else{
          newNumberString.append('1');
        }
      }
        return newNumberString.toString();
    }
}
```

### Best pratice

```java
public class FakeBinary {
    public static String fakeBin(String numberString) {
        return numberString.replaceAll("[0-4]", "0").replaceAll("[5-9]", "1");
    }
}
```

## kata 52

### Consigne

Write a function to split a string and convert it into an array of words.
Examples (Input ==> Output):

```bash
"Robin Singh" ==> ["Robin", "Singh"]

"I love arrays they are my favorite" ==> ["I", "love", "arrays", "they", "are", "my", "favorite"]
```

### My solution

```java
import java.util.Arrays;
public class Solution {

    public static String[] stringToArray(String s) {
      //your code;

        return s.split(" ");
    }

}
```

### Best pratice

```java
public class Solution {
    public static String[] stringToArray(String s) {
        return s.split(" ");
    }
}
```

## kata 53

### Consigne

Create a function with two arguments that will return an array of the first n multiples of x.

Assume both the given number and the number of times to count will be positive numbers greater than 0.

Return the results as an array or list ( depending on language ).
Examples

```bash
x = 1, n = 10 --> [1,2,3,4,5,6,7,8,9,10]
x = 2, n = 5  --> [2,4,6,8,10]

```

### My solution

```java
import java.util.*;

public class Kata {
  public static int[] countBy(int x, int n) {
    List<Integer> arrList = new ArrayList<>();
    for (int i = 1; i <= n; i++) {
      arrList.add(x * i);
    }

    // Convertir List<Integer> → int[]
    int[] result = new int[arrList.size()];
    for (int i = 0; i < arrList.size(); i++) {
      result[i] = arrList.get(i);
    }

    return result;
  }
}
```

### Best pratice

```java
import java.util.stream.IntStream;

public class Kata{
  public static int[] countBy(int x, int n){

    return IntStream.rangeClosed(1, n)
      .map(i -> i * x)
      .toArray();
  }
}
```

#### Or

```java
public class Kata{
  public static int[] countBy(int x, int n){
    int[] el = new int[n];
    for(int i = 0; i < n; i++)  el[i] = x * (i+1);
    return el;
  }
}
```

## kata 54

### Consigne

Build a function that returns an array of integers from n to 1 where n>0.

Example : n=5 --> [5,4,3,2,1]

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
