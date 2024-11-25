## Day 4: **Strings: Creation, Manipulation, and Common Methods.**

---

## **Key Topics for Day 4**
1. **Strings in Java**  
2. **String Immutability**  
3. **String Methods**  
4. **StringBuilder and StringBuffer**  
5. **Comparison of String, StringBuilder, and StringBuffer**  
6. **String Pool**  

---

### 1. **Strings in Java**
A string in Java is a sequence of characters, treated as an object of the `String` class.

**How to Create Strings:**
1. **Using String Literal:**
   ```java
   String str = "Hello";
   ```
   - Stored in the **String Pool** (part of the Heap Memory).

2. **Using the `new` Keyword:**
   ```java
   String str = new String("Hello");
   ```
   - Stored in the Heap Memory.

**Example:**
```java
public class StringExample {
    public static void main(String[] args) {
        String str1 = "Hello"; // Literal
        String str2 = new String("World"); // Object
        System.out.println(str1 + " " + str2); // Output: Hello World
    }
}
```

---

### 2. **String Immutability**
- Strings in Java are **immutable**, meaning once created, their values cannot be changed.
- Any operation like concatenation or replacement results in a new string being created.
- In Java, strings are immutable, meaning that once a String object is created, its contents cannot be changed. However, the reference variable that holds the String object can be reassigned to point to a different object.

**Example:**
```java
public class StringImmutable {
    public static void main(String[] args) {
        String s1 = "Hello";
        String s2 = s1.concat(" World");
        System.out.println(s1); // Output: Hello
        System.out.println(s2); // Output: Hello World
    }
}
```
- `s1` remains unchanged after `concat`.

**Why Strings are Immutable:**
1. **Thread-Safety:** Immutable objects are inherently thread-safe.
2. **Memory Optimization:** Allows sharing in the String Pool.
3. **Caching:** Strings are often used as keys in hashmaps. Immutability ensures consistent behavior.

---

### 3. **String Methods**
Java provides numerous built-in methods for string manipulation.

| **Method**                      | **Description**                                      | **Example**                                              |
|----------------------------------|------------------------------------------------------|----------------------------------------------------------|
| `length()`                      | Returns the length of the string                    | `"Hello".length()` → 5                                   |
| `charAt(index)`                 | Returns the character at the specified index        | `"Hello".charAt(1)` → 'e'                                |
| `substring(start, end)`         | Extracts a substring                                | `"Hello".substring(1, 4)` → "ell"                        |
| `str1.concat("str2")`         | Concats a string                                | `"Hello".concat(" world)` → "Hello world"                        |
| `indexOf(char)`                 | Returns the index of the first occurrence           | `"Hello".indexOf('l')` → 2                               |
| `lastIndexOf(char)`             | Returns the index of the last occurrence            | `"Hello".lastIndexOf('l')` → 3                           |
| `equals(str)`                   | Checks equality of content                          | `"Hello".equals("hello")` → false                        |
| `equalsIgnoreCase(str)`         | Checks equality, ignoring case                      | `"Hello".equalsIgnoreCase("hello")` → true               |
| `toUpperCase()`                 | Converts all characters to uppercase                | `"hello".toUpperCase()` → "HELLO"                        |
| `toLowerCase()`                 | Converts all characters to lowercase                | `"HELLO".toLowerCase()` → "hello"                        |
| `trim()`                        | Removes leading and trailing spaces                 | `"  Hello  ".trim()` → "Hello"                           |
| `replace(old, new)`             | Replaces occurrences of a character                 | `"Hello".replace('l', 'y')` → "Heyyo"                    |
| `split(regex)`                  | Splits the string into an array based on the regex  | `"a,b,c".split(",")` → ["a", "b", "c"]                   |
| `str.toCharArray()`                  | Splits the string into an char array  | `"abc".toCharArray()` → ["a", "b", "c"]                   |
| `str.getBytes()`                  | Splits the string into an Byte array  | `"hello".getBytes()` → [104 101 108 108 111]                   |

---

### 4. **StringBuilder and StringBuffer**
Both `StringBuilder` and `StringBuffer` are **mutable**, meaning they allow modification without creating a new object.

| Feature                  | `StringBuilder`               | `StringBuffer`                |
|--------------------------|-------------------------------|--------------------------------|
| Thread-Safety           | Not thread-safe               | Thread-safe (synchronized)    |
| Performance             | Faster                        | Slower due to synchronization |

**Common Methods:**
| Method                  | Description                          | Example                                         |
|-------------------------|--------------------------------------|------------------------------------------------|
| `append(String)`         | Adds text to the end                | `"Hello".append(" World")` → "Hello World"     |
| `insert(index, String)`  | Inserts text at a specific position | `"Hello".insert(1, "Java")` → "HJavaello"      |
| `delete(start, end)`     | Removes text within a range         | `"Hello".delete(1, 4)` → "Ho"                  |
| `reverse()`              | Reverses the string                 | `"Hello".reverse()` → "olleH"                  |

**Example:**
```java
public class StringBuilderExample {
    public static void main(String[] args) {
        StringBuilder sb = new StringBuilder("Hello");
        sb.append(" World");
        System.out.println(sb); // Output: Hello World
    }
}
```

---

### 5. **Comparison of String, StringBuilder, and StringBuffer**

| Feature           | String                | StringBuilder         | StringBuffer          |
|--------------------|-----------------------|-----------------------|-----------------------|
| **Mutability**     | Immutable             | Mutable               | Mutable               |
| **Thread-Safety**  | Thread-safe (due to immutability) | Not thread-safe      | Thread-safe           |
| **Performance**    | Slower (new object for each change) | Faster              | Slower (synchronized) |

---

### 6. **String Pool**
- The String Pool is a special area in the Heap Memory that stores string literals.
- Strings created using literals (`String str = "Hello";`) are stored in the pool.
- If a string with the same content already exists, the new reference points to the existing object.

**Example:**
```java
String s1 = "Hello";
String s2 = "Hello";
System.out.println(s1 == s2); // Output: true (both point to the same object)
```

---

### Code Example to Illustrate All Concepts
```java
public class StringDemo {
    public static void main(String[] args) {
        // String methods
        String s1 = " Hello Java ";
        System.out.println("Length: " + s1.length());
        System.out.println("Trimmed: " + s1.trim());
        System.out.println("Substring: " + s1.substring(1, 6));
        System.out.println("Replace: " + s1.replace('J', 'C'));
        
        // StringBuilder
        StringBuilder sb = new StringBuilder("Hello");
        sb.append(" World");
        sb.insert(6, "Java ");
        sb.delete(6, 11);
        sb.reverse();
        System.out.println("StringBuilder: " + sb);

        // Comparing Strings
        String str1 = "Hello";
        String str2 = new String("Hello");
        System.out.println("Equals: " + str1.equals(str2));
        System.out.println("==: " + (str1 == str2)); // False
    }
}
```

--- 

This covers everything you need for **Day 4**!