## basic syntax
```java
public class Main {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
```
## Data Types
### Primitive types 
| Type      | Size    | Example                    |
|-----------|---------|----------------------------|
| `byte`    | 1 byte  | -128 to 127               |
| `short`   | 2 bytes | -32,768 to 32,767         |
| `int`     | 4 bytes | -2^31 to 2^31-1           |
| `long`    | 8 bytes | -2^63 to 2^63-1           |
| `float`   | 4 bytes | 3.4e-038 to 3.4e+038      |
| `double`  | 8 bytes | 1.7e-308 to 1.7e+308      |
| `char`    | 2 bytes | 'a', '1', '\\u0000'       |
| `boolean` | 1 bit   | `true`, `false`           |

### References Types
Arrays, Strings, Classes, interfaces

## Data Structures
#### Arrays
A fixed-size, indexed collection of elements of the same type.
```java
int[] arr = {1, 2, 3, 4};
System.out.println(arr[0]); // Output: 1
```

#### Strings
Immutable sequences of characters.
```java
String str = "Hello";
System.out.println(str.length());  // Output: 5
```
### Java Collection Frameworks
#### List
- Definition: Ordered collection (can contain duplicates).
- Common Implementations:
  - ArrayList: Resizable array.
  - LinkedList: Doubly linked list.
##### ArrayList
```java
import java.util.ArrayList;
List<Integer> list = new ArrayList<>();
list.add(1);
list.add(2);
System.out.println(list); // Output: [1, 2]
```
##### LinkedList
```java
import java.util.LinkedList;
List<String> list = new LinkedList<>();
list.add("A");
list.add("B");
System.out.println(list); // Output: [A, B]
```

#### Set
- Definition: Unordered collection (no duplicates).
- Common Implementations:
  - HashSet: Uses a hash table (fast).
  - TreeSet: Maintains elements in sorted order.
  - LinkedHashSet: Maintains insertion order.
##### Hashset
```java
import java.util.HashSet;
Set<Integer> set = new HashSet<>();
set.add(1);
set.add(2);
set.add(1); // Duplicate, will be ignored
System.out.println(set); // Output: [1, 2]
```

##### TreeSet
```java
import java.util.TreeSet;
Set<Integer> set = new TreeSet<>();
set.add(3);
set.add(1);
set.add(2);
System.out.println(set); // Output: [1, 2, 3]

```
#### Queue
- Definition: FIFO (First-In-First-Out) collection.
- Common Implementations:
  - PriorityQueue: Elements ordered by natural ordering or comparator.
  - Deque: Double-ended queue.
#### Priority Queue
```java
import java.util.PriorityQueue;
Queue<Integer> pq = new PriorityQueue<>();
pq.add(3);
pq.add(1);
pq.add(2);
System.out.println(pq.poll()); // Output: 1 (smallest element)
```

##### deque
```java
import java.util.ArrayDeque;
Deque<Integer> deque = new ArrayDeque<>();
deque.addFirst(1);
deque.addLast(2);
System.out.println(deque.pollFirst()); // Output: 1
```

#### Map
- Definition: Key-value pairs.
- Common Implementations:
  - HashMap: Unordered key-value pairs.
  - TreeMap: Sorted by keys.
  - LinkedHashMap: Maintains insertion order.
##### HashMap
```java
import java.util.HashMap;
Map<String, Integer> map = new HashMap<>();
map.put("A", 1);
map.put("B", 2);
System.out.println(map.get("A")); // Output: 1
```

##### TreeMap
```java
import java.util.TreeMap;
Map<String, Integer> map = new TreeMap<>();
map.put("B", 2);
map.put("A", 1);
System.out.println(map); // Output: {A=1, B=2}
```
#### Stacks
```java
import java.util.Stack;
Stack<Integer> stack = new Stack<>();
stack.push(1);
stack.push(2);
System.out.println(stack.pop()); // Output: 2
```

## Control flow
Same

## OOP

### Classes and objects
```java
class Car {
    String color;
    int speed;

    void displayInfo() {
        System.out.println("Color: " + color + ", Speed: " + speed);
    }
}

public class Main {
    public static void main(String[] args) {
        Car car = new Car();
        car.color = "Red";
        car.speed = 120;
        car.displayInfo();
    }
}

```
### Inheritance 
```java
class Animal {
    void sound() {
        System.out.println("Animal makes a sound");
    }
}

class Dog extends Animal {
    void sound() {
        System.out.println("Dog barks");
    }
}
```
### Polymorphism
```java
Animal myDog = new Dog();
myDog.sound(); // Output: Dog barks
```
### Encapsulation 
```java
class Person {
    private String name;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}
```
### Abstraction
```java
abstract class Shape {
    abstract void draw();
}

class Circle extends Shape {
    void draw() {
        System.out.println("Drawing Circle");
    }
}
```