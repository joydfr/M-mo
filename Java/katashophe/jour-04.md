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
