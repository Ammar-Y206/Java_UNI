
# Lecture 06: Advanced Class Design (Abstraction)


## Part 1: Lecture Summary & Explanation

### 1. Abstraction
* **Definition:** Abstraction is the process of hiding the internal implementation details (the "how") and showing only the functionality (the "what") to the user.
* **Purpose:** It improves security (by hiding data) and allows for code reuse and easier maintenance through generalization.



* **Ways to Achieve Abstraction:**
    * **Abstract Classes** (0 to 100% abstraction).
    * **Interfaces** (Fully abstract).

### 2. Abstract Classes
* **Definition:** A class declared with the `abstract` keyword. It represents a generic concept (e.g., `ElectronicDevice` or `BankAccount`) that shouldn't be instantiated directly.
* **Key Characteristics:**
    * It is a non-access modifier.
    * It **cannot** be instantiated (you cannot say `new AbstractClass()`).
    * It can contain both **abstract methods** (no body) and **non-abstract methods** (methods with a body).

### 3. Abstract Methods
* **Syntax:** Defined using the `abstract` keyword and ending with a semicolon `;` instead of curly braces `{}`.
    * *Example:* `public abstract void turnOn();`
* **Rules:**
    * They have **no method body** (implementation).
    * They must be declared inside an **abstract class**.
    * They must be **overridden (implemented)** by the first "concrete" subclass.

### 4. Concrete Classes
* **Definition:** A standard class where all methods have a full implementation (body). This is the opposite of an abstract class.
* **Generalization:** You should generally write code that depends on the **abstract base type** (e.g., `ElectronicDevice`) rather than the specific concrete type (e.g., `Television`). This allows you to add new devices later without breaking existing code.



---

## Part 2: Practice Questions

### Section A: Multiple Choice Questions (MCQ)

**1. Which of the following statements about abstract classes is TRUE?**
- A) An abstract class must contain at least one abstract method.
- B) An abstract class cannot be instantiated using the new keyword.
- C) An abstract class cannot contain any non-abstract (concrete) methods.
- D) You cannot have a constructor in an abstract class.

**2. Which syntax correctly defines an abstract method?**
- A) `public abstract void start() {}`
- B) `public void abstract start();`
- C) `public abstract void start();`
- D) `public virtual void start() { return; }`

**3. If a concrete class inherits from an abstract class, what MUST it do?**
- A) It must declare itself as abstract.
- B) It must override and provide a body for all inherited abstract methods.
- C) It must implement an interface.
- D) It must not have any fields.

### Section B: Code Writing

**Task:**
1. Create an abstract class named `Shape`.
    * Add an abstract method `calculateArea()` that returns a `double`.
    * Add a concrete method `printType()` that prints "I am a generic shape".
2. Create a concrete subclass named `Circle` that extends `Shape`.
    * It should have a `radius` field.
    * Implement `calculateArea()` to return the area (Assume pi = 3.14).

**Write your code below:**
```java
// Write your Shape and Circle classes here

```

### Section C: Output Prediction

**What is the output of the following code?**

```java
abstract class Vehicle {
    abstract void start();
    
    void stop() {
        System.out.println("Vehicle stopped.");
    }
}

class Car extends Vehicle {
    @Override
    void start() {
        System.out.println("Car starting...");
    }
}

public class TestAbstraction {
    public static void main(String[] args) {
        Vehicle v = new Car();
        v.start();
        v.stop();
    }
}

```

**Predicted Output:**

---

<details>
<summary><strong>📝 Click here to reveal Answers</strong></summary>

### MCQ Answers:

1. **B** (Abstract classes cannot be instantiated).
2. **C** (Abstract methods have no body and end with a semicolon).
3. **B** (A concrete subclass must implement the "contract" defined by the abstract parent).

### Code Writing Answer:

```java
abstract class Shape {
    public abstract double calculateArea();

    public void printType() {
        System.out.println("I am a generic shape");
    }
}

class Circle extends Shape {
    double radius;

    public Circle(double r) {
        this.radius = r;
    }

    @Override
    public double calculateArea() {
        return 3.14 * radius * radius;
    }
}

```

### Output Prediction Answer:

```text
Car starting...
Vehicle stopped.

```

*(Explanation: The `start` method is overridden in `Car`, so that version runs. The `stop` method is inherited directly from `Vehicle`, so the generic version runs.)*
