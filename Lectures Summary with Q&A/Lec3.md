
# Lecture 03: Java Syntax, Memory, and Encapsulation

Here is the summary and practice set for **Lecture 03**.

## Part 1: Lecture Summary & Explanation

### 1. Class Mechanics & Organization

* **Packages & Imports:**
    * **Packages** act like folders to group related classes and avoid name conflicts.
    * **Imports** (e.g., `import java.util.Date;`) allow you to use classes from other packages without typing their full name every time.
    * *Note:* You don't need to import classes from the same package or from `java.lang`.

* **Constructors:**
    * Special methods used to initialize objects.
    * They share the **class name** and have **no return type**.
    * You can have a "no-arg" constructor or one with parameters to set initial values.

### 2. Memory Management: Pass-By-Value
*This is a critical technical concept in Java.*

**Java is always Pass-By-Value:**

1.  **Primitives:** When you pass an `int x` to a method, Java copies the **actual value**. If the method changes the value, the original `x` remains unchanged.
2.  **Objects:** When you pass an object (like `Employee e`), Java copies the **memory address (reference)**.
    * Because both the original variable and the method parameter point to the same address, modifying the object inside the method (e.g., `e.setName(...)`) **will affect** the original object.
    * *Exception:* If you reassign the reference entirely inside the method (`e = new Employee()`), the original variable is **not** affected.



### 3. Under the Hood: Compilation & Garbage Collection

* **Compilation:** You use `javac` to compile `.java` files into `.class` files. You use `java` to run them.
* **Class Loader:** The JVM loads classes into memory dynamically only when they are first used.
* **Garbage Collection:** You don't need to manually free memory. When an object is no longer reachable (referenced) by any code, the **Garbage Collector** automatically clears it to free up space.

### 4. Encapsulation (OOP Principle)
Encapsulation is about wrapping data and methods together and hiding the internal details.

* **The Problem:** If fields are `public`, any code can change them to invalid values (e.g., setting a salary to -500).
* **The Solution:**
    1.  Mark fields as `private`.
    2.  Provide `public` methods (Getters and Setters) to access them.



> **Best Practice:** Do not just blindly create setters. Create meaningful business methods. Instead of `setSalary()`, use `raiseSalary()` which contains logic to ensure the raise is valid.

---

## Part 2: Practice Questions

### Section A: Multiple Choice Questions (MCQ)

**1. If you declare a class field as private, which parts of the program can access it directly?**
- A) Any class in the same package.
- B) Any class in the entire project.
- C) Only methods within the class itself.
- D) Only subclasses.

**2. Consider the following scenario: You pass an object `myObj` to a method. Inside the method, you call `myObj.setValue(10)`. What happens to the original object outside the method?**
- A) It remains unchanged because Java is pass-by-value.
- B) It is updated to have the new value because Java copies the reference to the object.
- C) The compiler throws an error.
- D) A copy of the object is created, so the original is safe.

**3. Which Java component is responsible for freeing memory used by objects that are no longer reachable?**
- A) The ClassLoader
- B) The Compiler (javac)
- C) The Garbage Collector
- D) The import statement

### Section B: Code Writing

**Task:**
Create a class called `SmartPhone` that demonstrates Encapsulation.
1. Define a private field: `batteryLevel` (int).
2. Create a public constructor that initializes the battery to 100.
3. Create a public method `usePhone(int amount)` that decreases the battery level.
4. **Logic Check:** The battery cannot go below 0. If `amount` is greater than the current level, set it to 0.

**Write your code below:**
```java
// Write your SmartPhone class here

```

### Section C: Output Prediction

**What will be the output of the following code? (Focus on the Pass-By-Value concept)**

```java
public class ReferenceTest {
    public static void main(String[] args) {
        int num = 10;
        int[] arr = {10, 20, 30};

        modifyValues(num, arr);

        System.out.println("Num: " + num);
        System.out.println("Arr[0]: " + arr[0]);
    }

    public static void modifyValues(int x, int[] y) {
        x = 50;          // Modifying the primitive parameter
        y[0] = 50;       // Modifying the object (array) content
        y = new int[3];  // Reassigning the reference
        y[0] = 100;      // Modifying the new object
    }
}

```

**Predicted Output:**

---

<details>
<summary><strong>📝 Click here to reveal Answers</strong></summary>

### MCQ Answers:

1. **C** (private restricts access to the defining class only).
2. **B** (The reference is copied, so both variables point to the same object in memory).
3. **C** (Garbage Collector handles memory cleanup).

### Code Writing Answer:

```java
public class SmartPhone {
    private int batteryLevel;

    public SmartPhone() {
        this.batteryLevel = 100;
    }

    public void usePhone(int amount) {
        if (amount > batteryLevel) {
            batteryLevel = 0;
        } else {
            batteryLevel -= amount;
        }
    }
}

```

### Output Prediction Answer:

```text
Num: 10
Arr[0]: 50

```

*(Explanation: `num` is a primitive, so the change to `x` inside the method does not affect `num`. `arr` is an object, so `y[0] = 50` updates the actual array in memory. However, `y = new int[3]` breaks the link to the original array, so the subsequent `y[0] = 100` only affects the new local array, not the original `arr`.)*

</details>

```

