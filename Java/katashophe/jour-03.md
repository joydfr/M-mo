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

## kata 18

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
