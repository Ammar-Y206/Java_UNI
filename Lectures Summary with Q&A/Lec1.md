

# Lecture 01: Programming Techniques (Java)

Here is a summary and explanation of **Lecture 01**, followed by practice questions to test your understanding.

## Part 1: Lecture Summary & Explanation

### 1. Introduction to Programming & Binary
The lecture begins by defining computer language at the hardware level. Computers operate on **DC voltages**:

* **High Voltage (+5V to +15V):** Represents a **1**.
* **Low Voltage (0V to -5V):** Represents a **0**.
* This creates the **Binary System**, where instructions are sequences of 0s and 1s.

### 2. Java History & Characteristics
Java was created by **Sun Microsystems** in 1995 (led by James Gosling) and later acquired by **Oracle** in 2010. It is a versatile language used for desktop, web, enterprise, and mobile applications.

**Key Features of Java:**
* **Simple & Familiar:** It uses syntax similar to C++.
* **Object-Oriented:** It is fully object-oriented.
* **Platform Independent:** It creates software that runs on any operating system (Windows, Linux, Solaris) without recompiling.
* **Networked & Multithreaded:** Built to handle multiple tasks at once and communicate over networks (Sockets, RMI).

### 3. How Java Works (The Ecosystem)
This is a critical concept regarding how Java code is executed.

* **Hybrid Approach:** Java is both **Compiled** and **Interpreted**.

1. **Source Code (`.java`):** You write this.
2. **Compiler:** Translates source code into **Bytecode (`.class`)**.
3. **Interpreter (JVM):** The Java Virtual Machine reads the Bytecode and executes it natively on the specific computer.

#### The "Kit" Hierarchy:
* **JVM (Java Virtual Machine):** The engine that runs the code.
* **JRE (Java Runtime Environment):** JVM + Libraries (Libs).
* **JDK (Java Development Kit):** JRE + Compiler + Utilities. (This is what you need to install to *write* code).

### 4. Memory Management: Stack vs. Heap
The lecture introduces how Java manages memory:

| Memory Type | Description |
| :--- | :--- |
| **Stack Memory** | Stores variable **names** and references. It points to the data. |
| **Heap Memory** | Stores the actual **data values** or objects. |

> **Example:** If you have a variable `name = "Ahmed"`, "name" sits in the Stack, pointing to "Ahmed" which sits in the Heap.

> **Note:** You can adjust Heap size using flags like `-Xms512m` to prevent memory errors.

### 5. Program Structure

* **Method Signature:** A method is a block of code with a specific structure:
  `Access Modifier` + `Return Type` + `Name` + `(Parameters)`
  * *Example:* `public int add(int x, int y)`

* **The Main Method:** The entry point of any Java application.
  ```java
  public static void main(String[] args)



* **public:** Accessible from everywhere.
* **static:** Can be called without creating an object.
* **void:** Returns nothing.
* **Packages & JARs:** Classes are organized into **Packages** (folders). These can be compressed into a **JAR (Java Archive)** file for distribution.

### 6. Java Applets

Applets are client-side programs that run *inside* a web browser.

* **Security:** Because they run on a user's machine, they are heavily restricted. They cannot access the hard drive or communicate with untrusted servers.

---

## Part 2: Practice Questions

### Section A: Multiple Choice Questions (MCQ)

**1. Which component is responsible for translating Java Bytecode (`.class`) into native machine code?**

* A) Java Compiler
* B) Java Virtual Machine (JVM)
* C) Java Development Kit (JDK)
* D) NetBeans

**2. In Java memory management, where are the actual data values (the objects themselves) stored?**

* A) The Stack
* B) The Heap
* C) The JAR file
* D) The HDD

**3. Which of the following is required if you want to WRITE and COMPILE Java programs?**

* A) JRE only
* B) JVM only
* C) JDK
* D) Internet Explorer

### Section B: Code Writing

**Task:**
Based on the method signature rules explained in the lecture (Slide 13), write a simple Java method named `calculateArea`.

* It should be accessible from anywhere (`public`).
* It should return a whole number (`int`).
* It should accept two parameters: `width` (int) and `height` (int).
* Inside the method, return the product of the two parameters.

**Write your code below:**

```java
// Write your method here

```

### Section C: Output Prediction

**Consider the following standard Java "Hello World" structure provided in the lecture (Slide 22). What will be the output of this code?**

```java
public class TestApp {
    public static void main(String args[]) {
        System.out.println("Java is");
        System.out.print("Compiled and ");
        System.out.println("Interpreted");
    }
}

```

**Predicted Output:**
*(Note: Pay attention to `println` vs `print`)*

---

<details>
<summary><strong>📝 Click here to reveal Answers</strong></summary>

### MCQ Answers:

1. **B** (The JVM interprets bytecode)
2. **B** (Heap holds actual data values)
3. **C** (JDK contains the compiler)

### Code Writing Answer:

```java
public int calculateArea(int width, int height) {
    return width * height;
}

```

### Output Prediction Answer:

```text
Java is
Compiled and Interpreted

```

*(Explanation: `println` moves to a new line after printing. `print` keeps the cursor on the same line. So "Compiled and " and "Interpreted" appear on the same line.)*

</details>

```

```
