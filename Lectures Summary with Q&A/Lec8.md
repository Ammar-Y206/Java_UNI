
# Lecture 08: Advanced Class Design (Static Keyword)
```
note: this Lecture is named Lec8 as the Prof sent it but it is number 7.
```
## Part 1: Lecture Summary & Explanation

### 1. The `static` Keyword
The `static` modifier is used to create **class-level resources** rather than object-level resources.
* **Key Characteristic:** Static members belong to the class itself, not to any specific instance (object) of that class.
* **Usage:** They are used when data needs to be shared among all objects of the same type, or when a utility function doesn't require an object state.

### 2. Static Variables (Class Variables)
* **Shared Memory:** Unlike instance variables (where every object has its own copy), there is **only one single copy** of a static variable in memory per JVM. All objects share this same variable.
* **Initialization:** They are initialized when the class is first loaded into memory.
* **Access:** You can access them using the class name (e.g., `Student.college`) without creating an object.



**Example from Lecture:**
* **Shared Constant:** `static String college = "IT";` → Every student belongs to the "IT" college, so it's efficient to store this once.
* **Counter:** `static int count = 1;` → This is used to auto-generate unique IDs (1, 2, 3...) for each new `Student` object created.

### 3. Static Methods
* **Utility Functions:** Methods that can be called without instantiating the class (e.g., `Math.pow()` or `Student.validatePassword()`).
* **The `main` Method:** The entry point of a Java program (`public static void main`) must be static so the JVM can run it without creating an object of the Main class.

### 4. Restrictions on Static Methods
*This is a common source of errors for beginners.*

* **No Access to Instance Data:** A static method **cannot** directly access non-static (instance) variables or methods.
    * *Why?* Because a static method runs in the context of the class, it doesn't know *which* object's name or ID you are talking about.
* **No `this` or `super`:** You cannot use the `this` keyword inside a static context.
* **Workaround:** To access instance variables inside a static method (like `main`), you must first create an object instance:
    ```java
    Main m = new Main();
    m.x = 10;
    ```

---

## Part 2: Practice Questions

### Section A: Multiple Choice Questions (MCQ)

**1. Which of the following statements about static variables is TRUE?**
- A) Each object has its own unique copy of the static variable.
- B) Static variables are initialized every time a new object is created.
- C) There is only one copy of the variable shared by all instances of the class.
- D) Static variables can only be accessed from inside the main method.

**2. Why does the compiler throw an error if you try to use the keyword `this` inside a static method?**
- A) Because `this` is a reserved word for constructors only.
- B) Because static methods belong to the class and do not have a reference to a specific current object instance.
- C) Because static methods are private by default.
- D) Because `this` can only be used for integer variables.

**3. If you have a class `Student` with a static field `college = "Engineering"`, what happens if you change `Student.college` to `"Science"`?**
- A) Only the next created Student object will have "Science".
- B) All existing and future Student objects will see the change to "Science".
- C) The compiler throws an error because static fields are always final.
- D) Only the object that made the change sees "Science".

### Section B: Code Writing

**Task:**
Create a class `Product`.
1. Define a **static** integer variable `productCount` initialized to 0.
2. Define an **instance** string variable `productName`.
3. Create a constructor that accepts a name. Inside the constructor:
    * Set `this.productName`.
    * Increment `productCount` by 1.
4. Create a **static method** `displayCount()` that prints the total number of products created.

**Write your code below:**
```java
// Write your Product class here

```

### Section C: Output Prediction

**What is the output of the following code based on the logic presented in the lecture slides?**

```java
class Student {
    static int count = 0;
    int id;
    
    public Student() {
        count++;
        this.id = count;
    }
}

public class TestStatic {
    public static void main(String[] args) {
        Student s1 = new Student();
        Student s2 = new Student();
        Student s3 = new Student();
        
        System.out.println("s1 ID: " + s1.id);
        System.out.println("s3 ID: " + s3.id);
        System.out.println("Total Students: " + Student.count);
    }
}

```

**Predicted Output:**

---

<details>
<summary><strong>📝 Click here to reveal Answers</strong></summary>

### MCQ Answers:

1. **C** (Limited to a single copy per JVM).
2. **B** (`this` cannot be used in static context).
3. **B** (All object instances share a single copy).

### Code Writing Answer:

```java
public class Product {
    static int productCount = 0;
    String productName;

    public Product(String name) {
        this.productName = name;
        productCount++;
    }

    public static void displayCount() {
        System.out.println("Total Products: " + productCount);
    }
}

```

### Output Prediction Answer:

```text
s1 ID: 1
s3 ID: 3
Total Students: 3

```

*(Explanation: `count` is static, so it accumulates across all 3 objects. `id` is an instance variable, so it captures the value of count at the specific moment the object was created).*

