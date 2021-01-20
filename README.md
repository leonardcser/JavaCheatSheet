# CS-107: Introduction à la Programmation
# Table of contents
  * [1. Scanner](#1-scanner)
  * [2. Math](#2-math)
  * [3. Switch Statements](#3-switch-statements)
  * [4. Logic Operators](#4-logic-operators)
  * [5. Loops](#5-loops)
  * [6. Arrays](#6-arrays)
  * [7. Lists](#7-lists)
  * [8. Strings](#8-strings)
  * [9. Characters](#9-characters)
  * [10. Object Orientated Programming](#10-object-orientated-programming)
    + [10.1 Constructors](#101-constructors)
    + [10.2 Copy Constructors](#102-copy-constructors)
    + [10.3 toString() & equals()](#103-tostring-----equals--)
    + [10.4 instanceOf](#104-instanceof)
    + [10.5 instanceof vs getclass()](#105-instanceof-vs-getclass--)
    + [10.6 Hierarchy](#106-hierarchy)
  * [11. Enums](#11-enums)
  * [12. Inner Classes](#12-inner-classes)
  * [13. Exceptions](#13-exceptions)


## 1. Scanner

```java
import java.util.Scanner;

Scanner scanner = new Scanner(System.in);

// Integer
int n = scanner.nextInt();

// String
String s = scanner.nextLine();  // reads until \n
String s = scanner.next();      // reads until space
```

## 2. Math

```java
int max = Integer.MAX_VALUE;
int min = Integer.MIN_VALUE;

Random rand = new Random();
rand.nextInt(10);   // from 0 (inclusive) to 10 (exclusive)

Math.min(x, y);
Math.max(x, y);
Math.round(x);
Math.pow(x, y);
Math.sqrt(x, y);
Math.abs(x);
Math.PI

// Note: cast to double or float before division
```

## 3. Switch Statements

```java
switch (x) {
  case 1:
    // code
    break;
  case 2:
    // code
    break;
  case ...:
    // code
    break;
  default:
    // code
    break;
}
```

## 4. Logic Operators

```java
// ^    xor (TRUE if x is different to y)

if ((n >= 1) ^ (n <= 10)) {
}

--------------------------

// ?    ternary operator

var myVar = (logical expression) ? valueIfTrue : valueIfFalsers
```

## 5. Loops

```java
// Fori Loop:
for (i = 0; i < 5; ++i) {
}

// Foreach Loop:
for (int myNum : arr) {
}

// While Loops:
do {
} while (condition);

while (condition) {
}
```

## 6. Arrays

```java
int[] arr = {100, 200, 300, ... };
int[] arr = new int[arraySize];

int[][] multiArr = new int[m][n];
int[][] multiArr = {{0, 1, 2, 3, 42}, {4, 5, 6}, {7, 8}, {9, 0, 1}};

(arr1 == arr2)   // Compares the references in memory
arr1 = arr2      // Both tables now have the same reference in memory

var[] arr = list.toArray(new var[0]);   // Convert list to array

// Methods.......................................................................
arr.length       // Length of the array (.length() with brackets for Strings)
arr.clone()

// Sorting
Arrays.sort(arr);
Arrays.sort(arr, Collections.reverseOrder());
```

## 7. Lists

```java
import java.util.List;
import java.util.ArrayList;

// Integer, Double, String, Character...
List<Type> list = new ArrayList<Type>()
List<Integer> list = Arrays.asList(11, 4, 10);

// Converting int array to list - Java 8
int[] arr = new int[] {1,2,3,4,5};
List<Integer> list = Arrays.stream(arr).boxed().collect(Collectors.toList());
// Converting Integer array to list
Integer[] arr = new Integer[] { 1, 2, 3 };
List<Integer> list = Arrays.asList(arr);

// Methods.......................................................................
list.size()
list.add(x)
list.get(i)
list.set(i, x)
list.isEmpty()
list.contains(x);
list.clear()
list.remove(i)

list.removeIf(e -> e.x (boolean condition) );

// Min and max in list
int min = Collections.min(list);
int max = Collections.max(list);

// Frequency
int freq = Collections.frequency(list, x);

// Sorting
Collections.sort(list);
Collections.sort(list, Collections.reverseOrder());

// Compare elements of lists
list.get(0).equals(list.get(1))
```

## 8. Strings

```java
String s1 = "abc";        // nouvelle référence "abc"
String s2 = "abc";        // stoque dans la  référence "abc"
String s3 = s2;           // stoque dans la  référence "abc"
String s4 = s1 + "";      // nouvelle référence "abc"
String s5 = "ab" + 'c';   // nouvelle référence "abc"
String s6 = s5.intern();  // stoque dans la  référence "abc"

s1 == s2  //--> TRUE
s1 == s3  //--> TRUE
s1 == s4  //--> FALSE  -  pas dans la même référence "abc"
s1 == s5  //--> TRUE
s1 == s6  //--> TRUE

--------------------------

// .equals(str)
String s1 = "abc";
String s2 = "aBc";
String s3 = s1 + "";

System.out.println(s1.equals(s3));  //--> TRUE
System.out.println(s1.equals(s2));  //--> FALSE

--------------------------

// .compareTo(str)
String s1 = "abc";
String s2 = "aBc";
String s3 = "abc";
	
System.out.println(s1.compareTo(s3));  // 0
System.out.println(s1.compareTo(s2));  // 32

/**
Returns an int value:
- 0 if the string is equal to the other string.
- < 0 if the string is lexicographically less than the other string
- > 0 if the string is lexicographically greater than the other string
	(more characters)
**/

// Methods.......................................................................
str.length()
str.indexOf('a')
str.replace('x','y')
	String s1 = "magic";
	String s2 = magic.replace('a','*');    // s2 = "m*gic" & s1 = "magic"
str.substring(i, j)
	String s1 = "unmagical";
	String s2 = magic.substring(2, 8);    // s2 = "magical" & s1 = "unmagical"
str.charAt(i)
str.split(".");

int x = Integer.parseInt("9");
String s = String.valueOf(30);
String.format("%02d.%02d.%d", day, month, year);
/**
%c - char
%d - integer
%e - floating (scientific notation)
%f - floating
%s - String
**/
```

## 9. Characters

```java
char backspace = '\b';
char tab = '\t';
char newline = '\n';
char carriageReturn = '\r';
char backslash = '\\';
char quote = '\'';

// char + int -> int
```

## 10. Object Orientated Programming

### 10.1 Constructors

```java
public class Car {
  int modelYear;
  String modelName;

  public Car(int year, String name) {
    modelYear = year;
    modelName = name;
  }

  public Car() {
    modelYear = 2005;
    modelName = "BMW";
  }

  public Car() {
    this(2005, "BMW")
  }

  public static void main(String[] args) {
    Car myCar = new Car(1969, "Mustang");   // RIGHT HERE
    Car myCar2 = new Car();                 // DEFAULT VALUES
    System.out.println(myCar.modelYear + " " + myCar.modelName);
  }
}

// Outputs 1969 Mustang
```

### 10.2 Copy Constructors

```java
class Rectangle {

  public Rectangle(Rectangle autreRectangle) {
    hauteur = autreRectangle.hauteur;
    largeur = autreRectangle.largeur;
  }

  public static void main(String[] args) {
    Rectangle r1 = new Rectangle(12,3 14.5)
    Rectange r2 = new Rectangle(r1)

    Rectangle r1 = new Rectangle(12,3 14.5)
    Rectange r2 = r1.clone
  }
}
```

### 10.3 toString() & equals()

```java
class Rectangle {
  private double hauteur;
  private double largeur;

  @Override
  public String toString() {
    return "Rectange " + hauteur " x " + largeur
  }
	
  @Override
  public boolean equals(Object o) {
    if (o == null) {
      return false;
    } else if (o.getClass() != getClass()) {
      return false;
    } else {
      Rectangle r = (Rectange) o;
      return (largeur == r.largeur && hauteur == r.hauteur)
    }
  }

class Exemple {
  public static void main(String[] args) {
    System.out.println(new Rectangle(4.0, 5.0)) // Rectangle 4.0 x 5.0

    Rectangle r1 = new Rectangle(4.0, 5.0);
    Rectangle r2 = new Rectangle(4.0, 5.0);

    if (r1.equals(r2)) {
      //...
    }
  }

}
```

### 10.4 instanceOf

```java
// Java program to demonstrate working of instanceof 
  
// Creating sample classes with parent Child 
// relationship 
class Parent {...} 
class Child extends Parent { } 
  
class Test { 
  public static void main(String[] args) { 
    Child cobj = new Child(); 

    // A simple case 
    if (cobj instanceof Child) 
      System.out.println("cobj is instance of Child"); 
    else
      System.out.println("cobj is NOT instance of Child"); 

    // instanceof returns true for Parent class also  
    if (cobj instanceof Parent) 
      System.out.println("cobj is instance of Parent"); 
    else
      System.out.println("cobj is NOT instance of Parent"); 

    // instanceof returns true for all ancestors (Note : Object 
    // is ancestor of all classes in Java)  
    if (cobj instanceof Object) 
      System.out.println("cobj is instance of Object"); 
    else
      System.out.println("cobj is NOT instance of Object");            
    } 
}

// OUPUT
cobj is instance of Child
cobj is instance of Parent
cobj is instance of Object
```

### 10.5 instanceof vs getclass()

It depends if you consider if a subclass of a given class is equals to its parent.

```java
class LastName {
(...)
}

class FamilyName extends LastName {
(...)
}

```

Here I would use 'instanceof', because I want a LastName to be compared to FamilyName

- BREAKS SYMETRY a==b but b≠a

```java
class Organism {
(...)
}

class Gorilla extends Organism {
(...)
}
```

Here I would use 'getClass()', because the class already says that the two instances are not equivalent.

- PRESERVES SYMETRY a==b and b==a

### 10.6 Hierarchy

**Class methods:** "A-UN" (extends)

**Super classes:** "EST-UN" (extends)

- Always declare constructor from super class
- Always call super() constructor

```java
class Animal {
  public void animalSound() {
    System.out.println("The animal makes a sound");
  }
}

class Pig extends Animal {
  public void animalSound() {
    System.out.println("The pig says: wee wee");
  }
}

class Dog extends Animal {
  public void animalSound() {
    System.out.println("The dog says: bow wow");
  }
}

class MyMainClass {
  public static void main(String[] args) {
    Animal myAnimal = new Animal();  // Create a Animal object
    Animal myPig = new Pig();  // Create a Pig object
    Animal myDog = new Dog();  // Create a Dog object
    myAnimal.animalSound();
    myPig.animalSound();
    myDog.animalSound();
  }
}
```

**Abstract classes:**

- Force all sub classes to define abstract methods
- Cannot create instance of abstract class

```java
// Abstract class
abstract class Animal {
  // Abstract method (does not have a body)
  public abstract void animalSound();
  // Regular method
  public void sleep() {
    System.out.println("Zzz");
  }
}

// Subclass (inherit from Animal)
class Pig extends Animal {
  public void animalSound() {
    // The body of animalSound() is provided here
    System.out.println("The pig says: wee wee");
  }
}

class MyMainClass {
  public static void main(String[] args) {
    Pig myPig = new Pig(); // Create a Pig object
    myPig.animalSound();
    myPig.sleep();
  }
}
```

**Final classes:**

- Cannot have sub-classes

**Interfaces:** "SE-COMPORTE-COMME" (implements)

- Goal: impose some classes to have specific content

```java
// (<= Java 7)
-------------------
interface Graphique {
  public final static MAX = 200;

  void dessiner();
  boolean canDraw();
}

class Filet extends Entite implements Graphique {
  public void dessiner();
  public boolean canDraw();
}

// (>= Java 8)
-------------------
interface Graphique {
  public final static MAX = 200;

  void dessiner();
  default boolean canDraw() {
    return false;
  }
}

class Filet extends Entite implements Graphique {
  public void dessiner();
  // la methode n'est pas forcée à redéfinir
  default public boolean canDraw();
}
```

## 11. Enums

```java
public class MyClass {
  enum Level {
    LOW,
    MEDIUM,
    HIGH

    // can add attributes
    private final String frenchName;

    // can add constructor
    private Level(String frenchName) {
      this.frenchName = frenchName;
    }

    // can add methods
    public String frenchName() {
      return frenchName;
    }

    // can return new (add to enum)
    public Vector2D toVector() {
      switch(this) {
        case LOW:
          return new Vector2D(0, 1);
        case MEDIUM:
          //...
      }
    }
  }

  public static void main(String[] args) {
    Level myVar = Level.MEDIUM; 
    System.out.println(myVar);
  }
}
```

## 12. Inner Classes

```java
class OuterClass {
  int x = 10;

  class InnerClass {
    int y = 5;
  }
}

public class Main {
  public static void main(String[] args) {
    OuterClass myOuter = new OuterClass();
    OuterClass.InnerClass myInner = myOuter.new InnerClass();
    System.out.println(myInner.y + myOuter.x);
  }
}

// Outputs 15 (5 + 10)

------------------------

class OuterClass {
  int x = 10;

  private class InnerClass {
    int y = 5;
  }
}

public class Main {
  public static void main(String[] args) {
    OuterClass myOuter = new OuterClass();
    OuterClass.InnerClass myInner = myOuter.new InnerClass();
    System.out.println(myInner.y + myOuter.x);
  }
}

/**
   Main.java:13: error: OuterClass.InnerClass has private access in OuterClass
       OuterClass.InnerClass myInner = myOuter.new InnerClass();
                 ^
**/
------------------------

class OuterClass {
  int x = 10;

  static class InnerClass {
    int y = 5;
  }
}

public class Main {
  public static void main(String[] args) {
    OuterClass.InnerClass myInner = new OuterClass.InnerClass();
    System.out.println(myInner.y);
  }
}

// Outputs 5
```

## 13. Exceptions

```java
// SYNTAX -----------------------------------------------------------------
try {
  // Protected code
} catch (ExceptionName e1) {
  // Catch block
} finally {
  // Always executes
}

/**
  Multiple Catch Blocks ---------------------------------------------------
  (All catch blocks must be ordered from most specific to most general)
**/
try {
  // Protected code
} catch (ExceptionType1 e1) {
  // Catch block
} catch (ExceptionType2 e2) {
  // Catch block
} catch (ExceptionType3 e3) {
  // Catch block
}

// (>= Java 7)
try {
  // Protected code
} catch (ExceptionType1 e1 | ExceptionType2 e2 | ExceptionType3 e3) {
  // Catch block
}

// Throwing exceptions ----------------------------------------------------
public Object pop() {
  Object obj;

  if (size == 0) {
      throw new EmptyStackException();
  }

  obj = objectAt(size - 1);
  setObjectAt(size - 1, null);
  size--;
  return obj;
}
```