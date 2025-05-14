## Kata 17

### Consigne

Write a function that removes the spaces from the string, then return the resultant string.

Examples (Input -> Output):

```bash
"8 j 8   mBliB8g  imjB8B8  jl  B" -> "8j8mBliB8gimjB8B8jlB"
"8 8 Bi fk8h B 8 BB8B B B  B888 c hl8 BhB fd" -> "88Bifk8hB8BB8BBBB888chl8BhBfd"
"8aaaaa dddd r     " -> "8aaaaaddddr"
```

### My solution

```java
public class Kata {
    public static String noSpace(final String x) {
        return x.replaceAll("\\s+", "");
    }
}
```

### Best pratice

```java
class Kata {
    static String noSpace(final String x) {
        return x.replace(" ", "");
    }
}
```

## Kata jour 18

### Consigne

Code as fast as you can! You need to double the integer and return it.

### My solution

```java
class Java {
  public static int doubleInteger(int i) {
    // Double the integer and return it!
  return i * 2;
  }
}
```

### best pratice

```java
class Java {
  public static int doubleInteger(int i) {
    return i*2;
  }
}
```

## kata 19

### Consigne

Implement a function which convert the given boolean value into its string representation.

Note: Only valid inputs will be given.

### My solution

```java
public class BooleanToString {
  public static String convert(boolean b) {
    String answer;
    if (b == true)
    {
      answer = "true";
    }
    else {
      answer = "false";
    }
    return answer;
  }
}
```

### Best pratice

```java
public class BooleanToString {
  public static String convert(boolean b){
    return b ? "true" : "false";
  }
}
```

or

```java
public class BooleanToString {
  public static String convert(boolean b){
    return Boolean.toString(b);
  }
}
```

## kata 20

### Consigne

Create a function that accepts a parameter representing a name and returns the message: "Hello, <name> how are you doing today?".

[Make sure you type the exact thing I wrote or the program may not execute properly]

### My solution

```java
public class Kata
{
  public static String greet(String name)
  {
    // Your code here
      return "Hello, " + name + " how are you doing today?";

  }
}
```

### Best pratice

```java
public class Kata
{
  public static String greet(String name)
  {
    return String.format("Hello, %s how are you doing today?", name);
  }
}
```

## Kata 21

### Consigne

Your task is to create a function that does four basic mathematical operations.

The function should take three arguments - operation(string/char), value1(number), value2(number).
The function should return result of numbers after applying the chosen operation.
Examples(Operator, value1, value2) --> output

```bash
('+', 4, 7) --> 11
('-', 15, 18) --> -3
('*', 5, 5) --> 25
('/', 49, 7) --> 7
```

### My solution

```java
public class BasicOperations
{
  public static Integer basicMath(String op, int v1, int v2)
  {
    int result = 0;
    if (op == "+")
    {
      result = v1 + v2;
    }
    if (op == "-")
    {
      result = v1 - v2;
    }
    if (op == "*"){
      result = v1 * v2;
    }
    if (op == "/"){
      result = v1 / v2;
    }
    return result;
  }
}
```

### Best pratice

```java
public class BasicOperations
{
  public static Integer basicMath(String op, int v1, int v2)
  {
  switch (op) {
		case "-":
			return v1 - v2;
		case "+":
			return v1 + v2;
		case "*":
			return v1 * v2;
		case "/": {
			if (v2 == 0)
				throw new IllegalArgumentException("Division by zero");
			return v1 / v2;
		}
		default:
			throw new IllegalArgumentException("Unknown operation: " + op);
		}
  }
}
```

or

```java
public class BasicOperations{
  public static Integer basicMath(String symbol, int x, int y){
    switch (symbol){
      case "+": return x+y;
      case "-": return x-y;
      case "*": return x*y;
      case "/": return x/y;
    }
    return 0;
  }
}
```

## Kata 22

### Consigne

Nathan loves cycling.

