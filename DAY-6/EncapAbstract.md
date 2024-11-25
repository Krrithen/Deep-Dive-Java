### Day 6: Object-Oriented Programming - Encapsulation and Abstraction  

#### **1. Encapsulation**

**Definition**:  
Encapsulation is the process of bundling data (fields) and methods (functions) that operate on the data into a single unit, the class. It restricts direct access to some of the object's components, which is why it's often referred to as "data hiding."

**Key Characteristics**:
1. **Private Fields**:
   - Data members of a class are declared `private` to prevent unauthorized access.
2. **Public Methods (Getters and Setters)**:
   - Access to private fields is provided via `public` getter and setter methods.

**Benefits**:
1. Protects data integrity by allowing validation.
2. Reduces complexity by hiding implementation details.
3. Improves code maintainability.

**Implementation**:  
Here’s how encapsulation is applied:
```java
class BankAccount {
    private double balance;

    public double getBalance() {
        return balance;
    }

    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
        } else {
            System.out.println("Invalid deposit amount!");
        }
    }

    public void withdraw(double amount) {
        if (amount > 0 && amount <= balance) {
            balance -= amount;
        } else {
            System.out.println("Invalid withdrawal amount!");
        }
    }
}

public class Main {
    public static void main(String[] args) {
        BankAccount account = new BankAccount();
        account.deposit(1000);
        System.out.println("Balance: " + account.getBalance());
        account.withdraw(500);
        System.out.println("Balance: " + account.getBalance());
    }
}
```

---

#### **2. Abstraction**

**Definition**:  
Abstraction focuses on hiding implementation details and exposing only the essential features of an object or a system. It allows developers to define "what an object does" instead of "how it does it."

**Key Characteristics**:
1. Achieved using:
   - **Abstract Classes**
   - **Interfaces**
2. Promotes a high-level view of behavior.

**Benefits**:
1. Reduces code complexity.
2. Enhances reusability by separating concerns.
3. Provides flexibility by allowing multiple implementations.

---

#### **2.1 Abstract Classes**

1. **What is an Abstract Class?**  
   - A class that cannot be instantiated directly.
   - Can have both `abstract` (methods without implementation) and `concrete` (methods with implementation) methods.

2. **When to Use Abstract Classes**:
   - When a base class provides some common functionality, but specific details are left for derived classes.

3. **Syntax**:
   ```java
   abstract class Shape {
       abstract void draw(); // Abstract method
       void description() {
           System.out.println("This is a shape.");
       }
   }

   class Circle extends Shape {
       void draw() {
           System.out.println("Drawing a circle.");
       }
   }

   public class Main {
       public static void main(String[] args) {
           Shape s = new Circle();
           s.draw();
           s.description();
       }
   }
   ```

**Important Notes**:
- Abstract methods **must** be overridden in child classes.
- Abstract classes can have constructors, fields, and methods.

---

#### **2.2 Interfaces**

1. **What is an Interface?**  
   - A blueprint for a class. It defines a contract that implementing classes must fulfill.
   - All methods in an interface are implicitly `public` and `abstract` (prior to Java 8).
   - Fields in an interface are `public`, `static`, and `final`.

2. **When to Use Interfaces**:
   - To achieve **100% abstraction** (before Java 8).
   - When multiple inheritance is required, as Java doesn’t support it with classes.

3. **Syntax**:
   ```java
   interface Animal {
       void eat();
       void sleep();
   }

   class Dog implements Animal {
       public void eat() {
           System.out.println("Dog eats bones.");
       }

       public void sleep() {
           System.out.println("Dog sleeps in a kennel.");
       }
   }

   public class Main {
       public static void main(String[] args) {
           Animal a = new Dog();
           a.eat();
           a.sleep();
       }
   }
   ```

---

#### **3. Key Differences Between Abstract Classes and Interfaces**

| Feature                  | Abstract Class                          | Interface                              |
|--------------------------|-----------------------------------------|----------------------------------------|
| **Purpose**              | Partial abstraction (can have both concrete and abstract methods). | Complete abstraction (Java 8+ allows concrete methods). |
| **Inheritance**          | A class can inherit **only one** abstract class. | A class can implement **multiple** interfaces. |
| **Fields**               | Can have instance variables.           | Only `public static final` fields (constants). |
| **Constructors**         | Allowed.                               | Not allowed.                          |
| **Default Methods (Java 8)** | Not required, but possible.             | Supported.                            |

---

#### **4. Default and Static Methods in Interfaces (Java 8+)**

1. **Default Methods**:
   - Allow interfaces to have methods with default implementation.
   - **Example**:
     ```java
     interface Animal {
         void eat();
         default void sound() {
             System.out.println("Animal makes a sound.");
         }
     }

     class Dog implements Animal {
         public void eat() {
             System.out.println("Dog eats bones.");
         }
     }

     public class Main {
         public static void main(String[] args) {
             Animal dog = new Dog();
             dog.eat();
             dog.sound();
         }
     }
     ```

2. **Static Methods**:
   - Defined at the interface level and cannot be overridden.
   - **Example**:
     ```java
     interface Utility {
         static void printMessage() {
             System.out.println("Static method in interface.");
         }
     }

     public class Main {
         public static void main(String[] args) {
             Utility.printMessage();
         }
     }
     ```

---

#### **5. Real-Life Example: ATM System**

1. **Encapsulation**:
   - Fields like `PIN` and `balance` are kept private in the `Account` class.
   - Public methods like `withdraw()` and `deposit()` are used to access and modify these fields safely.

2. **Abstraction**:
   - Different transaction types (deposit, withdrawal) are abstracted through interfaces or abstract classes, while the implementation of these features is handled by specific classes.

**Code**:
```java
interface Transaction {
    void execute();
}

class Deposit implements Transaction {
    private double amount;

    Deposit(double amount) {
        this.amount = amount;
    }

    public void execute() {
        System.out.println("Depositing $" + amount);
    }
}

class Withdrawal implements Transaction {
    private double amount;

    Withdrawal(double amount) {
        this.amount = amount;
    }

    public void execute() {
        System.out.println("Withdrawing $" + amount);
    }
}

public class Main {
    public static void main(String[] args) {
        Transaction t1 = new Deposit(500);
        Transaction t2 = new Withdrawal(300);

        t1.execute();
        t2.execute();
    }
}
```

---