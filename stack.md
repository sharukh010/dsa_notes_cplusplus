### Notes on Stack Usage in C++ (Using STL Library)

**Introduction**  
A stack is a Last-In-First-Out (LIFO) data structure where the last element added is the first one to be removed. The C++ Standard Template Library (STL) provides a ready-to-use `stack` container that can be used for this purpose.

### Stack Basics

1. **Header File:**  
   To use the stack, you need to include the header file:
   ```cpp
   #include <stack>
   ```

2. **Namespace:**  
   Since we're using the standard library, include:
   ```cpp
   using namespace std;
   ```

3. **Stack Declaration:**  
   A stack is declared as:
   ```cpp
   stack<int> myStack;
   ```
   This creates an empty stack of integers.

### Common Stack Operations

1. **Push Operation (Adding Elements):**
   The `push()` function adds an element to the top of the stack.
   ```cpp
   myStack.push(10);
   myStack.push(20);
   ```
   The stack now contains: [10, 20]

2. **Pop Operation (Removing Elements):**
   The `pop()` function removes the top element from the stack.
   ```cpp
   myStack.pop();
   ```
   After the above operation, the stack now contains: [10]

3. **Top Operation (Accessing the Top Element):**
   The `top()` function returns the top element of the stack without removing it.
   ```cpp
   int topElement = myStack.top();
   cout << "Top element: " << topElement << endl;
   ```
   Output: `Top element: 10`

4. **Size Operation (Checking the Number of Elements):**
   The `size()` function returns the number of elements in the stack.
   ```cpp
   cout << "Stack size: " << myStack.size() << endl;
   ```
   Output: `Stack size: 1`

5. **Empty Operation (Checking if the Stack is Empty):**
   The `empty()` function returns `true` if the stack is empty, otherwise returns `false`.
   ```cpp
   if (myStack.empty()) {
       cout << "Stack is empty" << endl;
   } else {
       cout << "Stack is not empty" << endl;
   }
   ```
   Output: `Stack is not empty`

### Real-Life Example: Undo Feature in Text Editor

A stack can be used to implement the undo feature in a text editor. Each action (like typing a word) is stored in a stack. When the user presses "undo," the last action is popped from the stack and reversed.

**Code Example:**
```cpp
#include <iostream>
#include <stack>
using namespace std;

int main() {
    stack<string> editor;
    
    // Simulating typing
    editor.push("Hello");
    editor.push(" World");
    editor.push("!");

    // Performing undo operation
    cout << "Undo: " << editor.top() << endl;
    editor.pop();

    cout << "Current text: ";
    while (!editor.empty()) {
        cout << editor.top();
        editor.pop();
    }
    
    return 0;
}
```
**Output:**
```
Undo: !
Current text:  WorldHello
```

### Summary of Stack Operations

| Function     | Description                                 | Example Usage        |
|--------------|---------------------------------------------|----------------------|
| `push()`     | Adds an element to the top of the stack     | `myStack.push(10);`  |
| `pop()`      | Removes the top element from the stack      | `myStack.pop();`     |
| `top()`      | Returns the top element of the stack        | `int x = myStack.top();` |
| `size()`     | Returns the number of elements in the stack | `int s = myStack.size();` |
| `empty()`    | Checks if the stack is empty                | `if(myStack.empty())` |

### Conclusion
The stack in the C++ STL is simple yet powerful for solving problems where a LIFO structure is required. Understanding how to use these basic operations is essential for applications like undo features, expression evaluation, and more.

