# Topic 1. Random Number Generation

In class and in the textbook, you have encountered the `Random` class. This is a perfectly fine thing to use. It is much more elegant than using `Math.random()` 99% of the time. However, College Board does not place nearly as much emphasis on this as they do on `Math.random()`.

**Key differences between `Math.random()` and the `Random` class:**
`Math.random()` is a *static function* - this means we don't have to create a class to use this function. For example:
```java
double random = Math.random();
System.out.println("Random decimal: " + random);
```
Note how we had to store the result of `Math.random` in a `double`. This is because it returns a `double` from and including 0 up to but never exactly 1. (For you precalculus people, this is [0,1) in interval notation. )
This presents an issue. *How are we supposed to get random integers?* Well, College Board expects you to do the following:
```java
int min = 1; // minimum value
int max = 10; // maximum value
int rand = (int) (Math.random() * (max-min+1)) + min; // yields a number in from 1 to 10, including 1 and 10. (this is [1,10])
``` 
You must use parentheses in the given configuration to be marked as correct on the test (and consequently class assignments).
If you want to make a number in [`min`, `max`), just remove the +1 in the `(max-min+1)`.



Now, the alternate method is to use the `Random` class.
Example code:
```java
package examplecodetest;
import java.util.Random; // you shouldn't type this if you use an older Java version (one reason why it's very unlikely you'll be tested on it)
public class Test
{
  public static void main(String[] args)
  {
    Random r = new Random();
    int rand1 = r.nextInt(); // this can be any integer, be it positive or negative
    int rand2 = r.nextInt(10); // this is any random integer from 0 (inclusive) to 10 (exclusive).
    System.out.println("First random number: " + rand1 + "; Second random number [0, 10): " + rand2);
  }
}
```

Remember that likelihood of certain specific topics appearing is mostly speculation.
