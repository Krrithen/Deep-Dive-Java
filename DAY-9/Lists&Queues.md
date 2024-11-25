### **Day 9: Lists and Queues in Java - ArrayList, LinkedList, and PriorityQueue**

---

#### **1. Lists in Java**

A `List` is an ordered collection (sequence) in Java. It:
- Maintains the insertion order of elements.
- Allows duplicate elements.
- Provides indexed access to elements for efficient retrieval and modification.

---

#### **1.1 Key Features of Lists**
- **Dynamic Resizing**: Grows as elements are added (unlike arrays).
- **Random Access**: Using indices, elements can be accessed efficiently.
- **Null Values**: Lists can store `null` values (unless restricted explicitly).

#### **1.2 Common Methods in the `List` Interface**
| **Method**           | **Description**                                                               |
|-----------------------|-------------------------------------------------------------------------------|
| `add(E e)`            | Appends the element to the list.                                             |
| `add(int index, E e)` | Inserts an element at the specified position.                                |
| `remove(int index)`   | Removes the element at the specified position.                               |
| `set(int index, E e)` | Replaces the element at the specified index with the given element.          |
| `get(int index)`      | Retrieves the element at the specified position.                             |
| `contains(Object o)`  | Checks if the list contains the specified element.                           |
| `size()`              | Returns the number of elements in the list.                                 |
| `clear()`             | Removes all elements from the list.                                         |
| `indexOf(Object o)`   | Returns the index of the first occurrence of the specified element.          |
| `subList(int from, int to)` | Returns a view of the portion of the list between `from` (inclusive) and `to` (exclusive). |

---

#### **2. Common List Implementations**

1. **ArrayList**:
   - Backed by a dynamically resizable array.
   - Best for frequent retrievals but slower for insertions/deletions in the middle.

   **Characteristics**:
   - Allows random access in O(1) time.
   - Not synchronized (not thread-safe).
   - Example:
     ```java
     import java.util.ArrayList;

     public class Main {
         public static void main(String[] args) {
             ArrayList<String> list = new ArrayList<>();
             list.add("Java");
             list.add("Python");
             list.add("C++");
             list.remove("Python");
             System.out.println(list); // Output: [Java, C++]
         }
     }
     ```

2. **LinkedList**:
   - Backed by a doubly-linked list (each element points to its previous and next nodes).
   - Best for frequent insertions and deletions.

   **Characteristics**:
   - Sequential access is O(n).
   - Implements both `List` and `Deque` interfaces (can be used as a stack, queue, or deque).
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

#### **3. Queues in Java**

A `Queue` is a collection designed for holding elements before processing, following specific ordering rules:
- **FIFO (First-In-First-Out)**: Elements are processed in the order they were added.
- Some implementations prioritize elements based on a comparator.

---

#### **3.1 Key Features of Queues**
- **Head**: The element that will be removed next.
- **Tail**: The element that was added last.
- **Priority**: Some queues (like `PriorityQueue`) prioritize elements differently.

#### **3.2 Common Methods in the `Queue` Interface**
| **Method**         | **Description**                                                                 |
|---------------------|---------------------------------------------------------------------------------|
| `add(E e)`          | Adds the element to the queue, throws an exception if the queue is full.       |
| `offer(E e)`        | Adds the element to the queue, returns `false` if the queue is full.           |
| `remove()`          | Retrieves and removes the head of the queue, throws an exception if empty.     |
| `poll()`            | Retrieves and removes the head of the queue, returns `null` if empty.          |
| `element()`         | Retrieves (but does not remove) the head, throws an exception if empty.        |
| `peek()`            | Retrieves (but does not remove) the head, returns `null` if empty.             |

---

#### **4. Common Queue Implementations**

1. **PriorityQueue**:
   - Elements are ordered based on their *natural order* or a custom comparator.
   - **Key Features**:
     - Not thread-safe.
     - Allows `null` values.
   - **Use Case**: Task scheduling, event prioritization.
   - **Example**:
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

2. **ArrayDeque**:
   - A double-ended queue (deque) allowing efficient addition and removal from both ends.
   - **Key Features**:
     - Faster than `LinkedList` for stack and queue operations.
     - No capacity restriction.
   - **Use Case**: Implementing stacks, queues, and deques.
   - **Example**:
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

#### **5. Comparison of List and Queue Implementations**

| **Feature**           | **ArrayList**                 | **LinkedList**                 | **PriorityQueue**            | **ArrayDeque**              |
|------------------------|-------------------------------|--------------------------------|------------------------------|-----------------------------|
| **Ordering**           | Maintains insertion order.    | Maintains insertion order.     | Natural/custom priority.     | Maintains insertion order.  |
| **Duplicates**         | Allowed.                     | Allowed.                      | Allowed.                     | Allowed.                    |
| **Null Values**        | Allowed.                     | Allowed.                      | Allowed.                     | Not allowed.                |
| **Access Speed**       | Fast random access.           | Slower random access.          | N/A (priority-based).        | Fast sequential access.     |
| **Insertion/Deletion** | Slower in middle operations.  | Faster anywhere.               | N/A (priority-based).        | Fast at both ends.          |

---

#### **6. Utility Methods for Lists and Queues**

The `Collections` utility class provides various operations to work with lists and queues effectively.

| **Method**              | **Description**                                                    |
|--------------------------|--------------------------------------------------------------------|
| `Collections.sort()`     | Sorts the list elements in natural order.                         |
| `Collections.reverse()`  | Reverses the order of elements in a list.                         |
| `Collections.shuffle()`  | Randomly shuffles the elements in a list.                         |
| `Collections.binarySearch()` | Searches for a key in a sorted list.                         |

**Example**:
```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        List<Integer> list = Arrays.asList(5, 3, 8, 1);
        Collections.sort(list);
        System.out.println(list); // Output: [1, 3, 5, 8]
        int index = Collections.binarySearch(list, 5);
        System.out.println(index); // Output: 2
    }
}
```

---

#### **7. Summary**
- **Lists** (`ArrayList`, `LinkedList`) are ideal for storing ordered collections with frequent retrievals or modifications.
- **Queues** (`PriorityQueue`, `ArrayDeque`) are best suited for task scheduling or FIFO-based processing.
- Choosing the correct implementation depends on your use case: whether you prioritize speed, memory efficiency, or specific functionality like sorting or prioritization.

---