### **Day 12: Multithreading Basics in Java**

---

### **1. What is Multithreading?**

Multithreading is the ability of a CPU to execute multiple threads simultaneously. In Java:
- A **thread** is the smallest unit of a process that can execute concurrently.
- Multithreading allows a program to perform multiple tasks concurrently within a single process.

#### **Key Benefits of Multithreading**:
1. **Efficient CPU Utilization**: Maximizes CPU usage by running multiple threads simultaneously.
2. **Concurrency**: Enables non-blocking operations (e.g., handling I/O and computations at the same time).
3. **Responsiveness**: Keeps applications responsive by running time-consuming tasks in the background.

---

### **2. Java Thread Basics**

In Java, the **`Thread` class** and **`Runnable` interface** are the core components for creating threads.

---

### **3. Creating Threads**

#### **3.1 Using the `Thread` Class**

You can create a thread by extending the `Thread` class and overriding its `run()` method.

#### **Example**:
```java
class MyThread extends Thread {
    @Override
    public void run() {
        System.out.println("Thread is running: " + Thread.currentThread().getName());
    }
}

public class Main {
    public static void main(String[] args) {
        MyThread thread = new MyThread();
        thread.start(); // Start the thread
    }
}
```

#### **Key Methods of `Thread` Class**:
| Method               | Description                                                                 |
|----------------------|-----------------------------------------------------------------------------|
| `start()`            | Starts the thread; calls the `run()` method internally.                    |
| `run()`              | Contains the code to be executed by the thread.                            |
| `getName()`          | Returns the name of the thread.                                            |
| `setName(String)`    | Sets the name of the thread.                                               |
| `sleep(milliseconds)`| Pauses the thread for the specified time.                                  |
| `join()`             | Waits for the thread to finish before proceeding.                          |
| `isAlive()`          | Checks if the thread is still running.                                     |

---

#### **3.2 Using the `Runnable` Interface**

Another way to create threads is by implementing the `Runnable` interface.

#### **Example**:
```java
class MyRunnable implements Runnable {
    @Override
    public void run() {
        System.out.println("Thread is running: " + Thread.currentThread().getName());
    }
}

public class Main {
    public static void main(String[] args) {
        Thread thread = new Thread(new MyRunnable());
        thread.start(); // Start the thread
    }
}
```

#### **Difference Between `Thread` and `Runnable`**:
- **`Thread`**: Extending `Thread` restricts your class from extending any other class.
- **`Runnable`**: Implementing `Runnable` is preferred for more flexible and reusable code.

---

### **4. Thread States (Life Cycle)**

A thread can exist in one of the following states:

| State               | Description                                                                 |
|---------------------|-----------------------------------------------------------------------------|
| **New**             | Created but not started.                                                   |
| **Runnable**        | Ready to run but waiting for CPU allocation.                               |
| **Running**         | Currently executing.                                                       |
| **Blocked/Waiting** | Waiting for resources or another thread's signal.                          |
| **Terminated**      | Finished execution.                                                        |

---

### **5. Thread Synchronization**

#### **Problem: Race Condition**
- When multiple threads access shared resources, inconsistency may occur.

#### **Solution: Synchronization**
- Synchronization ensures only one thread accesses the resource at a time.

#### **Using `synchronized` Keyword**:
1. **Method Synchronization**:
   ```java
   public synchronized void display() {
       System.out.println("Synchronized method");
   }
   ```

2. **Block Synchronization**:
   ```java
   public void display() {
       synchronized (this) {
           System.out.println("Synchronized block");
       }
   }
   ```

---

#### **Example: Without Synchronization**
```java
class Counter {
    private int count = 0;

    public void increment() {
        count++; // Not thread-safe
    }

    public int getCount() {
        return count;
    }
}

public class Main {
    public static void main(String[] args) {
        Counter counter = new Counter();

        Thread t1 = new Thread(() -> {
            for (int i = 0; i < 1000; i++) counter.increment();
        });

        Thread t2 = new Thread(() -> {
            for (int i = 0; i < 1000; i++) counter.increment();
        });

        t1.start();
        t2.start();

        try {
            t1.join();
            t2.join();
        } catch (InterruptedException e) {
            e.printStackTrace();
        }

        System.out.println("Count: " + counter.getCount()); // Output may be inconsistent
    }
}
```

#### **Example: With Synchronization**
```java
class Counter {
    private int count = 0;

    public synchronized void increment() {
        count++; // Thread-safe
    }

    public int getCount() {
        return count;
    }
}

public class Main {
    public static void main(String[] args) {
        Counter counter = new Counter();

        Thread t1 = new Thread(() -> {
            for (int i = 0; i < 1000; i++) counter.increment();
        });

        Thread t2 = new Thread(() -> {
            for (int i = 0; i < 1000; i++) counter.increment();
        });

        t1.start();
        t2.start();

        try {
            t1.join();
            t2.join();
        } catch (InterruptedException e) {
            e.printStackTrace();
        }

        System.out.println("Count: " + counter.getCount()); // Always 2000
    }
}
```

---

### **6. Thread Communication**

Threads can communicate with each other using the following methods in the `Object` class:
| Method             | Description                                                                 |
|--------------------|-----------------------------------------------------------------------------|
| `wait()`           | Causes the thread to wait until it is notified.                            |
| `notify()`         | Wakes up a single waiting thread.                                          |
| `notifyAll()`      | Wakes up all waiting threads.                                              |

#### **Example**:
```java
class SharedResource {
    private boolean available = false;

    public synchronized void produce() {
        try {
            while (available) {
                wait(); // Wait until consumed
            }
            System.out.println("Produced");
            available = true;
            notify(); // Notify consumer
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
    }

    public synchronized void consume() {
        try {
            while (!available) {
                wait(); // Wait until produced
            }
            System.out.println("Consumed");
            available = false;
            notify(); // Notify producer
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
    }
}

public class Main {
    public static void main(String[] args) {
        SharedResource resource = new SharedResource();

        Thread producer = new Thread(resource::produce);
        Thread consumer = new Thread(resource::consume);

        producer.start();
        consumer.start();
    }
}
```

---

### **7. Daemon Threads**

- Daemon threads are background threads (e.g., garbage collection).
- They stop automatically when all non-daemon threads complete.

#### **Example**:
```java
public class Main {
    public static void main(String[] args) {
        Thread daemonThread = new Thread(() -> {
            while (true) {
                System.out.println("Daemon thread running...");
            }
        });

        daemonThread.setDaemon(true);
        daemonThread.start();

        System.out.println("Main thread ending...");
    }
}
```

---

### **8. Best Practices**

1. Use **ExecutorService** for managing threads in large applications.
2. Avoid thread starvation and deadlocks.
3. Always handle exceptions within threads using try-catch blocks.
4. Use synchronization only when necessary to avoid performance bottlenecks.
5. Leverage **concurrent utilities** like `java.util.concurrent`.

---