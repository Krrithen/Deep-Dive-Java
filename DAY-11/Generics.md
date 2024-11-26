### **Day 11: Generics and Type Safety in Java**  

---

### **1. Introduction to Generics**

Generics are a mechanism in Java that:
1. Enable **type safety** by specifying a type for objects used in classes, methods, or interfaces at compile time.
2. Allow code **reusability**, avoiding the need to write multiple implementations for different data types.

Without generics, objects like `List` or `Map` would store data as raw types (`Object`), which requires explicit typecasting and is error-prone. Generics eliminate this issue.

---

### **2. Why Generics?**
#### **2.1 Type Safety**
Generics restrict the type of objects that can be stored in a collection, avoiding `ClassCastException` at runtime.

- **Without Generics**:
  ```java
  import java.util.ArrayList;

  public class Main {
      public static void main(String[] args) {
          ArrayList list = new ArrayList(); // Raw type
          list.add("Java");
          list.add(123); // Allowed, but unsafe
          String str = (String) list.get(1); // Throws ClassCastException
      }
  }
  ```

- **With Generics**:
  ```java
  import java.util.ArrayList;

  public class Main {
      public static void main(String[] args) {
          ArrayList<String> list = new ArrayList<>();
          list.add("Java");
          // list.add(123); // Compile-time error
          String str = list.get(0); // No typecasting required
      }
  }
  ```

#### **2.2 Code Reusability**
Generics eliminate redundancy by allowing one implementation to work with different types:
- For example, a generic `swap()` method works with `Integer`, `String`, or any other type.

---

### **3. Generic Classes**

#### **3.1 Syntax**
```java
class GenericClass<T> { // 'T' is the type parameter
    private T data;

    public GenericClass(T data) {
        this.data = data;
    }

    public T getData() {
        return data;
    }
}
```

#### **3.2 Example**
```java
public class Main {
    public static void main(String[] args) {
        GenericClass<String> stringInstance = new GenericClass<>("Hello");
        System.out.println(stringInstance.getData()); // Output: Hello

        GenericClass<Integer> integerInstance = new GenericClass<>(123);
        System.out.println(integerInstance.getData()); // Output: 123
    }
}

class GenericClass<T> {
    private T data;

    public GenericClass(T data) {
        this.data = data;
    }

    public T getData() {
        return data;
    }
}
```

#### **3.3 Type Parameters**
Commonly used type parameters:
- `T` – Type
- `E` – Element (used in collections like `List<E>`)
- `K` and `V` – Key and Value (used in maps like `Map<K, V>`)

---

### **4. Generic Methods**

#### **4.1 Syntax**
```java
public static <T> void genericMethod(T data) {
    System.out.println("Data: " + data);
}
```

#### **4.2 Example**
```java
public class Main {
    public static void main(String[] args) {
        genericMethod("Java");
        genericMethod(100);
    }

    public static <T> void genericMethod(T data) {
        System.out.println("Data: " + data);
    }
}
```

---

### **5. Bounded Types in Generics**

#### **5.1 Upper Bound**
Restricts the type parameter to a specific type or its subclasses.
```java
class UpperBound<T extends Number> { // Only Number and its subclasses
    private T data;

    public UpperBound(T data) {
        this.data = data;
    }

    public T getData() {
        return data;
    }
}

public class Main {
    public static void main(String[] args) {
        UpperBound<Integer> intInstance = new UpperBound<>(123); // Valid
        // UpperBound<String> stringInstance = new UpperBound<>("Hello"); // Compile-time error
    }
}
```

#### **5.2 Lower Bound**
Specifies a type and its superclasses (usually used in wildcard contexts).
```java
public static void printNumbers(List<? super Integer> list) {
    for (Object obj : list) {
        System.out.println(obj);
    }
}
```

---

### **6. Wildcards in Generics**

Wildcards make generics more flexible when dealing with unknown types.

#### **6.1 Unbounded Wildcard (`<?>`)**
Allows any type.
```java
public static void printList(List<?> list) {
    for (Object obj : list) {
        System.out.println(obj);
    }
}
```

#### **6.2 Upper-Bounded Wildcard (`<? extends Type>`)**  
Limits the type to `Type` or its subclasses.
```java
public static void sumNumbers(List<? extends Number> list) {
    double sum = 0;
    for (Number num : list) {
        sum += num.doubleValue();
    }
    System.out.println("Sum: " + sum);
}
```

#### **6.3 Lower-Bounded Wildcard (`<? super Type>`)**  
Limits the type to `Type` or its superclasses.
```java
public static void addIntegers(List<? super Integer> list) {
    list.add(10); // Adding is allowed
}
```

---

### **7. Generic Interfaces**

Generics can also be applied to interfaces.

#### **Example**
```java
interface GenericInterface<T> {
    void display(T data);
}

class GenericClass<T> implements GenericInterface<T> {
    @Override
    public void display(T data) {
        System.out.println("Data: " + data);
    }
}

public class Main {
    public static void main(String[] args) {
        GenericInterface<String> instance = new GenericClass<>();
        instance.display("Java Generics");
    }
}
```

---

### **8. Generics and Collections**

Generics are heavily used in Java Collections for type safety:
- `List<String>`, `Map<Integer, String>`, etc.

#### **Example**
```java
import java.util.ArrayList;

public class Main {
    public static void main(String[] args) {
        ArrayList<String> list = new ArrayList<>();
        list.add("Java");
        // list.add(123); // Compile-time error
        System.out.println(list);
    }
}
```

---

### **9. Type Erasure**

During compilation, generic type information is removed to ensure compatibility with earlier Java versions.
- For example, `List<Integer>` becomes `List` at runtime.
- This means no generics exist at runtime, but type safety is ensured at compile-time.

---

### **10. Best Practices**

1. Use descriptive type names (`T`, `E`, `K`, `V`) for readability.
2. Avoid using raw types (`List` instead of `List<T>`).
3. Use bounded types when constraints are necessary.
4. Prefer wildcards (`<?>`, `<? extends>`, `<? super>`) for flexibility in method parameters.

---

### **11. Summary**
- **Generics** enable type safety and reusability in Java.
- Generic **classes**, **methods**, **interfaces**, and **wildcards** add flexibility while ensuring compile-time checks.
- Collections like `List`, `Set`, and `Map` are powerful examples of generics in action.

---