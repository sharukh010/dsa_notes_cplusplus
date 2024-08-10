### Stacks and Their Operations Using C++ STL

A **stack** is a data structure that follows the Last In, First Out (LIFO) principle. This means that the last element added to the stack is the first one to be removed. It’s similar to a stack of plates: you add (push) plates to the top, and you also remove (pop) plates from the top.

#### **Real-Life Example:**
Imagine you’re stacking books on a shelf. You place one book on top of the other. If you want to remove a book, you can only take the one on top. The book you placed last is the first one you remove, which perfectly illustrates the LIFO principle.

#### **Stack Operations Using C++ STL**

The C++ Standard Template Library (STL) provides a `stack` class that allows you to perform stack operations easily. Here’s how you can perform basic stack operations using the `stack` class.

1. **Creating a Stack:**
   - You can create a stack using the `stack` class provided by the STL.

   ```cpp
   #include <iostream>
   #include <stack>

   int main() {
       std::stack<int> bookStack;
       return 0;
   }
   ```

2. **Push Operation:**
   - The `push()` function is used to add an element to the top of the stack.
   
   ```cpp
   bookStack.push(1); // Adding the first book
   bookStack.push(2); // Adding the second book
   bookStack.push(3); // Adding the third book
   ```

   - **Real-Life Analogy:** Imagine you are stacking books one by one. You place the first book, then the second on top of the first, and then the third on top of the second.

3. **Pop Operation:**
   - The `pop()` function removes the top element from the stack.

   ```cpp
   bookStack.pop(); // Removes the third book (topmost)
   ```

   - **Real-Life Analogy:** When you want to read the book on top, you remove the top book from the stack first.

4. **Top Operation:**
   - The `top()` function returns the top element of the stack without removing it.

   ```cpp
   int topBook = bookStack.top(); // Accessing the top book
   std::cout << "The top book is: " << topBook << std::endl;
   ```

   - **Real-Life Analogy:** You can glance at the title of the top book without taking it off the stack.

5. **Size Operation:**
   - The `size()` function returns the number of elements in the stack.

   ```cpp
   std::cout << "Number of books in the stack: " << bookStack.size() << std::endl;
   ```

   - **Real-Life Analogy:** You count how many books are in your stack without removing any of them.

6. **Empty Operation:**
   - The `empty()` function checks if the stack is empty.

   ```cpp
   if (bookStack.empty()) {
       std::cout << "The stack is empty." << std::endl;
   } else {
       std::cout << "The stack is not empty." << std::endl;
   }
   ```

   - **Real-Life Analogy:** You check if there are any books left in the stack.

#### **Putting It All Together:**

Here’s a simple C++ program demonstrating all the stack operations using the real-life analogy of stacking books:

```cpp
#include <iostream>
#include <stack>

int main() {
    std::stack<int> bookStack;

    // Pushing books onto the stack
    bookStack.push(1); // First book
    bookStack.push(2); // Second book
    bookStack.push(3); // Third book

    // Accessing the top book
    std::cout << "The top book is: " << bookStack.top() << std::endl;

    // Removing the top book
    bookStack.pop();
    std::cout << "After popping, the top book is: " << bookStack.top() << std::endl;

    // Checking the size of the stack
    std::cout << "Number of books in the stack: " << bookStack.size() << std::endl;

    // Checking if the stack is empty
    if (bookStack.empty()) {
        std::cout << "The stack is empty." << std::endl;
    } else {
        std::cout << "The stack is not empty." << std::endl;
    }

    return 0;
}
```

#### **Explanation:**
- This program simulates stacking and unstacking books. Each operation corresponds to an action you would take in real life when dealing with a stack of books.
- The `push` operation adds books, the `pop` operation removes the top book, and the `top` operation lets you see the top book without removing it.
- The `size` and `empty` operations help you keep track of how many books are in the stack and whether the stack is empty.

Using stacks in programming is helpful when you need to manage data that needs to be processed in a LIFO manner, like undo operations in text editors, backtracking algorithms, or parsing expressions in compilers.