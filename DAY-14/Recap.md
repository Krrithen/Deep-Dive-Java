### **Day 14: Review of Arrays, Strings, and Week 1 & 2 Concepts**

---

### **1. Arrays in Detail**

#### **1.1 Key Properties**
- **Fixed size**: The size of an array is determined at the time of creation and cannot be changed.
- **Indexed-based access**: Elements are accessed via a zero-based index.
- **Type safety**: All elements in an array must be of the same type.
- Default values:
  - Numeric types: `0`
  - Boolean: `false`
  - Objects: `null`

---

#### **1.2 Advanced Operations**

##### **Cloning an Array**
- Cloning creates a shallow copy of the array. For primitive arrays, this behaves like a full copy.
  ```java
  int[] original = {1, 2, 3};
  int[] clone = original.clone();
  System.out.println(Arrays.equals(original, clone)); // true
  ```

##### **Multidimensional Arrays**
- Java does not enforce uniform lengths for inner arrays (i.e., jagged arrays).
  ```java
  int[][] jaggedArray = new int[2][];
  jaggedArray[0] = new int[]{1, 2};
  jaggedArray[1] = new int[]{3, 4, 5};
  ```

##### **Array Copying**
- Use `System.arraycopy` for performance over manual iteration:
  ```java
  int[] source = {1, 2, 3, 4};
  int[] dest = new int[4];
  System.arraycopy(source, 0, dest, 0, source.length);
  System.out.println(Arrays.toString(dest)); // Output: [1, 2, 3, 4]
  ```

---

#### **1.3 Key Utility Methods**

| **Utility Method**           | **Explanation**                                | **Example**                                       |
|------------------------------|-----------------------------------------------|--------------------------------------------------|
| `Arrays.copyOf()`            | Returns a copy of an array.                   | `int[] newArr = Arrays.copyOf(arr, arr.length);` |
| `Arrays.parallelSort()`      | Uses multithreading to sort large arrays.     | `Arrays.parallelSort(arr);`                      |
| `Arrays.mismatch()`          | Returns the first differing index of two arrays. | `int index = Arrays.mismatch(arr1, arr2);`    |

---

#### **1.4 Practical Example**
**Problem**: Rotate an array to the right by `k` steps.
```java
int[] nums = {1, 2, 3, 4, 5};
int k = 2;
k = k % nums.length; // Handle k > length
System.arraycopy(nums, nums.length - k, nums, 0, k);
System.arraycopy(nums, 0, nums, k, nums.length - k);
System.out.println(Arrays.toString(nums)); // Output: [4, 5, 1, 2, 3]
```

---

### **2. Strings in Detail**

#### **2.1 Immutable Nature**
- Strings are immutable in Java, meaning any modification results in a new string.
- Why immutability matters:
  - Thread safety: Multiple threads can share the same `String` instance.
  - Security: Prevents accidental or malicious modification.

---

#### **2.2 Performance: String vs. StringBuilder vs. StringBuffer**
| **Aspect**        | **String**           | **StringBuilder**          | **StringBuffer**           |
|-------------------|----------------------|----------------------------|----------------------------|
| Immutability      | Immutable            | Mutable                    | Mutable                    |
| Thread-safety     | Yes                  | No                         | Yes                        |
| Performance       | Slow (due to new instances) | Fast (single-threaded)  | Moderate (thread-safe)     |

---

#### **2.3 Common Regular Expression Patterns**
- Match email:
  ```java
  String regex = "^[A-Za-z0-9+_.-]+@(.+)$";
  System.out.println("test@gmail.com".matches(regex)); // true
  ```
- Extract digits:
  ```java
  String input = "Order ID: 12345";
  String digits = input.replaceAll("\\D+", "");
  System.out.println(digits); // Output: 12345
  ```

---

#### **2.4 Examples**

**Problem**: Check if a string is a palindrome.
```java
String str = "racecar";
boolean isPalindrome = str.equals(new StringBuilder(str).reverse().toString());
System.out.println(isPalindrome); // true
```

**Problem**: Count vowels and consonants.
```java
String input = "Hello, World!";
int vowels = 0, consonants = 0;
for (char c : input.toLowerCase().toCharArray()) {
    if ("aeiou".indexOf(c) != -1) vowels++;
    else if (Character.isLetter(c)) consonants++;
}
System.out.println("Vowels: " + vowels + ", Consonants: " + consonants);
```

---

### **3. Collections Framework**

#### **3.1 Advanced Operations on Lists**

##### **List Iteration**
- Using `ListIterator` for bidirectional traversal:
  ```java
  List<String> list = Arrays.asList("A", "B", "C");
  ListIterator<String> it = list.listIterator();
  while (it.hasNext()) {
      System.out.println(it.next());
  }
  ```

##### **Modifying Lists**
- Safe removal during iteration:
  ```java
  list.removeIf(e -> e.equals("A"));
  ```

---

#### **3.2 Common Set and Map Examples**

##### **Set Operations**
- Find union and intersection:
  ```java
  Set<Integer> set1 = new HashSet<>(Arrays.asList(1, 2, 3));
  Set<Integer> set2 = new HashSet<>(Arrays.asList(2, 3, 4));
  set1.addAll(set2); // Union
  set1.retainAll(set2); // Intersection
  ```

##### **Map Advanced Usage**
- Iterating through a `Map`:
  ```java
  for (Map.Entry<String, Integer> entry : map.entrySet()) {
      System.out.println(entry.getKey() + ": " + entry.getValue());
  }
  ```

- Sorting a map by values:
  ```java
  map.entrySet()
     .stream()
     .sorted(Map.Entry.comparingByValue())
     .forEach(e -> System.out.println(e.getKey() + ": " + e.getValue()));
  ```

---

### **4. Combining Arrays, Strings, and Collections**

**Problem**: Given a list of strings, find the most frequent word.
```java
List<String> words = Arrays.asList("apple", "banana", "apple", "orange");
Map<String, Integer> frequency = new HashMap<>();
for (String word : words) {
    frequency.put(word, frequency.getOrDefault(word, 0) + 1);
}
String mostFrequent = Collections.max(frequency.entrySet(), Map.Entry.comparingByValue()).getKey();
System.out.println(mostFrequent); // Output: apple
```

---

### **5. Best Practices**

1. Use **`StringBuilder`** for string manipulation in loops.
2. Use **`Collections`** utility methods (e.g., `Collections.sort`) for enhanced readability and efficiency.
3. Prefer **streams** and **lambdas** for functional programming tasks.

---