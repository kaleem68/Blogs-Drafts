Java Strings are immutable, which means that once the String class object is created, it cannot be modified.

### Immutability
```java
  String str = "You cannot modify."
  str = str + "me"
```
When we appended the value "me" to the **str** variable, a new String object was created and assigned to **str**. The original string "You cannot modify" does not get modified.

### Performance
Appending strings using the "+" operation has significant performance issues.

Whenever an append "+" is used, a new string object is created in the heap memory.

To modify the strings efficiently, we should use the StringBuilder class and the **append** method to modify the existing String.

### String Modification
Use StringBuilder class to modify the string; this does not create a new String object but modifies the existing object.
```java
  StringBuilder str = new StringBuilder("You can modify.");
  str.append("me");
```
### Benchmark
Let's do the `Append` operation performance benchmark using String and StringBuilder; consider the followings.
 
- Consider 10 data points
 - ```inputSample = [100k, 200k, 300k, 400k, 500k, 600k, 700k, 800k, 900k, 1m]```
- Starting with an empty string and append "a" **n** times. where n = inputSample[i] i.e ```n = 700k```
- ```We want to know how much time it takes to append a string n times using String and StringBuilder ```
 
#### String Class
```java
public class StringBenchmark {
    public static void main(String[] args) {
        String appendCharacter = "a";

        int inputSample[] = new int[]{
                100000, 200000, 300000, 400000,
                500000, 600000, 700000, 800000,
                900000, 1000000};

        for (int n : inputSample) {
            double startTime = System.nanoTime();
            testStringAppend(n, "", appendCharacter);
            double endTime = System.nanoTime();
            double duration = (endTime - startTime) / 1000000000;
            String seconds = String.format("%.2f", duration);
            System.out.println("n = " + n + ": seconds: " + seconds);
        }
    }

    static void testStringAppend(int n, String str, String appendCharacter) {
        for (int i = 1; i <= n; i++) {
            str += appendCharacter;
        }
    }
}
```
##### String Class Results
```
n = 100000: seconds: 0.38
n = 200000: seconds: 0.99
n = 300000: seconds: 2.14
n = 400000: seconds: 3.74
n = 500000: seconds: 5.79
n = 600000: seconds: 8.28
n = 700000: seconds: 11.16
n = 800000: seconds: 14.65
n = 900000: seconds: 18.29
n = 1000000: seconds: 22.43
```

#### StringBuilder Class
```java
public class StringBenchmark {
    public static void main(String[] args) {
        String appendCharacter = "a";

        int inputSample[] = new int[]{
                100000, 200000, 300000, 400000,
                500000, 600000, 700000, 800000,
                900000, 1000000};

        for (int n : inputSample) {
            double startTime = System.nanoTime();
            testStringAppend(n, "", appendCharacter);
            double endTime = System.nanoTime();
            double duration = (endTime - startTime) / 1000000000;
            String seconds = String.format("%.2f", duration);
            System.out.println("n = " + n + ": seconds: " + seconds);
        }
    }
    static void testStringAppend(int n, String str, String appendCharacter) {
        for (int i = 1; i <= n; i++) {
            str += appendCharacter;
        }
    }
}
```

```java
n = 100000: seconds: 0.0027
n = 200000: seconds: 0.0013
n = 300000: seconds: 0.0015
n = 400000: seconds: 0.0015
n = 500000: seconds: 0.0018
n = 600000: seconds: 0.0022
n = 700000: seconds: 0.0026
n = 800000: seconds: 0.0029
n = 900000: seconds: 0.0032
n = 1000000: seconds: 0.0036

```

# Conclusion
- Modifying String creates a new String in the heap memory, to modify the content of the String we should consider StringBuilder class, as StringBuilder has a constant modification time.
- Any attempt to modify the String class creates a new object in the memory which has signifnicant performence draw back as shown in String class benchmark.
- Pick StringBuilder over String class in all cases where you want to modify the content of the string.
