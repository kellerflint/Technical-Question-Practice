# Technical Questions - Set 1

## Part 1 - Whiteboarding Problem

Implement a singly linked list queue in Java that supports adding elements to the end of the list.

Your implementation should include:
- A Node class to represent elements of the list.
- A LinkedListQueue class with the method `void add(int value)` which adds a node with the given value at the end of the list.


Example Usage:
```java
LinkedListQueue queue = new LinkedListQueue();
queue.add(10);
queue.add(20);
queue.add(30);
// Queue now contains: 10 -> 20 -> 30
```

Example Solution:
```java
class LinkedListQueue {
    private static class Node {
        int value;
        Node next;

        Node(int value) {
            this.value = value;
            this.next = null;
        }
    }

    private Node head;
    private Node tail;

    public LinkedListQueue() {
        this.head = null;
        this.tail = null;
    }

    // Adds a node to the end of the list (FIFO order)
    public void add(int value) {
        Node newNode = new Node(value);
        if (tail == null) { // If the queue is empty
            head = tail = newNode;
        } else {
            tail.next = newNode;
            tail = newNode;
        }
    }

    public static void main(String[] args) {
        LinkedListQueue queue = new LinkedListQueue();
        queue.add(10);
        queue.add(20);
        queue.add(30);
        // The queue now contains: 10 -> 20 -> 30
    }
}
```

## Part 2 - Programming and Web Concepts

### HTTP Status Codes: 401, 403, 404

Question: What do the HTTP status codes 401, 403, and 404 mean? How does 401 differ from 403?

Answer:
- 401 Unauthorized: The request lacks valid authentication credentials. The server expects authentication but hasn't received valid credentials.
- 403 Forbidden: The request is authenticated, but the user does not have permission to access the resource.
- 404 Not Found: The requested resource does not exist on the server.

401 vs. 403:
- 401 means authentication is required but not provided or is invalid.
- 403 means authentication is valid, but the user lacks the required permissions to access the resource.

### Interfaces and Abstract Classes

Question: What is an interface? What is the difference between an interface and an abstract class?

Answer:
An interface defines a contract that classes must implement, without providing any implementation itself.

Abstract Class vs. Interface:
- Abstract Class: Can have both abstract (unimplemented) and concrete (implemented) methods. Use abstract classes when you have shared behavior across subclasses.
- Interface: Only defines method signatures; no implementation. Use interfaces when multiple unrelated classes need to implement the same methods (e.g., Serializable in Java).

Example:
```java
abstract class Animal {
    abstract void makeSound(); // Abstract method

    void sleep() { // Concrete method
        System.out.println("Sleeping...");
    }
}

class Dog extends Animal {
    @Override
    void makeSound() {
        System.out.println("Bark");
    }
}

public class Main {
    public static void main(String[] args) {
        Dog myDog = new Dog();
        myDog.makeSound(); // Output: Bark
        myDog.sleep(); // Output: Sleeping...
    }
}
```

```java
interface Flyable {
    void fly();
}

class Bird implements Flyable {
    @Override
    public void fly() {
        System.out.println("Bird is flying");
    }
}

public class Main {
    public static void main(String[] args) {
        Flyable myBird = new Bird();
        myBird.fly(); // Output: Bird is flying
    }
}
```
