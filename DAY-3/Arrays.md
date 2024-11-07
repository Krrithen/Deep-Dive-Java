## Day 3: Arrays in Java - Basics, Types, and Manipulation

#### **Overview of Arrays in Java**
An **array** is a collection of elements, all of the same type, stored in a contiguous memory location. Arrays in Java are objects that store multiple values, and they offer an efficient way to manage and manipulate groups of related data.

#### **Key Characteristics of Arrays**
1. **Fixed Size**: Once created, the size of an array is fixed. You cannot resize it.
2. **Zero-Based Indexing**: The first element is accessed with index `0`, the second with `1`, and so on.
3. **Homogeneous Data Type**: All elements in an array must be of the same type.
4. **Memory Efficiency**: Arrays provide fast access to elements due to their contiguous memory allocation.
5. **Single and Multidimensional Support**: Java supports both 1D and multidimensional arrays (like 2D arrays).

---

### **Types of Arrays in Java**

#### **1. One-Dimensional (1D) Array**
A one-dimensional array is a linear array where elements are stored in a single row.

**Syntax**:
```java
type[] arrayName = new type[size];
```

**Example**:
```java
int[] numbers = new int[5];  // Declaration of an integer array with 5 elements
```

**Initialization with Values**:
```java
int[] numbers = {10, 20, 30, 40, 50};  // Initializes an array with specific values
```

**Accessing Array Elements**:
Use the index to access each element.
```java
System.out.println(numbers[0]);  // Output: 10
```

**Modifying Elements**:
```java
numbers[1] = 25;  // Sets the second element to 25
```

#### **2. Two-Dimensional (2D) Array**
A two-dimensional array is essentially an array of arrays, often used for matrices or tabular data.

**Syntax**:
```java
type[][] arrayName = new type[rows][columns];
```

**Example**:
```java
int[][] matrix = new int[3][3];  // Declaration of a 3x3 matrix
```

**Initialization with Values**:
```java
int[][] matrix = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};
```

**Accessing Elements**:
```java
System.out.println(matrix[0][1]);  // Accesses element in the first row, second column, Output: 2
```

#### **3. Jagged Arrays (Array of Arrays)**
Jagged arrays allow rows of different lengths, unlike regular 2D arrays where each row must have the same number of columns.

**Syntax**:
```java
type[][] arrayName = new type[rows][];
```

**Example**:
```java
int[][] jaggedArray = new int[3][];
jaggedArray[0] = new int[2];  // First row has 2 columns
jaggedArray[1] = new int[3];  // Second row has 3 columns
jaggedArray[2] = new int[4];  // Third row has 4 columns
```

---

### **Basic Operations on Arrays**

#### **1. Traversing an Array**
To process each element in an array, you can use loops.

**Using a `for` loop**:
```java
int[] numbers = {10, 20, 30, 40, 50};
for (int i = 0; i < numbers.length; i++) {
    System.out.println(numbers[i]);
}
```

**Using an Enhanced `for` loop**:
```java
for (int num : numbers) {
    System.out.println(num);
}
```

#### **2. Array Length**
To find the number of elements in an array, use the `.length` property.

```java
int[] numbers = {10, 20, 30};
System.out.println(numbers.length);  // Output: 3
```

#### **3. Copying Arrays**
Java provides multiple ways to copy arrays:

- **Using `System.arraycopy()`**:
  ```java
  int[] source = {1, 2, 3};
  int[] destination = new int[3];
  System.arraycopy(source, 0, destination, 0, source.length);
  ```

- **Using `Arrays.copyOf()`**:
  ```java
  int[] copy = Arrays.copyOf(source, source.length);
  ```

#### **4. Multi-Dimensional Array Traversal**
For 2D arrays, use nested loops to traverse and access elements.

```java
int[][] matrix = {
    {1, 2, 3},
    {4, 5, 6}
};
for (int i = 0; i < matrix.length; i++) {
    for (int j = 0; j < matrix[i].length; j++) {
        System.out.println(matrix[i][j]);
    }
}
```

---

## **Array Utility Methods in `java.util.Arrays`**

#### **1. `Arrays.sort()`**
Sorts the elements of an array into ascending order.

- **Syntax**:
  ```java
  Arrays.sort(array);
  ```
- **Example**:
  ```java
  int[] numbers = {5, 2, 8, 1, 3};
  Arrays.sort(numbers);  // Sorted array: {1, 2, 3, 5, 8}
  ```

#### **2. `Arrays.binarySearch()`**
Performs a binary search on a sorted array to find the index of a specified element.

- **Syntax**:
  ```java
  int index = Arrays.binarySearch(array, value);
  ```
- **Example**:
  ```java
  int[] numbers = {1, 2, 3, 5, 8};
  int index = Arrays.binarySearch(numbers, 5);  // Output: 3
  ```
  > **Note**: The array must be sorted for binary search to work correctly.

#### **3. `Arrays.copyOf()`**
Creates a new array by copying the specified elements of an existing array.

- **Syntax**:
  ```java
  int[] newArray = Arrays.copyOf(originalArray, newLength);
  ```
- **Example**:
  ```java
  int[] numbers = {1, 2, 3};
  int[] copy = Arrays.copyOf(numbers, 5);  // Output: {1, 2, 3, 0, 0}
  ```
  > If the new length is larger, the extra elements are initialized to the default value (e.g., `0` for `int`).

#### **4. `Arrays.copyOfRange()`**
Copies a range of elements from one array to another.

- **Syntax**:
  ```java
  int[] subArray = Arrays.copyOfRange(array, fromIndex, toIndex);
  ```
