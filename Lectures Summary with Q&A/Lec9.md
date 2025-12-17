
# Lecture 09: Advanced Class Design (Final Keyword)


## Part 1: Lecture Summary & Explanation

### 1. The `final` Keyword Overview
The `final` keyword in Java is a non-access modifier used to restrict the user. It represents the concept of "immutability" or "completion" in specific contexts. It can be applied to four main areas:
1.  **Variables** (Constants)
2.  **Parameters** (Read-only arguments)
3.  **Methods** (Cannot be overridden)
4.  **Classes** (Cannot be inherited)

### 2. Final Variables
* **Behavior:** Once a final variable is assigned a value, it cannot be changed (reassigned).
* **Naming Convention:** Static final variables (constants) are usually written in `UPPER_CASE` with underscores (e.g., `STUDENT_ID`, `DEGREE_OF_SUCCESS`).

**Types:**
* **Initialized Final:** Assigned at declaration (e.g., `final int X = 10;`).
* **Blank Final:** A final instance variable that is **not** assigned a value at declaration.
    * **Rule:** You **MUST** initialize blank final variables inside the class constructor. If you don't, the compiler will throw an error saying the variable might not have been initialized.

**Reference Types:**
If a reference variable (like an object or array) is final, you cannot change the reference (address) to point to a new object, but you **can** still modify the internal data (fields) of that object.



### 3. Final Parameters
You can declare method parameters as final.
* **Rule:** The method cannot change the value of the argument passed to it.
* **Example:** If you have `public void test(final int x)`, trying to do `x = 5;` inside the method will cause a compile-time error.

### 4. Final Methods
* **Purpose:** To prevent a method's behavior from being altered by subclasses.
* **Rule:** A final method **cannot be overridden**.
* **Example:** If `Student` has a `final public String toString()`, the subclass `GraduatedStudent` cannot define its own `toString()` method. Attempting to do so results in: *"overridden method is final"*.

### 5. Final Classes
* **Purpose:** To prevent inheritance entirely. This is used when a class is "perfect" or security-sensitive (like the `String` class in Java).
* **Rule:** A final class **cannot be subclassed** (extended).
* **Example:** `final public class Student` means you cannot write `class GraduatedStudent extends Student`. It causes the error: *"cannot inherit from final Student"*.

---

## Part 2: Practice Questions

### Section A: Multiple Choice Questions (MCQ)

**1. Which of the following is TRUE regarding a "blank final" variable?**
- A) It can be left uninitialized if it is static.
- B) It must be initialized in the constructor of the class.
- C) It can be initialized in any method of the class.
- D) It takes a default value (0 or null) if not assigned.

**2. If you declare a class as final (e.g., `public final class MathLib`), what is the consequence?**
- A) All methods in the class are automatically abstract.
- B) You cannot create instances (objects) of the class.
- C) No other class can extend (inherit from) this class.
- D) All variables in the class must be static.

**3. You have a method `void process(final int id)`. What happens if you write `id = 100;` inside this method?**
- A) The value of id changes to 100.
- B) The value changes locally but not outside the method.
- C) A compile-time error occurs.
- D) A runtime exception is thrown.

### Section B: Code Writing

**Task:**
Create a class named `Account`.
1. Declare a blank final variable `ACCOUNT_NUMBER` (int).
2. Declare a static final variable `BANK_NAME` initialized to "Fayoum Bank".
3. Create a constructor that accepts an integer parameter and initializes the `ACCOUNT_NUMBER`.
4. Create a final method `getDetails()` that prints the bank name and account number.

**Write your code below:**
```java
// Write your Account class here

```

### Section C: Output Prediction

**What happens when you try to compile the following code? (Be specific about the error)**

```java
class Parent {
    public final void show() {
        System.out.println("Parent Show");
    }
}

class Child extends Parent {
    // Attempting to modify the behavior
    @Override
    public void show() { 
        System.out.println("Child Show");
    }
}

public class TestFinal {
    public static void main(String[] args) {
        Child c = new Child();
        c.show();
    }
}

```

**Predicted Result:**

---

<details>
<summary><strong>📝 Click here to reveal Answers</strong></summary>

### MCQ Answers:

1. **B** (Blank final variables must be initialized in the constructor).
2. **C** (Final classes cannot be inherited).
3. **C** (Final parameters cannot be assigned a new value).

### Code Writing Answer:

```java
public class Account {
    final int ACCOUNT_NUMBER; // Blank final
    static final String BANK_NAME = "Fayoum Bank"; // Static final constant

    // Constructor initializing the blank final variable
    public Account(int accNum) {
        this.ACCOUNT_NUMBER = accNum;
    }

    // Final method preventing overriding
    public final void getDetails() {
        System.out.println("Bank: " + BANK_NAME);
        System.out.println("Account: " + ACCOUNT_NUMBER);
    }
}

```

### Output Prediction Answer:

**Compilation Error.**

*(Explanation: The method `show()` in the `Parent` class is marked as `final`, so the `Child` class is strictly forbidden from overriding it. The compiler will report: "show() in Child cannot override show() in Parent; overridden method is final".)*
