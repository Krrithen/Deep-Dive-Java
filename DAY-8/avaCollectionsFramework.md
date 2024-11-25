### **Day 8: Java Collections Framework Overview**

---

#### **1. Java Collections Framework (JCF)**

**Definition**:  
The Java Collections Framework (JCF) provides a standard way to handle groups of objects efficiently. It includes interfaces, concrete classes, and utility methods to perform operations like searching, sorting, inserting, and deleting.

---

#### **1.1 Key Features of JCF**
1. **Unified Architecture**: Provides common methods across different collections (e.g., `add()`, `remove()`, `size()`).
2. **Flexibility**: Allows dynamic resizing, unlike arrays which have a fixed size.
3. **Generics Support**: Ensures type safety at compile time.
4. **Thread Safety (Optional)**: Classes like `Vector` and `Hashtable` are synchronized for thread-safe operations.
5. **Readymade Algorithms**: Contains methods for sorting, shuffling, searching, and more (in `Collections` utility class).

---

#### **2. Core Interfaces in the Collections Framework**

1. **`Collection` Interface**:
   - The root interface for most collection types.
   - Contains common methods like `add()`, `remove()`, `size()`, etc.
   - Subinterfaces: `List`, `Set`, and `Queue`.

2. **`List` Interface**:
   - An ordered collection allowing duplicate elements.
   - Indexed for random access.
   - Common Implementations: `ArrayList`, `LinkedList`, `Vector`.

3. **`Set` Interface**:
   - A collection that does not allow duplicate elements.
   - Common Implementations: `HashSet`, `TreeSet`, `LinkedHashSet`.

4. **`Queue` Interface**:
   - A collection designed for holding elements before processing (FIFO).
   - Common Implementations: `PriorityQueue`, `ArrayDeque`.

5. **`Map` Interface**:
   - Stores key-value pairs (does not extend `Collection`).
   - Duplicate keys are not allowed, but duplicate values are permitted.
   - Common Implementations: `HashMap`, `TreeMap`, `LinkedHashMap`.

---

#### **3. Key Implementations**

| **Class**         | **Characteristics**                                                                                           | **Use Cases**                                        |
|--------------------|-------------------------------------------------------------------------------------------------------------|-----------------------------------------------------|
| `ArrayList`        | Dynamic array, fast random access, slower for insertions/deletions.                                          | Frequently accessed collections.                    |
| `LinkedList`       | Doubly-linked list, faster for insertions/deletions, slower random access.                                   | Queue-based operations.                             |
| `HashSet`          | Unordered collection, no duplicates, uses hashing.                                                         | Fast searches in a non-ordered set.                 |
| `TreeSet`          | Ordered, no duplicates, elements sorted in natural or custom order.                                         | Sorted sets, range queries.                         |
| `PriorityQueue`    | Maintains elements in a priority order (natural or custom).                                                 | Job scheduling, task prioritization.                |
| `HashMap`          | Unordered key-value pairs, fast lookups and updates.                                                       | Storing mappings for quick retrievals.              |
| `TreeMap`          | Key-value pairs, maintains sorted order of keys.                                                           | Maintaining sorted mappings.                        |
| `ArrayDeque`       | Double-ended queue, supports insertion and deletion at both ends.                                           | Stack and queue implementations.                    |

---

#### **4. Generics in Collections**

- Introduced in Java 5 to enforce type safety at compile time.
- **Why Generics?**  
  Without generics, collections store `Object`, leading to runtime type casting and potential `ClassCastException`.
- Example with Generics:
  ```java
  import java.util.ArrayList;

  public class Main {
      public static void main(String[] args) {
          ArrayList<String> list = new ArrayList<>();
          list.add("Java");  // Type-safe
          list.add("Python");
          // list.add(123); // Compile-time error
          System.out.println(list);
      }
  }
  ```

---

#### **5. List Implementations**

1. **`ArrayList`**:
   - Backed by an array.
   - Best for random access.
   - Automatically resizes when full.
   - Example:
     ```java
     import java.util.ArrayList;

     public class Main {
         public static void main(String[] args) {
             ArrayList<String> list = new ArrayList<>();
             list.add("A");
             list.add("B");
             list.add("C");
             list.remove("B");
             System.out.println(list); // Output: [A, C]
         }
     }
     ```

