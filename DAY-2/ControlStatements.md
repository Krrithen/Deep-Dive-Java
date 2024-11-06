## For Day 1 - basics of Java: **Control Flow and Decision-Making**
This includes `if` statements, `switch` statements, loops (`for`, `while`, and `do-while`), and control flow mechanisms like `break`, `continue`, and `return`.

---

### 1. **If Statements**

   - **Definition**: The `if` statement is a conditional statement used to execute a block of code only if a specified condition is `true`.
   - **Syntax**:
     ```java
     if (condition) {
         // code to execute if condition is true
     }
     ```
   - **Example**:
     ```java
     int age = 18;
     if (age >= 18) {
         System.out.println("Eligible to vote");
     }
     ```

   - **`else` and `else if` Statements**: Used to handle alternative conditions.
     - **Syntax**:
       ```java
       if (condition) {
           // code if true
       } else if (anotherCondition) {
           // code if another condition is true
       } else {
           // code if all conditions are false
       }
       ```
     - **Example**:
       ```java
       int score = 85;
       if (score >= 90) {
           System.out.println("A grade");
       } else if (score >= 80) {
           System.out.println("B grade");
       } else {
           System.out.println("C grade");
       }
       ```

---

### 2. **Switch Statements**

   - **Definition**: The `switch` statement selects one of many code blocks to be executed based on the value of an expression.
   - **Syntax**:
     ```java
     switch (expression) {
         case value1:
             // code to execute
             break;
         case value2:
             // code to execute
             break;
         default:
             // code to execute if no case matches
     }
     ```
   - **Example**:
     ```java
     int day = 3;
     switch (day) {
         case 1:
             System.out.println("Monday");
             break;
         case 2:
             System.out.println("Tuesday");
             break;
         case 3:
             System.out.println("Wednesday");
             break;
         default:
             System.out.println("Invalid day");
     }
     ```
   - **Important**: The `break` statement is used to terminate a case. Without it, the program will continue to execute the following cases (known as “fall-through”).

---

### 3. **For Loops**

   - **Definition**: The `for` loop is used to repeat a block of code a specific number of times.
   - **Syntax**:
     ```java
     for (initialization; condition; update) {
         // code to execute
     }
     ```
   - **Example**:
     ```java
     for (int i = 0; i < 5; i++) {
         System.out.println("i = " + i);
     }
     ```
   - **Enhanced For Loop (for-each loop)**: Used to iterate over arrays or collections.
     - **Syntax**:
       ```java
       for (type var : array) {
           // code to execute
       }
       ```
     - **Example**:
       ```java
       int[] numbers = {1, 2, 3};
       for (int num : numbers) {
           System.out.println(num);
       }
       ```

---

### 4. **While Loops**

   - **Definition**: The `while` loop is used to repeat a block of code as long as a specified condition is `true`.
   - **Syntax**:
     ```java
     while (condition) {
         // code to execute
     }
     ```
   - **Example**:
     ```java
     int count = 0;
     while (count < 5) {
         System.out.println("Count: " + count);
         count++;
     }
     ```

---

### 5. **Do-While Loops**

   - **Definition**: Similar to the `while` loop, but the code executes at least once because the condition is checked after the loop body.
   - **Syntax**:
     ```java
     do {
         // code to execute
     } while (condition);
     ```
   - **Example**:
     ```java
     int count = 0;
     do {
         System.out.println("Count: " + count);
         count++;
     } while (count < 5);
     ```

---

### 6. **Break Statement**

   - **Definition**: The `break` statement terminates a loop or switch statement prematurely.
   - **Syntax**:
     ```java
     for (int i = 0; i < 10; i++) {
         if (i == 5) {
             break;  // exits loop when i == 5
         }
         System.out.println(i);
     }
     ```

---

### 7. **Continue Statement**

   - **Definition**: The `continue` statement skips the current iteration of a loop and proceeds to the next iteration.
   - **Syntax**:
     ```java
     for (int i = 0; i < 10; i++) {
         if (i % 2 == 0) {
             continue;  // skips even numbers
         }
         System.out.println(i);
     }
     ```

---

### 8. **Return Statement**

   - **Definition**: The `return` statement exits from a method and optionally returns a value to the method caller.
   - **Syntax**:
     ```java
     public int add(int a, int b) {
         return a + b;  // exits and returns a result
     }
     ```
   - **Note**: `return` is mandatory for methods with a return type (except `void`).

---

### Summary and Key Points to Remember

1. **If-Else**: Used for decision-making with one or multiple conditions.
2. **Switch**: Efficient for checking multiple values of an expression, especially when they are known constants.
3. **For Loop**: Used for executing a block of code a known number of times.
4. **Enhanced For Loop**: Ideal for iterating over arrays and collections.
5. **While and Do-While Loops**: Execute code while a condition is true, with `do-while` guaranteeing at least one execution.
6. **Break**: Exits loops or `switch` statements early.
7. **Continue**: Skips the rest of the current loop iteration and moves to the next.
8. **Return**: Exits a method, optionally passing back a result.

---