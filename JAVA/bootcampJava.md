# ☕ Java Pro Bootcamp: 5-Week Intensive Track

**Target Audience:** CS Grads / Developers with prior experience.
**Goal:** Production-ready Java skills, including concurrency, data structures, and build tools.

## 📚 Reference Material
* **Lectures:** [Udemy: Java Programming Tutorial](https://www.udemy.com/course/java-programming-tutorial-for-beginners/)
* **Practice:** [DataCamp: Java Skill Track](https://app.datacamp.com/learn/skill-tracks?topics=35)
* **Deep Dive:** [Packt: Java Programming](https://subscription.packtpub.com/video/programming/9781788994576/p1)

---

## 🗓️ Week 1: The Deep Dive (Syntax & Memory)
*Goal: Move beyond "it works" to "how it works in memory."*

### Day 1: The JVM, Primitives & Wrappers
**Concepts:** JVM vs JRE vs JDK, Bytecode, Primitives vs Wrapper Classes (Autoboxing/Unboxing), String Pool vs Heap.
* **Intense Exercises:**
    1.  **Memory Test:** Write code that demonstrates `String s1 = "Hello"; String s2 = "Hello";` are the same reference, but `String s3 = new String("Hello");` is different. Print their identity hash codes.
    2.  **Overflow:** Write a loop that continuously adds `1` to a `byte` variable. Print the value at every step to observe and explain the overflow wrapping behavior.

### Day 2: Control Flow & Algorithmic Logic
**Concepts:** `switch` expressions (modern Java), ternary operators, `break/continue` with labels.
* **Intense Exercises:**
    1.  **Diamond Printer:** Write a program that takes an odd integer `n` (e.g., 7) and prints a perfect diamond shape of asterisks of width `n` using nested loops.
    2.  **Prime Sieve:** Implement the "Sieve of Eratosthenes" to find all prime numbers up to 1000. Do not use a brute-force nested loop check.

### Day 3: Arrays & Multi-Dimensional Logic
**Concepts:** Jagged arrays, Array copying (`System.arraycopy` vs `.clone()`), Varargs.
* **Intense Exercises:**
    1.  **Matrix Multiplication:** Create two 3x3 integer matrices. Write a function to multiply them. (Must handle the row/column logic correctly).
    2.  **Spiral Traversal:** Write a program that accepts a size `N` and fills an `NxN` 2D array with numbers 1 to `N*N` in a spiral pattern (clockwise from top-left).

### Day 4: Deep Dive into Methods & Recursion
**Concepts:** Stack Overflow, Pass-by-Value (references), Recursive thinking.
* **Intense Exercises:**
    1.  **Recursive Palindrome:** Write a recursive method `boolean isPalindrome(String s)` that checks a string without using loops.
    2.  **Custom Fibonacci:** Write a recursive function to find the Nth Fibonacci number, but optimize it using **Memoization** (store previously calculated values in a static array/map to speed it up).

### Day 5: Strings & Regular Expressions (Regex)
**Concepts:** `StringBuilder` (Mutable) vs `String` (Immutable), Regex Pattern Matching.
* **Intense Exercises:**
    1.  **Email Validator:** Write a regex pattern that validates strictly formatted email addresses (must contain @, domain, extension). Test it against a list of 10 valid and 10 invalid emails.
    2.  **Text Scrubber:** Take a chaotic string ` "H3ll0 W0rld! Th1s is J4v4." `. Use Regex to replace all numbers with `*` and remove all punctuation.

---

### ☠️ Week 1 Friday Challenge: "The Cryptographer"
**Goal:** Bitwise manipulation and logic.
* **Task:** Create a class `Enigma`.
* **Requirements:**
    1.  Implement `encrypt(String message, int key)`: Shift every character's ASCII value by the key.
    2.  Implement `decrypt(String cipher, int key)`: Reverse the process.
    3.  **Hard Mode:** Instead of basic addition, use the **XOR (`^`) operator** for encryption/decryption.
    4.  Write a main method that proves `decrypt(encrypt(msg, key), key)` returns the original message.

---

## 🗓️ Week 2: OOP & Architectural Thinking


### Day 6: Classes, Statics & The "Singleton" Pattern
**Concepts:** `static` context, Instance control, Singleton Design Pattern.
* **Intense Exercises:**
    1.  **Singleton Config:** Create a class `AppConfig` that *cannot* be instantiated with `new`. It must provide a `getInstance()` static method that returns the *same* object every time.
    2.  **Object Counter:** Create a class where every time an instance is created, a static counter increments. Print the count from the main method without referencing any specific instance.

### Day 7: Inheritance & Polymorphism (The Right Way)
**Concepts:** `super`, Method Overriding, Covariant Return Types, `final` classes/methods.
* **Intense Exercises:**
    1.  **Shape Factory:** Create a parent `Shape` and children `Circle`, `Square`. Use an array `Shape[]` to hold mixed objects. Loop through and calculate the total area of all shapes without checking `instanceof`.
    2.  **Immutable Class:** Create a strictly immutable class `Employee` (all fields `final` and `private`, no setters, constructor sets all data).

### Day 8: Interfaces vs Abstract Classes
**Concepts:** Interface Default Methods (Java 8), Functional Interfaces, Multiple Inheritance issues.
* **Intense Exercises:**
    1.  **Plug-in System:** Define an interface `Plugin` with `execute()`. Create a class `CoreSystem` that accepts an array of `Plugin` objects. Create anonymous inner classes implementing `Plugin` and run them.
    2.  **Multiple Interfaces:** Create a class `SmartPhone` that implements `Camera`, `MusicPlayer`, and `Phone`. Resolve any method name conflicts if the interfaces have methods with the same name.

### Day 9: Composition over Inheritance
**Concepts:** "Has-a" vs "Is-a" relationships, Dependency Injection basics.
* **Intense Exercises:**
    1.  **PC Builder:** Create a `Computer` class. Instead of extending `Processor`, the `Computer` should *have* a `Processor`, *have* a `Ram`, and *have* a `Storage`.
    2.  **Swap Parts:** Write a method in `Computer` to upgrade the RAM (replace the `Ram` object with a new one with higher capacity).

### Day 10: Enums & Complex State
**Concepts:** Enums with fields, constructors, and abstract methods.
* **Intense Exercises:**
    1.  **Advanced Enum:** Create an enum `Operation` { ADD, SUBTRACT, MULTIPLY }. Add an abstract method `double apply(double x, double y)` to the enum. Implement the logic *inside* each constant.
    2.  **State Machine:** Use an Enum to represent the state of an Order (NEW, PROCESSING, SHIPPED, DELIVERED). Write logic that prevents invalid transitions (e.g., cannot go from NEW directly to DELIVERED).

---

### ☠️ Week 2 Friday Challenge: "The RPG Battle System"
**Goal:** heavy OOP usage, Polymorphism, and State management.
* **Task:** Build a text-based battle arena.
* **Requirements:**
    1.  Abstract class `Character` with `health`, `strength`, `attack()`.
    2.  Subclasses: `Warrior` (high health), `Mage` (low health, high damage), `Rogue` (chance to dodge).
    3.  **Logic:** The `attack()` method should calculate damage based on strength and randomness.
    4.  **Arena:** Loop a battle between two characters until one's health drops to 0.
    5.  **Polymorphism:** The main code calls `p1.attack(p2)`—it shouldn't care if p1 is a Mage or Warrior.

---

## 🗓️ Week 3: Advanced Data & Exceptions


### Day 11: Collections Deep Dive (Performance)
**Concepts:** `ArrayList` vs `LinkedList` (Big O), `HashMap` internal workings (Buckets/HashCode).
* **Intense Exercises:**
    1.  **Performance Test:** Insert 1 million integers into an `ArrayList` and a `LinkedList`. Measure and print the time taken to `get()` the middle element for both. Explain the difference.
    2.  **Custom Key:** Create a class `Person`. Use it as a Key in a `HashMap`. Demonstrate what goes wrong if you override `equals()` but NOT `hashCode()`.

### Day 12: Generics & Wildcards
**Concepts:** Bounded Type Parameters (`<T extends Number>`), Wildcards (`? super Integer`).
* **Intense Exercises:**
    1.  **Generic Stack:** Implement your own `MyStack<T>` class using an array internally. Handle the resizing of the array when it gets full.
    2.  **Wildcard Sum:** Write a method `sumList(List<? extends Number> list)` that can accept a `List<Integer>` OR a `List<Double>` and return the total sum.

### Day 13: Exception Handling Patterns
**Concepts:** Try-with-resources, Multi-catch, Stack Traces, Checked vs Unchecked.
* **Intense Exercises:**
    1.  **Auto-Closeable:** Create a class `Resource` that implements `AutoCloseable`. Use it in a try-with-resources block to prove the `close()` method runs automatically even if an exception occurs.
    2.  **Rethrowing:** Catch a standard exception (e.g., `IOException`) and rethrow it as a custom RuntimeException (`DataProcessingException`) to hide implementation details.

### Day 14: Java 8 Streams & Lambdas
**Concepts:** Functional Interfaces (`Predicate`, `Consumer`, `Function`), Stream pipelines, Lazy evaluation.
* **Intense Exercises:**
    1.  **Stream Statistics:** Given a list of 100 random integers: use Streams to find the Max, Min, Average, and Sum in a single pass (using `IntSummaryStatistics`).
    2.  **Grouping:** Given a list of `Employee` objects, use `Collectors.groupingBy` to create a `Map<Department, List<Employee>>`.

### Day 15: File I/O & Serialization
**Concepts:** `NIO.2` (Files, Paths), `Serializable`.
* **Intense Exercises:**
    1.  **Directory Walker:** Write a program that recursively lists every file in a given folder (and subfolders) and prints their file size.
    2.  **Object Serialization:** Save the RPG Character object from Week 2 into a `.dat` file. Write a separate program to load it back into memory to "resume" the game.

---

### ☠️ Week 3 Friday Challenge: "Log File Analyzer"
**Goal:** Streams, IO, and String manipulation.
* **Task:** Parse a massive server log file.
* **Requirements:**
    1.  Generate a dummy log file with 10,000 lines: `[IP_ADDRESS] [TIMESTAMP] [STATUS_CODE] [URL]`
    2.  **Analysis:**
        * Count total requests per IP address.
        * Find the Top 3 most requested URLs.
        * Calculate the percentage of "404 Error" responses.
    3.  **Constraint:** Use Java Streams for the analytics.

---

## 🗓️ Week 4: The "Pro" Stack (Concurrency & Tooling)


### Day 16: Basic Concurrency (Threads)
**Concepts:** `Thread` vs `Runnable`, Thread Lifecycle, `join()`, `sleep()`.
* **Intense Exercises:**
    1.  **Race Condition:** Create a shared counter variable. Launch 10 threads that each increment it 1000 times. Print the final result. (It will likely be wrong).
    2.  **The Fix:** Fix the above using the `synchronized` keyword or `AtomicInteger`.

### Day 17: Advanced Concurrency (Executors)
**Concepts:** Thread Pools (`ExecutorService`), `Callable`, `Future`.
* **Intense Exercises:**
    1.  **Thread Pool:** Create a "Fixed Thread Pool" of size 3. Submit 10 tasks that each take 1 second to run. Observe how they queue up and execute in batches.
    2.  **Future Result:** Submit a calculation task to an Executor. Do other work in the main thread. Then use `future.get()` to retrieve the result, handling the timeout if it takes too long.

### Day 18: Build Tools & Dependency Management
**Concepts:** Maven/Gradle structure, `pom.xml`, Dependencies.
* **Action:**
    1.  **Mavenize:** Take your Week 2 RPG project. Convert it into a Standard Maven Project structure (`src/main/java`).
    2.  **External Lib:** Add the `Gson` or `Jackson` dependency to `pom.xml`. Use it to convert your objects to JSON strings.

### Day 19: Unit Testing (JUnit 5)
**Concepts:** `@Test`, `@BeforeEach`, Assertions, Mocking concepts.
* **Intense Exercises:**
    1.  **Test the RPG:** Write JUnit tests for your `Warrior` class. Ensure health doesn't drop below 0.
    2.  **Edge Cases:** Write a test for your "Division" method to ensure it throws the correct exception when dividing by zero using `assertThrows`.

### Day 20: Database Basics (JDBC)
**Concepts:** JDBC Driver, `Connection`, `PreparedStatement`, SQL Injection prevention.
* **Intense Exercises:**
    1.  **Connect:** Connect to a local SQLite or H2 database.
    2.  **CRUD:** Write a Java program that Creates a table `Users`, Inserts a user, and Selects them back using `PreparedStatement`.

---

### ☠️ Week 4 Friday Challenge: "Multi-threaded Bank"
**Goal:** Handling concurrency and locking safely.
* **Task:** Simulate a bank with 100 accounts.
* **Requirements:**
    1.  Create 100 `Account` objects with $1000 each.
    2.  Create a "TransactionEngine" that spins up 20 threads.
    3.  Each thread randomly picks two accounts and transfers a random amount.
    4.  **Critical:** You must ensure no money is created or lost. The total money in the bank must remain exactly $100,000 at the end.
    5.  Use `synchronized` blocks or `ReentrantLock` to prevent race conditions.

---

## 🗓️ Week 5: Capstone Project (Can this be done in Week 4 itself?)
*Choose ONE of the following to build over 5 days.*

### Option A: The "Console E-Commerce Store"
* **Features:** User login (File I/O), Product Catalog (Collections), Cart Management, Checkout (Interface simulation), Order History (JSON/File storage).
* **Requirement:** Must use Maven, JUnit Tests (at least 5), and proper OOP design.

### Option B: The "Chat Server" (Networking)
* **Features:** A Server that listens on a port. Multiple Clients can connect (using Threads).
* **Function:** When Client A types a message, Client B and C see it.
* **Requirement:** Use `java.net.Socket` and `ServerSocket`. Handle client disconnections gracefully.


