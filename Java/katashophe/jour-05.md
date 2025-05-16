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
