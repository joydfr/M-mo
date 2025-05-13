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
