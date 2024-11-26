### **Day 13: Java Stream API and Functional Programming**

---

Java's Stream API and functional programming capabilities, introduced in **Java 8**, revolutionized data manipulation by providing a declarative approach to processing collections. This enables concise, readable, and functional-style code.

---

### **1. What is the Stream API?**

A **Stream** is a sequence of elements from a source that supports **aggregate operations** (e.g., filtering, mapping, reducing).  
Streams provide a way to perform complex data transformations and computations in a functional style.

---

### **2. Key Features of Streams**
- **Declarative**: Focuses on *what* to do instead of *how* to do it.
- **Laziness**: Operations are evaluated only when necessary.
- **Pipelining**: Allows chaining multiple operations without intermediate steps.
- **Parallelism**: Supports parallel processing to leverage multi-core CPUs.

---

### **3. Stream Lifecycle**

1. **Source**: A stream is created from a data source (collections, arrays, or I/O channels).
2. **Intermediate Operations**: Transform the stream into another stream (e.g., `filter`, `map`).
3. **Terminal Operations**: Produce a result or side-effect (e.g., `forEach`, `collect`).

---

### **4. Functional Programming in Java**

Functional programming focuses on using functions as first-class citizens, emphasizing immutability and avoiding state changes.

#### **Key Concepts**:
1. **Lambda Expressions**: Compact representations of anonymous functions.
2. **Method References**: Shorthand for calling methods.
3. **Functional Interfaces**: Interfaces with a single abstract method (e.g., `Predicate`, `Function`).

#### **Example of Lambda Expressions**:
```java
// Traditional
Comparator<Integer> comparator = new Comparator<Integer>() {
    @Override
    public int compare(Integer o1, Integer o2) {
        return o1.compareTo(o2);
    }
};

// With Lambda
Comparator<Integer> comparatorLambda = (o1, o2) -> o1.compareTo(o2);
```

---

### **5. Creating Streams**

#### **From Collections**:
```java
List<String> names = Arrays.asList("Alice", "Bob", "Charlie");
Stream<String> stream = names.stream();
```

#### **From Arrays**:
```java
String[] array = {"one", "two", "three"};
Stream<String> stream = Arrays.stream(array);
```

#### **From Static Methods**:
```java
Stream<Integer> stream = Stream.of(1, 2, 3, 4, 5);
```

#### **Infinite Streams**:
```java
Stream<Integer> infinite = Stream.iterate(0, n -> n + 2);
infinite.limit(5).forEach(System.out::println); // Output: 0, 2, 4, 6, 8
```

---

### **6. Stream Operations**

#### **6.1 Intermediate Operations**:
| Operation      | Description                                           | Example |
|----------------|-------------------------------------------------------|---------|
| `filter`       | Filters elements based on a condition.               | `stream.filter(x -> x > 10)` |
| `map`          | Transforms each element into another.                | `stream.map(String::toUpperCase)` |
| `flatMap`      | Flattens nested structures (e.g., lists of lists).    | `stream.flatMap(Collection::stream)` |
| `distinct`     | Removes duplicates.                                  | `stream.distinct()` |
| `sorted`       | Sorts elements.                                      | `stream.sorted()` |
| `limit`        | Limits the number of elements.                       | `stream.limit(3)` |
| `skip`         | Skips the first `n` elements.                        | `stream.skip(2)` |

#### **6.2 Terminal Operations**:
| Operation      | Description                                           | Example |
|----------------|-------------------------------------------------------|---------|
| `forEach`      | Iterates through elements.                           | `stream.forEach(System.out::println)` |
| `collect`      | Collects elements into a collection or string.       | `stream.collect(Collectors.toList())` |
| `reduce`       | Combines elements into a single result.              | `stream.reduce(0, Integer::sum)` |
| `count`        | Counts the number of elements.                       | `stream.count()` |
| `anyMatch`     | Returns `true` if any element matches the predicate. | `stream.anyMatch(x -> x > 10)` |
| `allMatch`     | Returns `true` if all elements match the predicate.  | `stream.allMatch(x -> x > 0)` |
| `noneMatch`    | Returns `true` if no elements match the predicate.   | `stream.noneMatch(x -> x < 0)` |

---

### **7. Example: Stream Operations**

#### **Filter and Map Example**:
```java
List<String> names = Arrays.asList("Alice", "Bob", "Charlie", "David");

// Filter names starting with 'A' and convert to uppercase
List<String> result = names.stream()
                           .filter(name -> name.startsWith("A"))
                           .map(String::toUpperCase)
                           .collect(Collectors.toList());

System.out.println(result); // Output: [ALICE]
```

#### **FlatMap Example**:
```java
List<List<Integer>> nestedList = Arrays.asList(
    Arrays.asList(1, 2, 3),
    Arrays.asList(4, 5, 6)
);

List<Integer> flatList = nestedList.stream()
                                   .flatMap(List::stream)
                                   .collect(Collectors.toList());

System.out.println(flatList); // Output: [1, 2, 3, 4, 5, 6]
```

---

### **8. Collectors**

The **`Collectors`** utility class provides methods for collecting stream elements.

| Method                     | Description                                   | Example |
|----------------------------|-----------------------------------------------|---------|
| `toList()`                 | Converts to a `List`.                        | `stream.collect(Collectors.toList())` |
| `toSet()`                  | Converts to a `Set`.                         | `stream.collect(Collectors.toSet())` |
| `toMap()`                  | Converts to a `Map`.                         | `stream.collect(Collectors.toMap(k -> k, v -> v.length()))` |
| `joining()`                | Joins elements into a single `String`.       | `stream.collect(Collectors.joining(", "))` |
| `groupingBy()`             | Groups elements by a key.                    | `stream.collect(Collectors.groupingBy(String::length))` |
| `partitioningBy()`         | Partitions into two groups (predicate-based).| `stream.collect(Collectors.partitioningBy(x -> x > 10))` |

---

### **9. Parallel Streams**

Parallel streams divide tasks across multiple threads, making them faster for large data sets.

#### **Example**:
```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);

int sum = numbers.parallelStream()
                 .reduce(0, Integer::sum);

System.out.println("Sum: " + sum); // Output: 15
```

#### **Use Case**:
Use parallel streams for CPU-intensive operations, but avoid them for tasks with side effects or small data.

---

### **10. Best Practices**

1. Use **Streams** for readability and maintainability, but ensure it suits the use case.
2. Avoid mutating shared state inside streams.
3. Prefer **parallel streams** only when dealing with large datasets or computationally heavy tasks.
4. Combine **Streams** with functional interfaces like `Predicate` and `Function` for better modularity.

---