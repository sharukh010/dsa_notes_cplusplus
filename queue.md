### Queue and Its Operations Using C++ STL

A **queue** is a data structure that follows the First In, First Out (FIFO) principle. This means that the first element added to the queue is the first one to be removed. It’s similar to a line of people waiting for service: the person who comes first is the first one to be served.

#### **Real-Life Example:**
Imagine you are at a ticket counter where people are waiting in line to buy tickets. The person who arrives first gets their ticket first and leaves the queue. The next person in line moves up, and the process continues.

#### **Queue Operations Using C++ STL**

The C++ Standard Template Library (STL) provides a `queue` class that allows you to perform queue operations easily. Here’s how you can perform basic queue operations using the `queue` class.

1. **Creating a Queue:**
   - You can create a queue using the `queue` class provided by the STL.

   ```cpp
   #include <iostream>
   #include <queue>

   int main() {
       std::queue<int> ticketQueue;
       return 0;
   }
   ```

2. **Enqueue Operation (Push):**
   - The `push()` function is used to add an element to the back of the queue.
   
   ```cpp
   ticketQueue.push(1); // First person in line
   ticketQueue.push(2); // Second person in line
   ticketQueue.push(3); // Third person in line
   ```

   - **Real-Life Analogy:** Imagine people joining the end of the line one by one to buy tickets. The first person to join the line will be the first to be served.

3. **Dequeue Operation (Pop):**
   - The `pop()` function removes the front element from the queue, which is the first element that was added.
   
   ```cpp
   ticketQueue.pop(); // The first person gets their ticket and leaves the line
   ```

   - **Real-Life Analogy:** The person at the front of the line buys their ticket and leaves, allowing the next person in line to step forward.

4. **Front Operation:**
   - The `front()` function returns the element at the front of the queue without removing it.
   
   ```cpp
   int firstInLine = ticketQueue.front(); // Accessing the first person in line
   std::cout << "The first person in line is: " << firstInLine << std::endl;
   ```

   - **Real-Life Analogy:** You check to see who is currently at the front of the line without making them leave.

5. **Back Operation:**
   - The `back()` function returns the last element in the queue without removing it.
   
   ```cpp
   int lastInLine = ticketQueue.back(); // Accessing the last person in line
   std::cout << "The last person in line is: " << lastInLine << std::endl;
   ```

   - **Real-Life Analogy:** You check to see who is the last person in the line.

6. **Size Operation:**
   - The `size()` function returns the number of elements in the queue.

   ```cpp
   std::cout << "Number of people in the queue: " << ticketQueue.size() << std::endl;
   ```

   - **Real-Life Analogy:** You count how many people are currently in the line.

7. **Empty Operation:**
   - The `empty()` function checks if the queue is empty.

   ```cpp
   if (ticketQueue.empty()) {
       std::cout << "The queue is empty." << std::endl;
   } else {
       std::cout << "The queue is not empty." << std::endl;
   }
   ```

   - **Real-Life Analogy:** You check if there are any people left in the line.

#### **Putting It All Together:**

Here’s a simple C++ program demonstrating all the queue operations using the real-life analogy of people waiting in line to buy tickets:

```cpp
#include <iostream>
#include <queue>

int main() {
    std::queue<int> ticketQueue;

    // People joining the queue
    ticketQueue.push(1); // First person
    ticketQueue.push(2); // Second person
    ticketQueue.push(3); // Third person

    // Accessing the front and back of the queue
    std::cout << "The first person in line is: " << ticketQueue.front() << std::endl;
    std::cout << "The last person in line is: " << ticketQueue.back() << std::endl;

    // The first person gets their ticket and leaves
    ticketQueue.pop();
    std::cout << "After serving the first person, the next person in line is: " << ticketQueue.front() << std::endl;

    // Checking the size of the queue
    std::cout << "Number of people in the queue: " << ticketQueue.size() << std::endl;

    // Checking if the queue is empty
    if (ticketQueue.empty()) {
        std::cout << "The queue is empty." << std::endl;
    } else {
        std::cout << "The queue is not empty." << std::endl;
    }

    return 0;
}
```

#### **Explanation:**
- This program simulates a queue of people waiting to buy tickets. Each operation corresponds to an action you would take in real life when dealing with a line of people.
- The `push` operation adds people to the back of the queue, the `pop` operation removes the person at the front, and the `front` and `back` operations allow you to check who is at the front and back of the line, respectively.
- The `size` and `empty` operations help you keep track of how many people are in the line and whether the line is empty.

Using queues in programming is useful when you need to manage data that needs to be processed in a FIFO manner, such as handling tasks in a printer queue, managing processes in an operating system, or breadth-first search in graphs.