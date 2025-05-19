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
