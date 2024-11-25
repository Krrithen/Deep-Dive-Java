### Day 7: Exception Handling and Basic I/O in Java  

#### **1. Exception Handling in Java**

**Definition**:  
Exception handling in Java is a mechanism to manage runtime errors, ensuring the normal flow of a program. It involves handling unexpected events that disrupt the execution of a program, such as invalid user input or file not found.

---

#### **1.1 Types of Exceptions**
1. **Checked Exceptions**:
   - Exceptions checked at compile time.
   - Example: `IOException`, `SQLException`.
   - Must be handled using `try-catch` or declared using `throws`.

2. **Unchecked Exceptions**:
   - Exceptions that occur at runtime.
   - Example: `ArithmeticException`, `NullPointerException`, `ArrayIndexOutOfBoundsException`.
   - Not mandatory to handle.

3. **Errors**:
   - Serious problems that applications should not try to handle.
   - Example: `OutOfMemoryError`, `StackOverflowError`.

---

#### **1.2 Exception Handling Keywords**
1. **`try` Block**:
   - Contains code that might throw an exception.
   - Example:
     ```java
     try {
         int result = 10 / 0;
     }
     ```

2. **`catch` Block**:
   - Handles exceptions thrown in the `try` block.
   - Example:
     ```java
     catch (ArithmeticException e) {
         System.out.println("Cannot divide by zero.");
     }
     ```

3. **`finally` Block**:
   - Always executes, regardless of exception occurrence.
   - Used for cleanup activities like closing resources.
   - Example:
     ```java
     finally {
         System.out.println("Cleanup code executed.");
     }
     ```

4. **`throw`**:
   - Used to explicitly throw an exception.
   - Example:
     ```java
     throw new ArithmeticException("Custom Exception");
     ```

5. **`throws`**:
   - Declares exceptions that a method might throw.
   - Example:
     ```java
     void method() throws IOException {
         // Code that might throw IOException
     }
     ```

---

#### **1.3 Example: Basic Exception Handling**
```java
public class Main {
    public static void main(String[] args) {
        try {
            int result = 10 / 0;
        } catch (ArithmeticException e) {
            System.out.println("Cannot divide by zero.");
        } finally {
            System.out.println("Execution completed.");
        }
    }
}
```

---

#### **1.4 Creating Custom Exceptions**
- Custom exceptions are user-defined exceptions extending `Exception` or `RuntimeException`.
- Example:
  ```java
  class MyException extends Exception {
      public MyException(String message) {
          super(message);
      }
  }

  public class Main {
      public static void main(String[] args) {
          try {
              throw new MyException("Custom exception occurred!");
          } catch (MyException e) {
              System.out.println(e.getMessage());
          }
      }
  }
  ```

---

#### **2. Basic Input/Output (I/O) in Java**

**Definition**:  
I/O in Java refers to reading and writing data to various sources like files, console, or network sockets.

---

#### **2.1 Java I/O Streams**
1. **Byte Streams**:
   - Used for binary data.
   - Classes: `InputStream`, `OutputStream`.
   - Example:
     ```java
     FileInputStream fis = new FileInputStream("file.txt");
     FileOutputStream fos = new FileOutputStream("output.txt");
     ```

2. **Character Streams**:
   - Used for text data.
   - Classes: `Reader`, `Writer`.
   - Example:
     ```java
     FileReader fr = new FileReader("file.txt");
     FileWriter fw = new FileWriter("output.txt");
     ```

---

#### **2.2 File Handling**
1. **Creating a File**:
   ```java
   import java.io.File;
   import java.io.IOException;

   public class Main {
       public static void main(String[] args) {
           try {
               File file = new File("example.txt");
               if (file.createNewFile()) {
                   System.out.println("File created: " + file.getName());
               } else {
                   System.out.println("File already exists.");
               }
           } catch (IOException e) {
               System.out.println("An error occurred.");
               e.printStackTrace();
           }
       }
   }
   ```

2. **Writing to a File**:
   ```java
   import java.io.FileWriter;
   import java.io.IOException;

   public class Main {
       public static void main(String[] args) {
           try (FileWriter writer = new FileWriter("example.txt")) {
               writer.write("Hello, world!");
               System.out.println("Successfully wrote to the file.");
           } catch (IOException e) {
               System.out.println("An error occurred.");
               e.printStackTrace();
           }
       }
   }
   ```

3. **Reading from a File**:
   ```java
   import java.io.FileReader;
   import java.io.BufferedReader;
   import java.io.IOException;

   public class Main {
       public static void main(String[] args) {
           try (BufferedReader reader = new BufferedReader(new FileReader("example.txt"))) {
               String line;
               while ((line = reader.readLine()) != null) {
                   System.out.println(line);
               }
           } catch (IOException e) {
               System.out.println("An error occurred.");
               e.printStackTrace();
           }
       }
   }
   ```

---

#### **2.3 Common Java I/O Classes**
| Class/Interface   | Description                                   |
|--------------------|-----------------------------------------------|
| `File`            | Represents a file or directory.              |
| `FileInputStream` | Reads data from a file (binary).             |
| `FileOutputStream`| Writes data to a file (binary).              |
| `FileReader`      | Reads data from a file (character-based).    |
| `FileWriter`      | Writes data to a file (character-based).     |
| `BufferedReader`  | Reads text from an input stream efficiently. |
| `BufferedWriter`  | Writes text to an output stream efficiently. |

---

#### **3. Real-World Example: File Copy Utility**
```java
import java.io.*;

public class FileCopy {
    public static void main(String[] args) {
        try (FileInputStream fis = new FileInputStream("source.txt");
             FileOutputStream fos = new FileOutputStream("destination.txt")) {
            int byteData;
            while ((byteData = fis.read()) != -1) {
                fos.write(byteData);
            }
            System.out.println("File copied successfully!");
        } catch (IOException e) {
            System.out.println("An error occurred.");
            e.printStackTrace();
        }
    }
}
```

---

#### **4. Summary**
- **Exception Handling**:
  - Use `try-catch-finally` for safe code execution.
  - Understand checked vs. unchecked exceptions.
  - Create custom exceptions for specific cases.

- **Basic I/O**:
  - Work with byte and character streams.
  - Master file handling techniques for creating, reading, and writing files.

---