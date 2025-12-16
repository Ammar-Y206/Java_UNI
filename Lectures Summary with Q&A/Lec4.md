
# Lecture 04: Encapsulation, Subclassing, and Method Overloading


## Part 1: Lecture Summary & Explanation

### 1. Encapsulation Recap & Immutability
* **The Concept:** Encapsulation wraps data (fields) and behavior (methods) into a single unit. It hides internal details by making fields `private` and exposing access via `public` methods.
* **Refining the Model:**
    * **Hide Data:** Change fields like `empId` and `salary` to `private`.
    * **Business Logic:** Instead of generic setters (like `setSalary`), use business-specific methods (like `raiseSalary`) to validate logic.
* **Immutability:** A strong design pattern is to set all values via the **Constructor** and remove setter methods entirely. This makes the object "immutable" (unchangeable after creation), which is safer in complex systems.

### 2. Subclassing (Inheritance)
* **Definition:** Subclassing allows you to define a new class based on an existing one.
    * **Parent:** `Employee` (Superclass).
    * **Child:** `Manager` (Subclass).
* **The `extends` Keyword:** Used to create a subclass.
    * *Example:* `public class Manager extends Employee { ... }`
* **Single Inheritance:** In Java, a class can extend only **one** other class.
* **The `super` Keyword:**
    * Constructors are **not** inherited. You must define them in the subclass.
    * Use `super(args...)` to call the parent's constructor.
    * **Crucial Rule:** This must be the **first statement** in the subclass constructor.



### 3. Polymorphism (Intro)
"Many Forms": An object can take on multiple forms. A Manager is an Employee.

* **Reference vs. Object:**
    * **Legal:** `Employee emp = new Manager();` (A Manager is an Employee).
    * **Compiler Restriction:** If you use an `Employee` reference (`emp`), you can only call methods defined in the **Employee** class. You cannot call `emp.getDeptName()` even if the actual object is a Manager, because the compiler only checks the reference type.

### 4. Method Overloading
* **Definition:** You can have multiple methods with the **same name** in the same class, as long as their **parameter lists differ** (number or type of arguments).
* **Note:** Changing *only* the return type is **not** sufficient for overloading.

### 5. Variable Arguments (Varargs)
* **Problem:** Sometimes you don't know how many arguments a method will receive (e.g., calculating the average of 2 numbers, or 5, or 100).
* **Solution:** Use the `...` syntax (e.g., `int... nums`).
* **Behavior:** Java treats this parameter as an **array** inside the method.
* **Rule:** The varargs parameter must be the **last parameter** in the list.

---

## Part 2: Practice Questions

### Section A: Multiple Choice Questions (MCQ)

**1. Which keyword is used in a subclass constructor to invoke the constructor of the parent class?**
- A) this
- B) parent
- C) super
- D) extends

**2. Which of the following statements about Variable Arguments (Varargs) is TRUE?**
- A) You can have multiple varargs parameters in a single method.
- B) The varargs parameter must be the first parameter in the method signature.
- C) Inside the method, the varargs parameter is treated as an array.
- D) You define them using three underscores `___`.

**3. Given the classes `Person` and `Student extends Person`, which line of code causes a compiler error?**
*(Assume `Student` has a method `getGrade()` that `Person` does not have).*
- A) `Person p = new Student();`
- B) `Person p = new Person();`
- C) `Student s = new Student(); s.getGrade();`
- D) `Person p = new Student(); p.getGrade();`

### Section B: Code Writing

**Task:**
Create a class `Calculator`.
1. Write a method `add` that uses **Varargs** to accept any number of integers.
2. Inside the method, sum all the numbers and return the result.

**Write your code below:**
```java
// Write your Calculator class here

```

### Section C: Output Prediction

**What is the output of the following code?**

```java
public class TestOverload {
    public void print(int x) {
        System.out.println("Integer: " + x);
    }

    public void print(String s) {
        System.out.println("String: " + s);
    }

    public static void main(String[] args) {
        TestOverload t = new TestOverload();
        t.print(10);
        t.print("10");
    }
}

```

**Predicted Output:**

---

<details>
<summary><strong>📝 Click here to reveal Answers</strong></summary>

### MCQ Answers:

1. **C** (`super` calls the parent constructor).
2. **C** (Java treats `int... nums` as `int[] nums`).
3. **D** (The reference type `Person` does not know about the method `getGrade()`, even though the object is a `Student`).

### Code Writing Answer:

```java
public class Calculator {
    public int add(int... numbers) {
        int sum = 0;
        for (int num : numbers) {
            sum += num;
        }
        return sum;
    }
}

```

### Output Prediction Answer:

```text
Integer: 10
String: 10

```

*(Explanation: The compiler selects the correct `print` method based on the argument type passed—`int` vs `String`).*
