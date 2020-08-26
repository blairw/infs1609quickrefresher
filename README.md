# INFS1609 Quick Refresher
This is a quick refresher of INFS1609 for UNSW students who are taking later courses that assume INFS1609 as prerequisite knowledge, but might need some help jogging their memory. 😅

These notes will reacquaint you with some concepts that you have previously studied in depth, but these notes will not fully explain these concepts for you. For that, please refer to your notes from when you studied INFS1609.

**Contents:**

- [💻 1. Elementary Programming](#elementaryprogramming)
- [👉🏻 2. Selections](#selections)
- [🧵 3. Loops](#loops)
- [🔨 4. Methods](#methods)
- [📚 5. Arrays](#arrays)
- [📦 6. Object-Oriented Programming](#oop)
- [🗃 7. ArrayLists](#arraylists)
- [💭 8. Abstract Classes and Interfaces](#abstractclassesvinterfaces)
- [💡 9. Tips and Tricks](#tipsandtricks)

_INFS1609 is a programming course taught by the School of Information Systems and Technology Management (SISTM) at UNSW Business School. We pride ourselves on high-quality student-centric teaching. To find out more about us, please see the [UNSW SISTM website](https://www.business.unsw.edu.au/about/schools/information-systems-technology-management)._

---

<a name="elementaryprogramming"></a>
## 💻&nbsp;&nbsp;1. Elementary Programming

Do you remember these?

- Java's numeric primitive data types: `byte`, `short`, `int`, `long`, `float`, `double`
- Java's text-related data types:`char` and `String`
- Operators (e.g. `x + y`) and increments/decrements (e.g. `x++`, `y--`)
- Implicit and explicit casting

Some handy string-related methods that you might find useful:

- `toLowerCase()` and `toUpperCase()`
- `trim()`
- `concat(..)`
- `substring(..)`

Reading a character from the command line:

```java
Scanner input = new Scanner(System.in);    // Do you remember what a Scanner is?
System.out.print("Enter a character: ");   // Why print(..) and not println(..)?
                                           // Also, what are System.in and System.out?
String s = input.nextLine();               // Why nextLine() and not next()?
char ch = s.charAt(0);                     // What is charAt(..)?
System.out.println(ch)                     // What would we see?
```

<a name="selections"></a>
## 👉🏻&nbsp;&nbsp;2. Selections

Boolean shorthands:

```java
boolean myBool1 = (x > y);
boolean myBool2 = (x > 0 && x < 100 && x > y);
```

If-else statements:

```java
if (x > y) {
    doSomething();
} else {
    doSomethingElse();
}
```

Ternary operator:

```java
int numberOfCats = (numberofRooms > 2 ? desiredCats * 2 : desiredCats)
```

Switch statements:

```java
switch (numberOfRooms) {
    case 1:
        numberOfCats = 2;
        break;
    case 2:
        numberOfCats = 5;
        break;
    default:
        numberOfCats = 0;
        break;
}
```

<a name="loops"></a>
## 🧵&nbsp;&nbsp;3. Loops

While-loop:

```java
while (x > y) {
    x++;
}
```

For-loop:

```java
for (int i = 5000; i > 1; i--) {
    System.out.println(i + " bottles of beer on the wall");
}
```

<a name="methods"></a>
## 🔨&nbsp;&nbsp;4. Methods

By the end of INFS1609, you should understand what every part of this means:

```java
public static void main(String[] args) {
    sayHelloTo("World"); // invoking sayHelloTo(..)
}

public static void sayHelloTo(String recipient) {
    System.out.println("Hello " + recipient);
}
```

Especially in relation to the first method:

- `public` modifier &mdash; as opposed to `private`, `protected`
- `static` modifier
    - ⚠️ If you're ever asked what this means, _"it doesn't change"_ is not an adequate answer - that's more like a definition for `final`!
    - 💡 When do we use `static` and when do we not use `static`? The answer involves objects.
- `void` return value type &mdash; as opposed to `int`, `String`, `boolean` etc.
- `main` &mdash; what's the significance of this method?
- `String[] args` as the parameters &mdash; why?

<a name="arrays"></a>
## 📚&nbsp;&nbsp;5. Arrays

An array is an ordered set of elements of the same type. It should not be confused with an object, a set of elements of different types.

Create a blank array of a fixed size:

```java
int[] arrayAlpha = new int[50];
String[] arrayBravo = new String[10];
```

Create an array with set notation:

```java
int[] arrayCharlie = {3, 1, 4, 1, 5, 9, 2};
String[] arrayDelta = {"Fish Fingers", "Custard"};
```

Access an array element (⚠️ note that elements are numbered `0` .. `length - 1`):

```java
arrayAlpha[0] = 42;
x = arrayAlpha[0];
```

<a name="oop"></a>
## 📦&nbsp;&nbsp;6. Object-Oriented Programming

**Object-Oriented Programming (OOP)** is the process of designing and implementing programs as systems of interacting objects. It is fundamentally based around two ideas:
- **💭 Abstraction:** dividing the program into chunks (called objects) with its own data (stored in variables called fields) and methods. Similar objects are grouped together by object classes which have the same fields and methods but different field contents. Objects that belong to a class are called object instances. Advantages of abstraction include:
    - code reusability
    - clearer design
    - easier debugging
- **📦 Encapsulation:** each object hides its implementation details from outsiders. Outsiders can only access the private implementation (how it works) through a public interface (how it can be used).

I'd be remiss if I didn't include some variation of [the classic](https://twitter.com/iamdevloper/status/727854065426804738):

```java
public class Animal {
    private String name;
    // private - to ensure encapsulation

    public String getName() {
        return this.name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public Animal(String name) {
        this.setName(name);
    }
}

public class Cat extends Animal {
    // abstracting the idea of a Dog against the idea of an Animal

    private int meowLevel;

    public int getMeowLevel() {
        return this.meowLevel();
    }

    public void setMeowLevel(int meowLevel) {
        this.meowLevel = meowLevel;
    }

    public Cat(String name, int meowLevel) {
        super(name);
        this.setMeowLevel(meowLevel);
    }
}
```

OOP blesses us with the joy of **polymorphism**. Polymorphism is the concept of an object having different forms &mdash; behaviours in different contexts. For example, a human being can be thought of as a "user" in the context of a computer login system, a "citizen" in the context of politics, a "player" in the context of a game, a "customer" in the context of a shopping website, a "mass" in the context of physics, etc. In Java this manifests itself in the ability to do this:

```java
Animal myPet = new Cat("Purrfect", 52);
```

I can put an assign a `Cat` into a variable that is not of type `Cat` per se but rather of type `Animal`, which only works because `Cat extends Animal`.


<a name="arraylists"></a>
## 🗃&nbsp;&nbsp;7. ArrayLists

Object-Oriented Programming also helps us make sense of ArrayLists. An ArrayList is an object class from the Java Class Library that does what an array of primitive types can do, but with methods that automate creating/reading/updating/deleting elements. Since ArrayList is an object class, every ArrayList object in existence is really an object that encapsulates traditional arrays and permits access to them through public methods like `add`, `get`, `set`, etc. Since ArrayLists come from the JCL, they must be explicitly imported: `import java.util.ArrayList;`.

When creating an ArrayList we need to specify the type of objects it contains in the type parameter, which is the bit bounded by angled brackets. Note that an ArrayList's type parameter must be a class type, not a primitive type. If we want an ArrayList that contains items of a primitive type, we use object- wrappers, e.g. `Integer` instead of `int`, `Character` instead of `char`, `Boolean` instead of `boolean`, etc.

| | Array of primitive types | ArrayList |
| - | - | - |
| **Nature** | fixed-length list | variable-length list |
| **Declaration** | `private int[] myNumbers;` | `private ArrayList<Integer> myNumbers;` |
| **Construction** | `private String[] myList = new String[52];` | `private ArrayList<String> myList = new ArrayList<String>();` |
| **Obtain size** | `myList.length` | `myList.size()` |
| **Create new element** | Create new array, copy elements from old array, insert new element, replace old array with new array | `myStrings.add("Blair");` |
| **Read element at given index** | `x = myList[0];` | `x = myList.get(0);` |
| **Update element** | `myList[1] = "Bob";` | `myList.set(1, "Bob");` |
| **Delete element** | Create new array, copy some elements from old array, remove the element to delete, copy the rest, replace old array with new array | `myStrings.remove(12)` |
| **Make an exact copy** | Create a new array of the same size and populate it using a for-loop | `private ArrayList<String> copiedList = new ArrayList<String>(myList);` (but see warning below) | 
| **Process using a for-loop** | `for (int i = 0; i < myList.length; i++) {...}` (`i` becomes established as the current **index**) | `for (String thingy : myList) {...}` (`thingy` becomes established as the current **element**)

⚠️ **Warning:** When you do something like `x = y` where these are both Objects (not primitives), `x` becomes a **reference** to `y`. This means that if you change `x`, you also change `y`.

<a name="abstractclassesvinterfaces"></a>
## 💭&nbsp;&nbsp;8. Abstract Classes and Interfaces

- An **abstract class** is a class that couldn't actually be instantiated, but defines the supertype of some other class(es) that could be instantiated. For example an `Animal` that is neither a `Cat` nor a `Dog` nor a `Fish` nor ... (you get the idea: there's no Animal that is not one of the subtypes).

- An **interface** is a promise to fulfil some functionality. It's similar to an abstract class but:
    1. The intention is different (promise to fulfil vs. ideal-typical abstraction / _is-a_ relationship vs. _is-a-kind-of_ relationship), and
    2. Interfaces can't have constructors, and
    3. A class can only extend one abstract class but could implement multiple interfaces.

<a name="tipsandtricks"></a>
## 💡&nbsp;&nbsp;9. Tips and Tricks

- 🤔&nbsp;&nbsp;Just because the program compiles without errors doesn't mean that it will run properly.
- 🐤&nbsp;&nbsp;Sometimes you just need to explain it to somebody - a friend, a colleague, or even a rubber duck.
- 💭&nbsp;&nbsp;If you're getting lost in your own logic, break up your code into smaller manageable chunks.
- 📝&nbsp;&nbsp;Document your code well, so that it makes sense - to others and to your future self!
- 🍀&nbsp;&nbsp;Good luck with your studies!