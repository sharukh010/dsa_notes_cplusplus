### Notes on **Linear Search** and **Binary Search** in C++ Using Arrays

#### 1. **Linear Search**

Linear search is the simplest search algorithm. It works by checking each element of the array sequentially until the target value is found or the end of the array is reached.

##### **Working of Linear Search**
- Start at the first element of the array.
- Compare the target value with each element of the array one by one.
- If the target value matches an element, return the index of the element.
- If the target value does not match any element, return -1 to indicate that the element is not found.

##### **Time Complexity**:
- **Best Case**: O(1) (when the target value is the first element).
- **Worst Case**: O(n) (when the target value is the last element or not present).

##### **Code for Linear Search in C++**:

```cpp
#include <iostream>
using namespace std;

int linearSearch(int arr[], int n, int target) {
    for (int i = 0; i < n; i++) {
        if (arr[i] == target) {
            return i; // Return the index if target is found
        }
    }
    return -1; // Return -1 if target is not found
}

int main() {
    int arr[] = {10, 20, 30, 40, 50};
    int n = sizeof(arr)/sizeof(arr[0]);
    int target = 30;
    int result = linearSearch(arr, n, target);
    
    if(result != -1) {
        cout << "Element found at index " << result << endl;
    } else {
        cout << "Element not found" << endl;
    }
    return 0;
}
```

#### 2. **Binary Search**

Binary search is a more efficient search algorithm, but it requires that the array be **sorted**. It works by repeatedly dividing the search interval in half and comparing the target value to the middle element of the interval.

##### **Working of Binary Search**
- Start with the entire sorted array.
- Compare the target value with the middle element.
  - If the target value is equal to the middle element, return the index of the middle element.
  - If the target value is less than the middle element, search the left half of the array.
  - If the target value is greater than the middle element, search the right half of the array.
- Repeat the process until the target value is found or the search interval is empty (i.e., the left index is greater than the right index).

##### **Time Complexity**:
- **Best Case**: O(1) (when the target value is the middle element).
- **Worst Case**: O(log n) (since the array is halved with each step).

##### **Code for Binary Search in C++**:

```cpp
#include <iostream>
using namespace std;

int binarySearch(int arr[], int left, int right, int target) {
    while (left <= right) {
        int mid = left + (right - left) / 2; // Avoids overflow

        // Check if target is present at mid
        if (arr[mid] == target) {
            return mid; // Return the index if target is found
        }
        // If target is greater, ignore the left half
        else if (arr[mid] < target) {
            left = mid + 1;
        }
        // If target is smaller, ignore the right half
        else {
            right = mid - 1;
        }
    }
    return -1; // Return -1 if target is not found
}

int main() {
    int arr[] = {10, 20, 30, 40, 50};
    int n = sizeof(arr)/sizeof(arr[0]);
    int target = 30;
    int result = binarySearch(arr, 0, n - 1, target);
    
    if(result != -1) {
        cout << "Element found at index " << result << endl;
    } else {
        cout << "Element not found" << endl;
    }
    return 0;
}
```

#### **Comparison: Linear Search vs Binary Search**

| Feature                | Linear Search           | Binary Search        |
|------------------------|-------------------------|----------------------|
| **Precondition**        | No need for sorted array| Requires sorted array|
| **Time Complexity**     | O(n)                    | O(log n)             |
| **Best Case**           | O(1)                    | O(1)                 |
| **Worst Case**          | O(n)                    | O(log n)             |
| **Space Complexity**    | O(1)                    | O(1)                 |
| **Efficiency**          | Less efficient          | More efficient       |
| **Use Case**            | Small/Unsorted datasets | Large/Sorted datasets|

#### **Conclusion**:
- Use **linear search** when the array is unsorted or small in size.
- Use **binary search** when the array is sorted, especially for larger datasets, to improve efficiency.

