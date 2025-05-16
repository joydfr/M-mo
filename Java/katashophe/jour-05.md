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
import java.util.*;
public class Sequence{

  public static int[] reverse(int n){
    int[] reverse = new int [n];
    for (int i =0; i < n ; i++)
     reverse[i] = n -i ;
    return reverse;
  }

}
```

### Best pratice

```java
public class Sequence{

  public static int[] reverse(int n){
    //your code
    int[] res = new int[n];
    for (int i=0; i<n; i++)
      res[i]=n-i;
    return res;
  }

}
```

## kata 55

### Consigne

Let's play! You have to return which player won! In case of a draw return Draw!.

Examples(Input1, Input2 --> Output):

```bash
"scissors", "paper" --> "Player 1 won!"
"scissors", "rock" --> "Player 2 won!"
"paper", "paper" --> "Draw!"
```

### My solution

```java
public class Kata {
  public static String rps(String p1, String p2) {
    if (p1.equals(p2)) return "Draw!";

    if ((p1.equals("rock") && p2.equals("scissors")) ||
        (p1.equals("scissors") && p2.equals("paper")) ||
        (p1.equals("paper") && p2.equals("rock"))) {
      return "Player 1 won!";
    } else {
      return "Player 2 won!";
    }
  }
}
```

### Best pratice

```java
public class Kata {
  public static String rps(String p1, String p2) {
    if(p1 == p2) return "Draw!";
    int p = (p1 + p2).equals("scissorspaper") || (p1 + p2).equals("rockscissors") || (p1 + p2).equals("paperrock") ? 1 : 2;
    return "Player " + p + " won!";
  }
}
```

## kata 56

### Consigne

If you can't sleep, just count sheeps!!
Task:

Given a non-negative integer, 3 for example, return a string with a murmur: "1 sheep...2 sheep...3 sheep...". Input will always be valid, i.e. no negative integers.

### My solution

```java
class Kata {
  public static String countingSheep(int num) {
    //Add your code here
    StringBuilder countingSheeps = new StringBuilder();
    for (int i = 1; i <= num ; i++){
      countingSheeps.append(i).append(" sheep...");
    }
    return countingSheeps.toString();
  }
}
```

### Best pratice

```java
class Kata {
    public static String countingSheep(int num) {
        StringBuilder stringBuilder = new StringBuilder();
        for (int i = 1; i <= num; i++) {
            stringBuilder.append(i).append(" sheep...");
        }
        return stringBuilder.toString();
    }
}
```

## kata 57

### Consigne

Grade book

Complete the function so that it finds the average of the three scores passed to it and returns the letter value associated with that grade.
Numerical Score Letter Grade
90 <= score <= 100 'A'
80 <= score < 90 'B'
70 <= score < 80 'C'
60 <= score < 70 'D'
0 <= score < 60 'F'

Tested values are all between 0 and 100. Theres is no need to check for negative values or values greater than 100.

### My solution

```java
public class GrassHopper {
    public static char getGrade(int s1, int s2, int s3) {
      int average = (s1 + s2 + s3) / 3;
     return average >= 90  ? 'A':
      average >= 80  ? 'B':
        average >= 70 ? 'C':
          average >= 60 ? 'D':'F';
    }
}
```

### Best pratice

```java
public class GrassHopper {

    public static char getGrade(int s1, int s2, int s3) {
        int mean = (s1 + s2 + s3) / 3;
        if (mean >= 90) return 'A';
        if (mean >= 80) return 'B';
        if (mean >= 70) return 'C';
        if (mean >= 60) return 'D';
        return 'F';
    }
}
```

## kata 58

### Consigne

Create a function that gives a personalized greeting. This function takes two parameters: name and owner.

Use conditionals to return the proper message:
case return
name equals owner 'Hello boss'
otherwise 'Hello guest'

### My solution

```java
class Kata {
    static String greet(String name, String owner) {
        // Add code here
      return name.equals(owner) ? "Hello boss" : "Hello guest";
    }
}
```

### Best pratice

```java
class Kata {
    static String greet(String name, String owner) {
        return name.equals(owner) ? "Hello boss" : "Hello guest";
    }
}
```

## kata 59

### Consigne

After a hard quarter in the office you decide to get some rest on a vacation. So you will book a flight for you and your girlfriend and try to leave all the mess behind you.

You will need a rental car in order for you to get around in your vacation. The manager of the car rental makes you some good offers.

Every day you rent the car costs $40. If you rent the car for 7 or more days, you get $50 off your total. Alternatively, if you rent the car for 3 or more days, you get $20 off your total.

Write a code that gives out the total amount for different days(d).

### My solution

```java
public class Kata {
  public static int rentalCarCost(int d) {
    // Your solution here
    int total = d * 40;
    return d >= 7 ? total - 50 : d >= 3 ? total - 20 : total;
  }
}
```

### Best pratice

```java
public class Kata {
  private static final int COST_PER_DAY = 40;

  public static int rentalCarCost(int d) {
    if (d < 3)       return d * COST_PER_DAY;
    else if (d >= 7) return d * COST_PER_DAY - 50;
    else             return d * COST_PER_DAY - 20;
  }
}
```

## kata 60

### Consigne

Write function RemoveExclamationMarks which removes all exclamation marks from a given string.

### My solution

```java
class Solution {
    static String removeExclamationMarks(String s) {
        return s.replace("!","");
    }
}
```

### Best pratice

```java
class Solution {
    static String removeExclamationMarks(String s) {
        return s.replaceAll("!", "");
    }
}
```

## kata 60

### Consigne

Given a month as an integer from 1 to 12, return to which quarter of the year it belongs as an integer number.

For example: month 2 (February), is part of the first quarter; month 6 (June), is part of the second quarter; and month 11 (November), is part of the fourth quarter.

Constraint:

```bash
1 <= month <= 12
```

### My solution

```java
public class Kata {
    public static int quarterOf(int month) {
        // Your code here
      return month <= 3 ? 1:
      month <= 6 ? 2 :
      month <= 9 ? 3 : 4;
    }
}
```

### Best pratice

```java
interface Kata {
  static int quarterOf(int month) {
    return (int) Math.ceil(month / 3.);
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
