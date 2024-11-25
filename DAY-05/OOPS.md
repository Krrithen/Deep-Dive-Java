### Day 5: Object-Oriented Programming - Classes and Objects

#### **1. Object-Oriented Programming (OOP) Principles**

OOP is a programming paradigm based on the concept of "objects," which contain data (fields) and behavior (methods). The four key principles of OOP are:

1. **Encapsulation**:
   - Bundles data and methods operating on the data into a single unit (class).
   - Protects data from unauthorized access by using private fields and exposing public getter/setter methods.
   - **Example**:
     ```java
     class Employee {
         private String name;
         private int age;

         public String getName() {
             return name;
         }

         public void setName(String name) {
             this.name = name;
         }

         public int getAge() {
             return age;
         }

         public void setAge(int age) {
             if (age > 0) {
                 this.age = age;
             }
         }
     }
     ```

2. **Abstraction**:
   - Hides implementation details and shows only the essential features of an object.
   - Achieved using abstract classes or interfaces.
   - **Example**:
     ```java
     abstract class Vehicle {
         abstract void start();
     }

     class Car extends Vehicle {
         void start() {
             System.out.println("Car starts with a key.");
         }
     }
     ```

3. **Inheritance**:
   - Allows one class to acquire the properties and behavior of another class.
   - **Base class (Parent)**: Provides common features.
   - **Derived class (Child)**: Adds or overrides functionality.
   - **Example**:
     ```java
     class Animal {
         void eat() {
             System.out.println("This animal eats food");
         }
     }

     class Cat extends Animal {
         void meow() {
             System.out.println("Cat meows");
         }
     }
     ```

4. **Polymorphism**:
   - Enables methods to perform different tasks depending on the context.
   - **Compile-time Polymorphism (Method Overloading)**: Same method name, different parameters.
   - **Run-time Polymorphism (Method Overriding)**: Child class overrides parent class method.
   - **Example**:
     ```java
     // Overloading
     class Calculator {
         int add(int a, int b) {
             return a + b;
         }

         double add(double a, double b) {
             return a + b;
         }
     }

     // Overriding
     class Animal {
         void sound() {
             System.out.println("Animal makes a sound");
         }
     }

     class Dog extends Animal {
         @Override
         void sound() {
             System.out.println("Dog barks");
         }
     }
     ```

---

#### **2. Classes and Objects**

1. **Class**:
   - A blueprint that defines the structure (fields) and behavior (methods) of an object.
   - **Example**:
     ```java
     class Student {
         String name;
         int rollNo;

         void displayDetails() {
             System.out.println("Name: " + name + ", Roll No: " + rollNo);
         }
     }
     ```

2. **Object**:
   - An instance of a class created using the `new` keyword.
   - **Example**:
     ```java
     Student student1 = new Student();
     student1.name = "John";
     student1.rollNo = 101;
     student1.displayDetails();
     ```

---

#### **3. Constructors**

1. **What is a Constructor?**
   - A special method used to initialize an object when it is created.
   - Has the same name as the class and no return type.

2. **Types of Constructors**:
   - **Default Constructor**:
     - No arguments. Provided by the compiler if not explicitly defined.
     - **Example**:
       ```java
       class Car {
           Car() {
               System.out.println("Car object created!");
           }
       }

       Car car1 = new Car(); // Outputs: Car object created!
       ```

   - **Parameterized Constructor**:
     - Takes arguments to initialize fields.
     - **Example**:
       ```java
       class Car {
           String model;

           Car(String model) {
               this.model = model;
           }
       }

       Car car1 = new Car("Tesla");
       ```

   - **Constructor Overloading**:
     - Multiple constructors with different parameter lists.
     - **Example**:
       ```java
       class Person {
           String name;
           int age;

           Person() {
               name = "Default Name";
               age = 18;
           }

           Person(String name, int age) {
               this.name = name;
               this.age = age;
           }
       }
       ```

---

#### **4. `this` Keyword**

1. **Referring to the Current Object**:
   - Resolves ambiguity between instance variables and parameters.
   - **Example**:
     ```java
     class Employee {
         String name;

         Employee(String name) {
             this.name = name; // Resolves ambiguity
         }
     }
     ```

2. **Invoking Current Class Constructor**:
   - Calls one constructor from another in the same class.
   - **Example**:
     ```java
     class Employee {
         String name;
         int age;

         Employee() {
             this("Unknown", 0);
         }

         Employee(String name, int age) {
             this.name = name;
             this.age = age;
         }
     }
     ```

---

#### **5. Static Members**

1. **Static Variables**:
   - Shared among all instances of a class.
   - **Example**:
     ```java
     class Counter {
         static int count = 0;

         Counter() {
             count++;
         }
     }
     ```

2. **Static Methods**:
   - Belong to the class rather than any object. Can access only static members.
   - **Example**:
     ```java
     class MathUtils {
         static int square(int n) {
             return n * n;
         }
     }

     int result = MathUtils.square(5);
     ```

3. **Static Block**:
   - Executes once when the class is loaded.
   - **Example**:
     ```java
     class App {
         static {
             System.out.println("Static block executed");
         }
     }
     ```

---

#### **6. Inner Classes**

1. **Static Nested Classes**:
   - Can access outer class static members directly.
   - **Example**:
     ```java
     class Outer {
         static class Nested {
             void display() {
                 System.out.println("Static nested class");
             }
         }
     }
     ```

2. **Non-Static Inner Classes**:
   - Require an instance of the outer class to be created.
   - **Example**:
     ```java
     class Outer {
         class Inner {
             void display() {
                 System.out.println("Non-static inner class");
             }
         }
     }

     Outer.Inner obj = new Outer().new Inner();
     ```

3. **Anonymous Inner Classes**:
   - Used to create one-time implementations of interfaces or abstract classes.
   - **Example**:
     ```java
     interface Greeting {
         void sayHello();
     }

     Greeting greet = new Greeting() {
         public void sayHello() {
             System.out.println("Hello, World!");
         }
     };
     greet.sayHello();
     ```

---