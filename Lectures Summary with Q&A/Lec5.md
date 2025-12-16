
# Lecture 05: Polymorphism, Abstract Classes, and Interfaces


## Part 1: Lecture Summary & Explanation

### 1. Method Overriding
* **Definition:** When a subclass provides a specific implementation for a method that is already defined in its parent class.
* **Rules:**
    * The method name, return type, and arguments must match the parent's method **exactly**.
* **`@Override` Annotation:** It is good practice to place `@Override` above the method. It tells the compiler to check if you are actually overriding a parent method (preventing typos).



* **Overloading vs. Overriding:**
    * *Overloading:* Same method name, **different** arguments (in the same class).
    * *Overriding:* Same method name, **same** arguments (in a subclass).

### 2. Virtual Method Invocation (Polymorphism)
* **The Concept:** This is the magic of Java. When you call a method on an object, the JVM determines *at runtime* which version of the method to execute based on the **actual object** type, not the reference type.

* **Example:**
  ```java
  Employee e = new Manager();
  e.getDetails();

```

* Even though the variable `e` is of type `Employee`, the JVM sees that the object in memory is a `Manager`. If `Manager` overrides `getDetails()`, the **Manager's** version runs.

### 3. The `Object` Class

* Every class in Java automatically inherits from `java.lang.Object` (the root of the class hierarchy).
* **Key Methods to Override:**
* `toString()`: Returns a string representation of the object. By default, it prints the memory address. You should override this to print meaningful data (e.g., "Employee: John").
* `equals(Object o)`: Compares objects. By default, it checks if they are the *same instance* in memory (`==`). You usually override this to check if their *data* is equal.



### 4. Abstract Classes

* **Purpose:** To define a template for a group of subclasses. It models a general concept (like "Animal") that shouldn't exist on its own.
* **Characteristics:**
* Declared using the `abstract` keyword.
* **Cannot be instantiated** (you cannot do `new AbstractClass()`).
* Can contain **abstract methods** (methods without a body) that subclasses *must* implement.
* Can also contain concrete (fully implemented) methods.



### 5. Interfaces

* **Definition:** An interface is a contract. It defines *what* a class can do, without defining *how* it does it.
* **Key Features:**
* Declared using `interface`.
* All methods are implicitly `public` and `abstract` (before Java 8).
* A class uses `implements` to use an interface.
* **Multiple Inheritance:** A class can extend only one parent class, but it can implement **multiple** interfaces.



---

## Part 2: Practice Questions

### Section A: Multiple Choice Questions (MCQ)

**1. What happens if you try to instantiate an abstract class (e.g., `Shape s = new Shape();`)?**

* A) It creates a generic object.
* B) It throws a runtime exception.
* C) It causes a compiler error.
* D) It is allowed if the class has no abstract methods.

**2. Which annotation should you use to ensure you are correctly redefining a parent class's method?**

* A) `@Overload`
* B) `@Override`
* C) `@Abstract`
* D) `@Virtual`

**3. In Java, a class can inherit from _______ class(es) and implement _______ interface(s).**

* A) one, one
* B) multiple, multiple
* C) one, multiple
* D) multiple, one

### Section B: Code Writing

**Task:**

1. Define an **interface** named `Playable`.
* It should have one method: `void play()`.


2. Create a class `Guitar` that **implements** `Playable`.
3. Inside `Guitar`, implement the `play` method to print "Strumming strings...".

**Write your code below:**

```java
// Write your interface and class here

```

### Section C: Output Prediction

**What is the output of the following polymorphism example?**

```java
class Animal {
    public void makeSound() {
        System.out.println("Some generic sound");
    }
}

class Cat extends Animal {
    @Override
    public void makeSound() {
        System.out.println("Meow");
    }
}

public class TestPoly {
    public static void main(String[] args) {
        Animal myPet = new Cat();
        myPet.makeSound();
    }
}

```

**Predicted Output:**

---

<details>
<summary><strong>📝 Click here to reveal Answers</strong></summary>

### MCQ Answers:

1. **C** (Abstract classes cannot be instantiated).
2. **B** (`@Override` is the correct annotation).
3. **C** (Java supports single class inheritance but multiple interface implementation).

### Code Writing Answer:

```java
interface Playable {
    void play();
}

class Guitar implements Playable {
    @Override
    public void play() {
        System.out.println("Strumming strings...");
    }
}

```

### Output Prediction Answer:

```text
Meow

```

*(Explanation: Virtual Method Invocation ensures that even though `myPet` is declared as an `Animal`, the JVM calls the `Cat` version of the method because the actual object in memory is a `Cat`).*