Because Nathan knows it is important to stay hydrated, he drinks 0.5 litres of water per hour of cycling.

You get given the time in hours and you need to return the number of litres Nathan will drink, rounded down.

For example:

```bash
time = 3 ----> litres = 1

time = 6.7---> litres = 3

time = 11.8--> litres = 5
```

### My solution

```java
public class KeepHydrated  {
  public static int liters(double time)  {
    //Your code goes here! Hint: You should change that -1
     double water = 0.0;
     if (time >= 1){
        water =time * 0.5;
     }
    int intWater = (int)Math.floor(water);
    System.out.println(intWater);
    return intWater;

  }
}

```

### Best pratice

```java
public class KeepHydrated  {
  public static int liters(double time)  {
    //Your code goes here! Hint: You should change that -1
    return (int) time / 2;
  }
}
```

#### Or

```java
public class KeepHydrated  {
  public static int liters(double time)  {
    //Your code goes here! Hint: You should change that -1
    double t = time*0.5;
    return (int)t;

  }
}
```

## Kata 23

### Consigne

Introduction

The first century spans from the year 1 up to and including the year 100, the second century - from the year 101 up to and including the year 200, etc.
Task

Given a year, return the century it is in.
Examples

```bash
1705 --> 18
1900 --> 19
1601 --> 17
2000 --> 20
2742 --> 28
```

Note: this kata uses strict construction as shown in the description and the examples, you can read more about it here

### My solution

```java
public class Solution {
  public static int century(int number) {
    // your code goes here
   double  result = number / 100.0;
    return (int)Math.ceil(result);
  }
}
```

### Best pratice

```java
public class Solution {
  public static int century(int number) {
    return (number + 99) / 100;
  }
}
```

## kata 24

### Consigne

Given an array of integers, return a new array with each value doubled.

For example:

```bash
[1, 2, 3] --> [2, 4, 6]
```

### My solution

```java
 import java.util.Arrays;

public class Maps {
  public static int[] map(int[] arr) {
    return Arrays.stream(arr).map(n -> n * 2).toArray();
  }
}
```

### Best pratice

```java
import java.util.*;
public class Maps {
  public static int[] map(int[] arr) {
      return Arrays.stream(arr).map(x -> x*2).toArray();
  }
}
```

#### Or

```java
public class Maps {

  public static int[] map(int[] inputArray) {

  for (int i = 0; i < inputArray.length; i++) {
      inputArray[i] = inputArray[i]*2;
    }
  return inputArray;
  }
}
```

## kata 25

## Consigne

Return the number (count) of vowels in the given string.

We will consider a, e, i, o, u as vowels for this Kata (but not y).

The input string will only consist of lower case letters and/or spaces.

## My Solution

```java
public class Vowels {

  public static int getCount(String str) {
    int vowels = 0;
 for (int i =0 ; i < str.length(); i++){
   char c = str.charAt(i);
   if (c =='a' || c== 'e'|| c == 'i'|| c== 'o' || c == 'u'){
     vowels++;
   }
   }
   return vowels;
 }
}
```

### Best pratice

```java

public class Vowels {

    public static int getCount(String str) {
        return str.replaceAll("(?i)[^aeiou]", "").length();
    }

}
```

## Kata 26

### Consigne

Trolls are attacking your comment section!

A common way to deal with this situation is to remove all of the vowels from the trolls' comments, neutralizing the threat.

Your task is to write a function that takes a string and return a new string with all vowels removed.

For example, the string "This website is for losers LOL!" would become "Ths wbst s fr lsrs LL!".

Note: for this kata y isn't considered a vowel.

### My solution

```java
public class Troll {
    public static String disemvowel(String str) {
        // Code away...
      return str.replaceAll("(?i)[aeiou]", "");
    }
}
```

### Best pratice

```java
public class Troll {
    public static String disemvowel(String Z) {
        return Z.replaceAll("(?i)[aeiou]" , "");
    }
}
```