2. **`LinkedList`**:
   - Implements both `List` and `Deque`.
   - Stores elements as nodes in a doubly-linked list.
   - Example:
     ```java
     import java.util.LinkedList;

     public class Main {
         public static void main(String[] args) {
             LinkedList<String> list = new LinkedList<>();
             list.add("A");
             list.addFirst("B");
             list.addLast("C");
             System.out.println(list); // Output: [B, A, C]
         }
     }
     ```

---

#### **6. Set Implementations**

1. **`HashSet`**:
   - Uses hashing for storage.
   - Does not maintain order.
   - Example:
     ```java
     import java.util.HashSet;

     public class Main {
         public static void main(String[] args) {
             HashSet<Integer> set = new HashSet<>();
             set.add(1);
             set.add(2);
             set.add(1); // Duplicate, ignored
             System.out.println(set); // Output: [1, 2]
         }
     }
     ```

2. **`TreeSet`**:
   - Maintains sorted order.
   - Slower than `HashSet` for insertion and deletion.
   - Example:
     ```java
     import java.util.TreeSet;

     public class Main {
         public static void main(String[] args) {
             TreeSet<Integer> treeSet = new TreeSet<>();
             treeSet.add(10);
             treeSet.add(5);
             treeSet.add(15);
             System.out.println(treeSet); // Output: [5, 10, 15]
         }
     }
     ```

---

#### **7. Queue Implementations**

1. **`PriorityQueue`**:
   - Elements are ordered based on priority.
   - Example:
     ```java
     import java.util.PriorityQueue;

     public class Main {
         public static void main(String[] args) {
             PriorityQueue<Integer> pq = new PriorityQueue<>();
             pq.add(20);
             pq.add(10);
             pq.add(30);
             System.out.println(pq.poll()); // Output: 10 (lowest priority)
         }
     }
     ```

2. **`ArrayDeque`**:
   - Double-ended queue for efficient insertions and deletions.
   - Example:
     ```java
     import java.util.ArrayDeque;

     public class Main {
         public static void main(String[] args) {
             ArrayDeque<String> deque = new ArrayDeque<>();
             deque.addFirst("A");
             deque.addLast("B");
             System.out.println(deque); // Output: [A, B]
         }
     }
     ```

---

#### **8. Map Implementations**

1. **`HashMap`**:
   - Unordered key-value pairs.
   - Example:
     ```java
     import java.util.HashMap;

     public class Main {
         public static void main(String[] args) {
             HashMap<Integer, String> map = new HashMap<>();
             map.put(1, "One");
             map.put(2, "Two");
             System.out.println(map); // Output: {1=One, 2=Two}
         }
     }
     ```

2. **`TreeMap`**:
   - Maintains sorted order of keys.
   - Example:
     ```java
     import java.util.TreeMap;

     public class Main {
         public static void main(String[] args) {
             TreeMap<String, Integer> treeMap = new TreeMap<>();
             treeMap.put("C", 3);
             treeMap.put("A", 1);
             System.out.println(treeMap); // Output: {A=1, C=3}
         }
     }
     ```

---

#### **9. Utility Methods in `Collections`**

| **Method**          | **Description**                        |
|----------------------|----------------------------------------|
| `sort(List<T> list)` | Sorts the list in natural order.       |
| `reverse(List<T>)`   | Reverses the order of elements.        |
| `shuffle(List<T>)`   | Shuffles the elements randomly.        |
| `binarySearch()`     | Searches for a key in a sorted list.   |
| `max()` / `min()`    | Finds the maximum or minimum element.  |

Example:
```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        List<Integer> list = Arrays.asList(5, 3, 8, 1);
        Collections.sort(list);
        System.out.println(list); // Output: [1, 3, 5, 8]
    }
}
```

---

#### **10. Summary**
- JCF is a powerful library that simplifies handling complex data structures.
- Interfaces like `List`, `Set`, `Queue`, and `Map` form the foundation of JCF.
- Each implementation has unique characteristics suitable for specific use cases.
- Utility methods in `Collections` enhance operations like sorting and searching.

---