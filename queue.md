Here are notes on using queues in C++ with the STL library:

---

### **Queue in C++ (STL Library)**

**Introduction:**
A queue is a data structure that follows the First-In-First-Out (FIFO) principle. Elements are inserted at the back (enqueue) and removed from the front (dequeue). It is useful in scenarios like managing tasks in order or simulating real-world queues like people waiting in line.

**Syntax Overview:**

```cpp
#include <iostream>
#include <queue>
using namespace std;

int main() {
    queue<int> q;  // Declaring a queue of integers
    return 0;
}
```

### **Basic Operations on Queue:**

1. **push()**: Adds an element to the back of the queue.

2. **pop()**: Removes the front element of the queue.

3. **front()**: Returns the front element.

4. **back()**: Returns the last element.

5. **empty()**: Checks if the queue is empty.

6. **size()**: Returns the number of elements in the queue.

### **Code Examples:**

#### **1. Basic Queue Operations**

```cpp
#include <iostream>
#include <queue>
using namespace std;

int main() {
    queue<int> q;

    // Inserting elements into the queue
    q.push(10);
    q.push(20);
    q.push(30);

    // Displaying the front and back elements
    cout << "Front: " << q.front() << endl;  // Output: 10
    cout << "Back: " << q.back() << endl;    // Output: 30

    // Removing the front element
    q.pop();

    // After pop operation
    cout << "Front after pop: " << q.front() << endl;  // Output: 20

    // Checking if the queue is empty
    if (q.empty()) {
        cout << "Queue is empty." << endl;
    } else {
        cout << "Queue is not empty." << endl;
    }

    // Size of the queue
    cout << "Size of the queue: " << q.size() << endl;  // Output: 2

    return 0;
}
```

#### **2. Real-Life Example: Ticket Counter Simulation**

In a ticket counter, people are served based on the order they arrive. This can be simulated using a queue:

```cpp
#include <iostream>
#include <queue>
using namespace std;

int main() {
    queue<string> ticketQueue;

    // People arriving at the counter
    ticketQueue.push("Alice");
    ticketQueue.push("Bob");
    ticketQueue.push("Charlie");

    // Serving the first person in the queue
    cout << "Serving: " << ticketQueue.front() << endl;  // Output: Alice
    ticketQueue.pop();  // Alice is served and removed

    // Serving the next person
    cout << "Serving: " << ticketQueue.front() << endl;  // Output: Bob
    ticketQueue.pop();  // Bob is served and removed

    return 0;
}
```

### **Key Points to Remember:**

- A queue in C++ only allows insertion at the back and deletion from the front.
- The `queue` container does not allow direct access to elements other than the front or back.
- Common applications of queues include task scheduling, breadth-first search (BFS) in graphs, and buffering.

### **Common Mistakes to Avoid:**

- Forgetting that elements are removed from the front (FIFO).
- Trying to access elements directly using an index, which is not possible in a queue.

---