- **Example**:
  ```java
  int[] numbers = {1, 2, 3, 4, 5};
  int[] subArray = Arrays.copyOfRange(numbers, 1, 4);  // Output: {2, 3, 4}
  ```
  > The `fromIndex` is inclusive, and `toIndex` is exclusive.

#### **5. `Arrays.equals()`**
Compares two arrays for equality, checking if both arrays contain the same elements in the same order.

- **Syntax**:
  ```java
  boolean isEqual = Arrays.equals(array1, array2);
  ```
- **Example**:
  ```java
  int[] array1 = {1, 2, 3};
  int[] array2 = {1, 2, 3};
  boolean isEqual = Arrays.equals(array1, array2);  // Output: true
  ```

#### **6. `Arrays.fill()`**
Fills all or part of an array with a specified value.

- **Syntax**:
  ```java
  Arrays.fill(array, value);
  Arrays.fill(array, fromIndex, toIndex, value);
  ```
- **Example**:
  ```java
  int[] numbers = new int[5];
  Arrays.fill(numbers, 1);  // All elements set to 1: {1, 1, 1, 1, 1}
  Arrays.fill(numbers, 2, 4, 8);  // Partial fill: {1, 1, 8, 8, 1}
  ```

#### **7. `Arrays.toString()`**
Returns a string representation of an array, which is especially useful for printing arrays.

- **Syntax**:
  ```java
  String arrayString = Arrays.toString(array);
  ```
- **Example**:
  ```java
  int[] numbers = {1, 2, 3};
  System.out.println(Arrays.toString(numbers));  // Output: [1, 2, 3]
  ```

#### **8. `Arrays.deepToString()`**
Returns a string representation of a multidimensional array (such as a 2D array).

- **Syntax**:
  ```java
  String arrayString = Arrays.deepToString(multidimensionalArray);
  ```
- **Example**:
  ```java
  int[][] matrix = {{1, 2}, {3, 4}};
  System.out.println(Arrays.deepToString(matrix));  // Output: [[1, 2], [3, 4]]
  ```

#### **9. `Arrays.asList()`**
Converts an array into a fixed-size `List` that is backed by the array. This can be useful when you need to work with collections.

- **Syntax**:
  ```java
  List<Type> list = Arrays.asList(array);
  ```
- **Example**:
  ```java
  String[] array = {"apple", "banana", "cherry"};
  List<String> list = Arrays.asList(array);
  ```

#### **10. `Arrays.hashCode()`**
Computes a hash code for an array, based on its contents.

- **Syntax**:
  ```java
  int hash = Arrays.hashCode(array);
  ```
- **Example**:
  ```java
  int[] numbers = {1, 2, 3};
  int hash = Arrays.hashCode(numbers);
  ```

#### **11. `Arrays.deepEquals()`**
Compares two multidimensional arrays for equality, useful for 2D and higher-dimensional arrays.

- **Syntax**:
  ```java
  boolean isEqual = Arrays.deepEquals(array1, array2);
  ```
- **Example**:
  ```java
  int[][] array1 = {{1, 2}, {3, 4}};
  int[][] array2 = {{1, 2}, {3, 4}};
  boolean isEqual = Arrays.deepEquals(array1, array2);  // Output: true
  ```

---

### **Summary of `java.util.Arrays` Utility Methods**
The `java.util.Arrays` class offers a variety of methods that make common array tasks easier:

- **Sorting and Searching**: `sort()`, `binarySearch()`
- **Copying**: `copyOf()`, `copyOfRange()`
- **Comparing**: `equals()`, `deepEquals()`
- **Filling**: `fill()`
- **String Conversion**: `toString()`, `deepToString()`
- **Conversion to List**: `asList()`
- **Hashing**: `hashCode()`

These methods make working with arrays simpler and more efficient, allowing you to focus on your code logic rather than implementing basic array functions manually.

---

### **Advanced Array Concepts**

#### **1. Array as a Parameter**
Arrays can be passed to methods as arguments.

```java
public static void printArray(int[] array) {
    for (int element : array) {
        System.out.println(element);
    }
}
```

#### **2. Returning an Array from a Method**
A method can return an array.

```java
public static int[] getArray() {
    return new int[] {1, 2, 3};
}
```

#### **3. Variable-Length Argument Lists (`varargs`)**
Java supports variable-length arguments, allowing you to pass a varying number of arguments to a method.

```java
public static void printNumbers(int... numbers) {
    for (int num : numbers) {
        System.out.println(num);
    }
}
```

#### **4. Cloning Arrays**
`clone()` creates a new array that is a copy of the original.

```java
int[] numbers = {1, 2, 3};
int[] copy = numbers.clone();
```

---

### **Common Pitfalls and Tips**

- **ArrayIndexOutOfBoundsException**: Attempting to access an index outside the array’s range will throw this exception.
- **Default Values**: Uninitialized array elements have default values (e.g., `0` for int, `null` for objects).
- **Using `Arrays.toString()`**: This method provides a human-readable format for arrays, making it easier to print their contents.

**Example**:
```java
int[] numbers = {1, 2, 3};
System.out.println(Arrays.toString(numbers));  // Output: [1, 2, 3]
```

---

### **Summary**

1. **Arrays are fixed-size data structures** for storing elements of the same type.
2. **Types of Arrays**: One-dimensional, two-dimensional, and jagged arrays.
3. **Key operations** include traversing, sorting, searching, filling, and copying arrays.
4. **Methods for manipulation**: Use methods in the `Arrays` class for common array tasks like sorting, searching, and comparing.
5. **Memory Management**: Arrays are efficient in memory usage but require careful management to avoid bounds errors.

---