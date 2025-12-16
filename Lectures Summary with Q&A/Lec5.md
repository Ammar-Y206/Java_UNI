
# Lecture 05: Java Class Design


## Part 1: Comprehensive Lecture Summary & Explanation

### 1. Access Control (Encapsulation)
Java uses access modifiers to protect data and hide implementation details. There are four levels of access, determined by keywords.

* **`private`**: Visible **only within the same class**. This is the strictest level and is used for sensitive data.
* **Default (no keyword)**: Visible to any class in the **same package**. If you don't write a keyword, this is what you get.
* **`protected`**: Visible to classes in the **same package** AND **subclasses in other packages**. This is crucial for inheritance.
* **`public`**: Visible to **everyone** (the entire universe).



**Table of Visibility:**

| Modifier | Same Class | Same Package | Subclass (Diff Pkg) | Universe |
| :--- | :---: | :---: | :---: | :---: |
| **private** | ✅ | ❌ | ❌ | ❌ |
| **default** | ✅ | ✅ | ❌ | ❌ |
| **protected**| ✅ | ✅ | ✅ | ❌ |
| **public** | ✅ | ✅ | ✅ | ✅ |

### 2. Method Overriding
* **Definition:** A subclass provides a specific implementation for a method already defined in its parent class.
* **Rules:** The method signature (name, argument list, and return type) must be identical to the parent's.
* **`@Override` Annotation:** It is best practice to put `@Override` above the method. This helps the compiler catch errors (like if you misspelled the method name).

### 3. Polymorphism & Virtual Method Invocation
* **Virtual Method Invocation:** When you call a method on an object, Java determines which version to run based on the **actual object type** in memory at runtime, not the variable type.
* **Example:**
  ```java
  Employee e = new Manager();
  e.getSalary(); // Runs the Manager's version


### 4. Object Casting & Type Safety

* **Upward Casting (Implicit):** Converting a subclass to a superclass (e.g., `Employee e = new Manager();`). This is automatic.
* **Downward Casting (Explicit):** Converting a generic reference back to a specific subclass (e.g., `Manager m = (Manager) e;`). This is risky because the object might not actually be a Manager.
* **`instanceof` Operator:** Used to strictly check an object's type before casting to avoid runtime errors (`ClassCastException`).

```java
if (e instanceof Manager) {
    Manager m = (Manager) e; // Safe cast
}

```

### 5. The `Object` Class

Every class in Java inherits from `java.lang.Object`. You often override these methods to make your classes useful:

* **`toString()`:** Returns a string representation of the object. Default is memory address; override it to return meaningful data like "ID: 101, Name: Bob".
* **`equals(Object o)`:** Checks equality. Default uses `==` (memory address check). Override it to compare actual data (like IDs).
* **`hashCode()`:** Returns a unique integer for the object. If you override `equals`, you must override `hashCode` so that equal objects have the same hash code.

---

## Part 2: Practice Questions

### Section A: Multiple Choice Questions (MCQ)

**1. Which access modifier allows a method to be accessed by subclasses in a different package, but NOT by unrelated classes in that different package?**

* A) `public`
* B) `private`
* C) `protected`
* D) Default (Package-Private)

**2. What is the specific purpose of the `instanceof` operator?**

* A) To create a new instance of a class.
* B) To check if an object is of a specific type to safely perform a cast.
* C) To call the parent class's constructor.
* D) To override a method from the Object class.

**3. If you override the `equals()` method in a class, which other method from the `Object` class must you also override to maintain the contract?**

* A) `toString()`
* B) `clone()`
* C) `hashCode()`
* D) `finalize()`

### Section B: Code Writing

**Task:**

1. Create a class `Person` with a **protected** string field `name`.
2. Create a subclass `Student` that extends `Person`.
3. Inside `Student`, override the `toString()` method.
4. The `toString()` implementation should return "Student Name: " followed by the value of the inherited `name` field.

**Write your code below:**

```java
// Write your classes here

```

### Section C: Output Prediction

**What is the output of the following polymorphism code?**

```java
class Device {
    public void turnOn() {
        System.out.println("Device is starting...");
    }
}

class Phone extends Device {
    @Override
    public void turnOn() {
        System.out.println("Phone is booting up...");
    }
}

public class TestCast {
    public static void main(String[] args) {
        Device myDev = new Phone(); // Upward cast
        
        // Virtual Method Invocation
        myDev.turnOn();
        
        // Instanceof check
        if (myDev instanceof Phone) {
            System.out.println("It is a phone!");
        }
    }
}

```

**Predicted Output:**

---

<details>
<summary><strong>📝 Click here to reveal Answers</strong></summary>

### MCQ Answers:

1. **C** (`protected` gives access to subclasses regardless of package).
2. **B** (`instanceof` is for type checking before casting).
3. **C** (`hashCode()` must be consistent with `equals()`).

### Code Writing Answer:

```java
class Person {
    protected String name = "Unknown";
}

class Student extends Person {
    @Override
    public String toString() {
        return "Student Name: " + this.name;
    }
}

```

### Output Prediction Answer:

```text
Phone is booting up...
It is a phone!

```

*(Explanation: The `turnOn` method runs the `Phone` version because the actual object is a `Phone`. The `instanceof` check is true, so the print statement executes.)*


