# Technical Questions - Set 2

## Part 1 - Whiteboarding Problem

Implement a function that takes an unsorted array of integers and returns a new array with duplicate elements removed, while preserving the original order of elements.

```java
int[] input = {4, 2, 4, 5, 2, 3, 1};
int[] result = removeDuplicates(input);
// Expected output: [4, 2, 5, 3, 1]
```

Edge Cases:
- Empty array should return an empty array.
- Array with one element should return the same array.

There are several possible solutions of various time / space complexities.

HashSet Example Solution:
```java
import java.util.*;

class RemoveDuplicates {
    public static int[] removeDuplicates(int[] arr) {
        if (arr == null || arr.length == 0) {
            return new int[0]; // Return an empty array if input is null or empty
        }

        LinkedHashSet<Integer> seen = new LinkedHashSet<>();
        for (int num : arr) {
            seen.add(num); // Adds only unique elements while maintaining order
        }

        // Convert the LinkedHashSet to an int array
        int[] result = new int[seen.size()];
        int index = 0;
        for (int num : seen) {
            result[index++] = num;
        }

        return result;
    }

    public static void main(String[] args) {
        int[] input = {4, 2, 4, 5, 2, 3, 1};
        int[] result = removeDuplicates(input);
        
        System.out.println(Arrays.toString(result)); // Output: [4, 2, 5, 3, 1]
    }
}
```

- Time complexity: O(n). HashSet insertion is O(1) on average.
- Space complexity: O(n). To store set of unique elements.

Non-HashSet Example Solution:
```java
import java.util.*;

class RemoveDuplicatesManual {
    public static int[] removeDuplicates(int[] arr) {
        if (arr == null || arr.length == 0) {
            return new int[0]; // Return empty array if input is null or empty
        }

        List<Integer> uniqueList = new ArrayList<>();
        
        for (int num : arr) {
            // Manually check if the number is already in the list
            boolean exists = false;
            for (int unique : uniqueList) {
                if (unique == num) {
                    exists = true;
                    break;
                }
            }
            if (!exists) {
                uniqueList.add(num);
            }
        }

        // Convert list to array
        int[] result = new int[uniqueList.size()];
        for (int i = 0; i < uniqueList.size(); i++) {
            result[i] = uniqueList.get(i);
        }

        return result;
    }

    public static void main(String[] args) {
        int[] input = {4, 2, 4, 5, 2, 3, 1};
        int[] result = removeDuplicates(input);
        
        System.out.println(Arrays.toString(result)); // Output: [4, 2, 5, 3, 1]
    }
}
```

- Time complexity: O(n^2). Nested loop checking `uniqueList`.
- Space complexity: O(n). To store list of unique elements.
## Part 2 - Programming and Web Concepts

### Polymorphism

Question: What is polymorphism? Can you give an example where it might be used?

Answer:
- Polymorphism is an object-oriented programming principle that allows different classes to be treated as instances of the same interface or superclass. 
- It enables methods to be called on different types of objects in a uniform way.

Example:
Imagine a `Shape` class with a `draw()` method. Different subclasses (`Circle`, `Rectangle`) implement `draw()` differently.

```java
abstract class Shape {
    abstract void draw();
}

class Circle extends Shape {
    @Override
    void draw() {
        System.out.println("Drawing a Circle");
    }
}

class Rectangle extends Shape {
    @Override
    void draw() {
        System.out.println("Drawing a Rectangle");
    }
}

public class Main {
    public static void main(String[] args) {
        Shape shape1 = new Circle();
        Shape shape2 = new Rectangle();

        shape1.draw(); // Output: Drawing a Circle
        shape2.draw(); // Output: Drawing a Rectangle
    }
}
```

This allows extending functionality without modifying existing code (such as adding new shapes) without changing the existing logic.
### Composition vs. Inheritance

Question: What is composition vs. inheritance? Is one preferable? Give an example.

Answer:
- Inheritance: "Is-a" relationship. A subclass extends a parent class, inheriting its methods and properties.
- Composition: "Has-a" relationship. A class contains an instance of another class instead of inheriting from it.

Example:

Inheritance:  
A `Bird` inherits from `Animal`.

```java
class Animal {
    void makeSound() {
        System.out.println("Some generic animal sound");
    }
}

class Bird extends Animal {
    void fly() {
        System.out.println("Bird is flying");
    }
}

public class Main {
    public static void main(String[] args) {
        Bird bird = new Bird();
        bird.makeSound(); // Inherited method
        bird.fly();
    }
}
```

Composition:  
A `Car` has an `Engine` instead of inheriting from `Engine`.
```java
class Engine {
    void start() {
        System.out.println("Engine started");
    }
}

class Car {
    private Engine engine;

    Car() {
        engine = new Engine();
    }

    void startCar() {
        engine.start();
    }
}

public class Main {
    public static void main(String[] args) {
        Car myCar = new Car();
        myCar.startCar(); // Output: Engine started
    }
}
```

Which is preferable?
- Prefer composition when classes do not share a strict hierarchical relationship.
- Use inheritance when an object truly "is-a" another type (e.g., `Dog` is an `Animal`).
- Composition is often favored as it promotes flexibility and avoids deep inheritance trees, which can make code harder to maintain.
