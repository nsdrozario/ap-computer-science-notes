# Topic 2: `Scanner` class


## What is a Scanner?
Scanners are just a class type for grabbing user input. We may have situations where we can't just recompile our code when we get new information. To work around this issue, we just get information at runtime.

### How do I use it?
See here:
```java
import java.util.Scanner;
public class ScannerTest 
{
  {
    Scanner s = new Scanner(System.in); // We **MUST** feed System.in into the constructor!
    String tmp;
    System.out.print("Type something: ");
    tmp = s.nextLine(); // we want to grab the next line of input and store it in tmp
    System.out.println("You typed: " + tmp);
  }
}
```
As usual, we must import the class from its own package (most useful stuff will be in `java.util`, but you can just use Eclipse to search for what classes you need).
Then, we must construct a Scanner object. The constructor wants us to pass an input stream. We will be using `System.in` as the stream. 
Therefore, whenever you want to create a Scanner, you must type `Scanner variableName = new Scanner(System.in);`.

## How do scanners work?
Imagine a Scanner is like a scanner in real life, and imagine the user input is just a bunch of barcodes. When we call a scanner method, like `nextLine()`, `nextInt()`, or `nextDouble()`, we scan the "barcode" right under our scanner, and move our scanner down to the next "barcode". Our "barcode" depends on what we call; `nextInt` uses integers, `nextLine` uses strings, and `nextDouble`, well, uses doubles. Scanner uses spaces to separate different "barcodes".

But consider the following input:
```
I 
like 
pancakes. 
4096 
I 
have 
eaten 
3 
pancakes 
today.
```
What if we wanted to grab all the words over here in order, and do the same for numbers?
If we used one scanner, we could possibly grab them in order. Let `s` be a correctly defined `Scanner`, and `s1` , `s2`, `s3`, and so forth, be strings, and same for `n1` and onward for ints:
```java
s1 = s.nextLine(); 
s2 = s.nextLine();
s3 = s.nextLine();
n1 = s.nextInt();
s4 = s.nextLine();
s5 = s.nextLine();
s6 = s.nextLine();
n2 = s.nextInt();
s7 = s.nextLine();
s8 = s.nextLine();
```
Not only is this tedious, but look how we need to know **exactly** where the numbers are. If you don't do this in the right order, some of the numbers will be treated as strings. We won't always know where the numbers are! If we expect a string to be at some position on the line of "barcodes", but it's actually an int, we can't just backtrack and correct ourselves; it's too late.

But we do have a solution: *use multiple scanners*.

If we use multiple scanners:
```
Scanner scanStrings = new Scanner(System.in);
Scanner scanInts = new Scanner(System.in);
```
We can scan in any order provided we scan different types using different scanners!
So this would also be valid:
```
s1 = scanStrings.nextLine();
s2 = scanStrings.nextLine();
// ...
s8 = scanStrings.nextLine();
n1 = scanInts.nextInt();
n2 = scanInts.nextInt();
```
And this would work with any order of strings and ints as long as there are 8 strings and 2 ints; but we don't need to know the order of the words and numbers anymore.
This can be done more elegantly and efficiently using loops, but that is out of the scope of a lesson about Scanners.
