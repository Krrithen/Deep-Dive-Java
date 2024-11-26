### **Day 10: Sets and Maps in Java - HashSet, TreeSet, HashMap, and TreeMap**

---

### **1. Introduction to Sets and Maps**

#### **1.1 Sets**
A `Set` is a collection that:
- Does not allow duplicate elements.
- Does not guarantee any particular order of elements (depends on the implementation).

#### **1.2 Maps**
A `Map` is a collection of key-value pairs:
- Keys are unique; each key maps to exactly one value.
- Allows fast retrieval, update, and deletion of elements based on keys.

---

### **2. Key Features of Sets and Maps**

| Feature             | Set                               | Map                                      |
|---------------------|-----------------------------------|-----------------------------------------|
| **Uniqueness**      | Elements are unique.             | Keys are unique; values can be duplicate. |
| **Order**           | Varies by implementation.        | Varies by implementation.               |
| **Null Handling**   | Allows one `null` element.       | Allows one `null` key; multiple `null` values. |

---

### **3. Set Implementations**

#### **3.1 HashSet**
- **Description**: Uses a hash table for storage. Elements are unordered.
- **Key Features**:
  - Fast operations (O(1) for `add`, `remove`, `contains`).
  - Allows one `null` value.
- **Use Case**: Maintaining a collection of unique elements.
- **Example**:
  ```java
  import java.util.HashSet;

  public class Main {
      public static void main(String[] args) {
          HashSet<String> set = new HashSet<>();
          set.add("Java");
          set.add("Python");
          set.add("Java"); // Duplicate, will not be added
          System.out.println(set); // Output: [Java, Python] (order not guaranteed)
      }
  }
  ```

#### **3.2 TreeSet**
- **Description**: Implements a sorted set using a red-black tree.
- **Key Features**:
  - Maintains elements in natural or custom order (via comparator).
  - No `null` elements (throws `NullPointerException`).
- **Use Case**: Sorted unique elements.
- **Example**:
  ```java
  import java.util.TreeSet;

  public class Main {
      public static void main(String[] args) {
          TreeSet<Integer> set = new TreeSet<>();
          set.add(10);
          set.add(5);
          set.add(15);
          System.out.println(set); // Output: [5, 10, 15]
      }
  }
  ```

---

### **4. Map Implementations**

#### **4.1 HashMap**
- **Description**: Uses a hash table for storing key-value pairs. Keys are unordered.
- **Key Features**:
  - Fast operations (O(1) for `put`, `get`, `remove`).
  - Allows one `null` key and multiple `null` values.
- **Use Case**: Fast key-based lookups.
- **Example**:
  ```java
  import java.util.HashMap;

  public class Main {
      public static void main(String[] args) {
          HashMap<String, Integer> map = new HashMap<>();
          map.put("Java", 1);
          map.put("Python", 2);
          map.put(null, 3);
          System.out.println(map); // Output: {null=3, Java=1, Python=2}
      }
  }
  ```

#### **4.2 TreeMap**
- **Description**: Implements a sorted map using a red-black tree.
- **Key Features**:
  - Maintains keys in natural or custom order.
  - Does not allow `null` keys (throws `NullPointerException`).
- **Use Case**: Key-value pairs where keys need to be sorted.
- **Example**:
  ```java
  import java.util.TreeMap;

  public class Main {
      public static void main(String[] args) {
          TreeMap<String, Integer> map = new TreeMap<>();
          map.put("C", 3);
          map.put("A", 1);
          map.put("B", 2);
          System.out.println(map); // Output: {A=1, B=2, C=3}
      }
  }
  ```

---

### **5. Comparison of Set and Map Implementations**

| Feature              | **HashSet**         | **TreeSet**         | **HashMap**          | **TreeMap**          |
|----------------------|---------------------|---------------------|----------------------|----------------------|
| **Ordering**         | No order            | Sorted (natural/custom) | No order             | Sorted (natural/custom) |
| **Duplicates**       | No                  | No                  | Keys: No, Values: Yes | Keys: No, Values: Yes |
| **Null Handling**    | One `null` value    | No `null` values    | One `null` key, multiple `null` values | No `null` keys, allows `null` values |
| **Performance**      | O(1) operations     | O(log n) operations | O(1) operations      | O(log n) operations  |

---

### **6. Iteration Techniques**

1. **Iterating Over a Set**:
   - Using an enhanced `for` loop:
     ```java
     for (String element : set) {
         System.out.println(element);
     }
     ```
   - Using an `Iterator`:
     ```java
     Iterator<String> iterator = set.iterator();
     while (iterator.hasNext()) {
         System.out.println(iterator.next());
     }
     ```

2. **Iterating Over a Map**:
   - Using `keySet` and `entrySet`:
     ```java
     for (Map.Entry<String, Integer> entry : map.entrySet()) {
         System.out.println(entry.getKey() + ": " + entry.getValue());
     }
     ```

---

### **7. Utility Methods in Collections**

Java provides utility methods in the `Collections` class for working with sets and maps.

| Method                           | Description                                      |
|----------------------------------|--------------------------------------------------|
| `Collections.unmodifiableSet()`  | Returns an unmodifiable view of a set.          |
| `Collections.unmodifiableMap()`  | Returns an unmodifiable view of a map.          |
| `Collections.synchronizedSet()`  | Returns a synchronized (thread-safe) set.       |
| `Collections.synchronizedMap()`  | Returns a synchronized (thread-safe) map.       |

---

### **8. Use Cases**

- **HashSet**: Storing unique usernames or IDs without worrying about order.
- **TreeSet**: Maintaining a sorted set of unique items like dates or scores.
- **HashMap**: Fast lookups for storing configuration settings or a cache.
- **TreeMap**: Key-value pairs where keys need to be sorted, such as a phone book.

---

### **9. Summary**
- **Sets** ensure unique elements, while **Maps** associate keys with values.
- Use `HashSet` and `HashMap` for fast operations without ordering.
- Use `TreeSet` and `TreeMap` when sorting is essential.

---