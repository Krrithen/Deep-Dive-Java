## For Day 1 - basics of Java: **variables, data types, and operators**

---

### **1. Java Variables**
A variable in Java is a container that holds data that can be changed during program execution. Variables have types, which determine the kind of data they can hold.

#### **Syntax**
```java
type variableName = value;
```

#### **Types of Variables**
1. **Local Variable**: Declared within a method or a block and only accessible within that scope.
2. **Instance Variable**: Declared inside a class but outside of any method, tied to object instances.
3. **Class Variable (Static Variable)**: Declared with the `static` keyword in a class, shared across all instances of the class.

#### **Example**
```java
public class Example {
    int instanceVar = 5;        // Instance variable
    static int staticVar = 10;  // Class variable

    public void method() {
        int localVar = 15;      // Local variable
        System.out.println(localVar);
    }
}
```

---

### **2. Data Types in Java**
Java is a strongly typed language, meaning each variable has a defined type.

#### **Primitive Data Types**
1. **byte**: 8-bit integer, range: -128 to 127
2. **short**: 16-bit integer, range: -32,768 to 32,767
3. **int**: 32-bit integer, range: -2^31 to 2^31-1
4. **long**: 64-bit integer, range: -2^63 to 2^63-1 (add an `L` to indicate a long literal, e.g., `1000L`)
5. **float**: 32-bit floating point, use `f` for literals (e.g., `3.14f`)
6. **double**: 64-bit floating point, default for decimals
7. **char**: Single 16-bit Unicode character (e.g., `'A'`)
8. **boolean**: Represents `true` or `false`

#### **Reference Data Types**
- Reference types are objects that refer to memory addresses where data is stored, such as arrays, classes, and interfaces.

#### **Example**
```java
int age = 25;
double salary = 50000.5;
boolean isJavaFun = true;
char grade = 'A';
```

---

### **3. Java Operators**
Java operators are symbols that perform operations on variables and values. Operators can be categorized as follows:

#### **Arithmetic Operators**
Used for basic mathematical operations.

| Operator | Description          | Example       |
|----------|----------------------|---------------|
| `+`      | Addition             | `a + b`      |
| `-`      | Subtraction          | `a - b`      |
| `*`      | Multiplication       | `a * b`      |
| `/`      | Division             | `a / b`      |
| `%`      | Modulus (remainder)  | `a % b`      |

#### **Example**
```java
int a = 10, b = 20;
int sum = a + b;           // 30
int remainder = b % a;     // 0
```

#### **Assignment Operators**
Used to assign values to variables.

| Operator | Description           | Example        |
|----------|-----------------------|----------------|
| `=`      | Simple assignment     | `a = 10`      |
| `+=`     | Add and assign        | `a += 5`      |
| `-=`     | Subtract and assign   | `a -= 5`      |
| `*=`     | Multiply and assign   | `a *= 5`      |
| `/=`     | Divide and assign     | `a /= 5`      |
| `%=`     | Modulus and assign    | `a %= 5`      |

#### **Example**
```java
int x = 10;
x += 5;   // x = 15
x *= 2;   // x = 30
```

#### **Comparison (Relational) Operators**
Used to compare two values.

| Operator | Description               | Example       |
|----------|---------------------------|---------------|
| `==`     | Equal to                  | `a == b`     |
| `!=`     | Not equal to              | `a != b`     |
| `>`      | Greater than              | `a > b`      |
| `<`      | Less than                 | `a < b`      |
| `>=`     | Greater than or equal to  | `a >= b`     |
| `<=`     | Less than or equal to     | `a <= b`     |

#### **Example**
```java
int age = 20;
boolean isAdult = (age >= 18);  // true
```

#### **Logical Operators**
Used to perform logical operations on boolean expressions.

| Operator | Description           | Example              |
|----------|-----------------------|----------------------|
| `&&`     | Logical AND           | `(a > b) && (c > d)` |
| `\|\|`   | Logical OR            | `(a > b) \|\| (c > d)` |
| `!`      | Logical NOT           | `!(a > b)`           |

#### **Example**
```java
boolean isAdult = true;
boolean isStudent = false;
boolean result = isAdult && isStudent; // false
```

#### **Increment and Decrement Operators**
Used to increase or decrease a variable’s value by 1.

| Operator | Description                     | Example       |
|----------|---------------------------------|---------------|
| `++`     | Increment                       | `a++` or `++a` |
| `--`     | Decrement                       | `a--` or `--a` |

#### **Example**
```java
int x = 5;
int y = ++x;   // y = 6, x = 6
int z = x--;   // z = 6, x = 5
```

#### **Ternary Operator**
A shorthand for `if-else` conditions.

```java
variable = (condition) ? expressionIfTrue : expressionIfFalse;
```

#### **Example**
```java
int age = 18;
String result = (age >= 18) ? "Adult" : "Minor";
```

---

### **4. Additional Notes and Tips**

- **Default Values**: Primitive variables have default values if not explicitly initialized (e.g., `int` is `0`, `boolean` is `false`), but local variables do not have default values and must be initialized.
- **Type Casting**: Java is a statically typed language, so sometimes you need to convert one type to another. This can be done with explicit casting.
    - **Implicit casting** (widening): Automatically converts smaller to larger data types, e.g., `int` to `double`.
    - **Explicit casting** (narrowing): Manually converts larger to smaller data types, e.g., `double` to `int`.
    
    ```java
    int x = 10;
    double y = x; // Implicit casting
    double a = 9.78;
    int b = (int) a; // Explicit casting, b is 9
    ```

- **`final` Keyword**: Used to declare constants or immutable variables. A `final` variable cannot be changed once assigned.
  
    ```java
    final int MAX_VALUE = 100;
    ```

---

This should cover the essentials for Day 1, including definitions, syntax, and examples.
