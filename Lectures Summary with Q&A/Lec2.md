
# Lecture 02: Java Syntax and Class Review


## Part 1: Lecture Summary & Explanation

### 1. Class Structure & Naming Conventions
**Structure:** A Java program is made up of classes. A basic class structure includes:
```java
package com.example;      // Optional, for organization
import java.util.*;       // To use other classes

public class ClassName {  // Class Definition
    // Members: Fields, Constructors, and Methods
}

```

**Naming Rules:**

* **Classes:** UpperCamelCase (Noun) → `CreditCard`
* **Methods:** lowerCamelCase (Verb) → `getCharges()`
* **Variables:** lowerCamelCase → `creditCardNumber`
* **Constants:** ALL_CAPS → `MAX_VALUE`

### 2. Data Types & Literals

Java has two main categories of data:

#### A. Primitive Types (8 total)

*Stores the actual value.*

* **Integer:** `byte`, `short`, `int`, `long` (use 'L' suffix).
* **Floating Point:** `float` (use 'F' suffix), `double`.
* **Character:** `char` (stores single characters like 'a').
* **Logical:** `boolean` (true/false).

#### B. Reference Types

*Stores the address (reference) to an object in memory.*

* Examples: Arrays, Strings, Classes.

#### C. Java 7+ Features

* **Underscores in numbers:** You can write `1_000_000` for readability.
* **Binary Literals:** You can write binary using `0b` prefix (e.g., `0b101` is 5).

### 3. Operators

* **Arithmetic:** `+`, `-`, `*`, `/`, `%` (remainder).
* **Unary:** `++` (increment), `--` (decrement).
* *Note:* Position matters (`i++` uses then increments; `++i` increments then uses).


* **Relational:** `==`, `!=`, `>`, `<`, etc.
* **Ternary Operator:** A shorthand for `if-else`.
```java
result = (condition) ? valueIfTrue : valueIfFalse;

```



### 4. Strings (Special Object)

* **Immutability:** Once a String is created, it cannot be changed.
* **String Pool vs. Heap:**
* `String s = "Hello";` → Stored in the **String Pool** (saves memory by reusing identical strings).
* `String s = new String("Hello");` → Forces a new object in the **Heap**, even if "Hello" exists.


* **Concatenation:** Can be done using `+` or `.concat()`.

### 5. Control Flow

* **Conditionals:** `if`, `if-else`.
* **Switch Statement:** Since Java 7, you can use **Strings** in a switch statement (e.g., `case "Red":`).
* **Loops:**
* `for`: Standard counting loop.
* `while`: Loops while a condition is true.
* `do-while`: Executes at least once, then checks condition.
* `for-each`: Simplified loop for arrays/collections.
```java
for(String s : names) { ... }

```





### 6. Arrays

Arrays are homogeneous (all elements must be the same type) and have a fixed size.

* **Declaration:**
```java
int[] numbers = new int[5];
// or
int[] numbers = {10, 20, 30};

```


* **Memory:** The array variable is in the **Stack**, pointing to the array elements in the **Heap**.

---

## Part 2: Practice Questions

### Section A: Multiple Choice Questions (MCQ)

**1. Which of the following is a valid way to write the number one million in Java (version 7+)?**

* A) 1,000,000
* B) 1000000
* C) 1_000_000
* D) Both B and C

**2. What happens when you create a String using the literal method: `String s = "Java";`?**

* A) It always creates a new object in the Heap.
* B) It checks the String Pool; if "Java" exists, it reuses the reference.
* C) It throws a compilation error because you must use new.
* D) It creates a mutable string.

**3. Which loop is guaranteed to execute at least one time?**

* A) for loop
* B) while loop
* C) do-while loop
* D) for-each loop

### Section B: Code Writing

**Task:**
Write a Java method named `printEvenNumbers`.

1. It should accept an array of integers as a parameter.
2. Use a **for-each** loop to iterate through the array.
3. Inside the loop, check if the number is even.
4. If it is even, print it.

**Write your code below:**

```java
// Write your method here

```

### Section C: Output Prediction

**What is the output of the following code block?**

```java
public class Test {
    public static void main(String[] args) {
        int x = 5;
        int y = 10;
        
        // Ternary operator check
        int result = (x > y) ? 100 : 200;
        System.out.println("Result: " + result);

        // String concatenation
        String s1 = "1";
        String s2 = "2";
        System.out.println(s1 + s2);
        
        // Arithmetic addition
        System.out.println(x + y);
    }
}

```

**Predicted Output:**

---

<details>
<summary><strong>📝 Click here to reveal Answers</strong></summary>

### MCQ Answers:

1. **D** (Both standard notation and underscores are valid).
2. **B** (Literals use the String Pool to save memory).
3. **C** (Do-while checks the condition after the code block runs).

### Code Writing Answer:

```java
public void printEvenNumbers(int[] numbers) {
    for (int num : numbers) {
        if (num % 2 == 0) {
            System.out.println(num);
        }
    }
}

```

### Output Prediction Answer:

```text
Result: 200
12
15

```

*(Explanation: `x > y` is false, so it picks 200. Strings "1" and "2" concatenate to "12". Integers 5 and 10 add up to 15).*

</details>

```

