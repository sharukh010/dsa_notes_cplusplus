## Bubble Sort in C++

Bubble Sort is a simple comparison-based sorting algorithm. It repeatedly steps through the list, compares adjacent elements, and swaps them if they are in the wrong order. This process is repeated until the list is sorted.

### How Bubble Sort Works

1. The algorithm starts at the beginning of the array and compares the first two elements.
2. If the first element is greater than the second, they are swapped.
3. It then moves to the next pair of elements, compares them, and swaps if necessary.
4. This process continues to the end of the array, and the largest element "bubbles up" to its correct position.
5. The steps are repeated for the remaining unsorted portion of the array until the entire array is sorted.

### Key Characteristics of Bubble Sort

- **Time Complexity:** 
  - Best Case: \( O(n) \) – when the array is already sorted.
  - Average and Worst Case: \( O(n^2) \) – when elements are in reverse order.
- **Space Complexity:** \( O(1) \) – bubble sort is an in-place sorting algorithm.
- **Stability:** Bubble sort is a stable sorting algorithm because it does not change the relative order of equal elements.
- **Simplicity:** Easy to understand and implement but inefficient for large datasets.

### Implementation of Bubble Sort in C++

Here’s a simple implementation of bubble sort in C++:

```cpp
#include <iostream>
using namespace std;

void bubbleSort(int arr[], int n) {
    for (int i = 0; i < n - 1; i++) {
        // Flag to check if a swap occurred in this pass
        bool swapped = false;

        // Last i elements are already sorted, so skip them
        for (int j = 0; j < n - i - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                // Swap arr[j] and arr[j + 1]
                int temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
                swapped = true;
            }
        }

        // If no swap occurred, the array is already sorted
        if (!swapped) {
            break;
        }
    }
}

void printArray(int arr[], int n) {
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;
}

int main() {
    int arr[] = {64, 34, 25, 12, 22, 11, 90};
    int n = sizeof(arr) / sizeof(arr[0]);

    cout << "Original array: ";
    printArray(arr, n);

    bubbleSort(arr, n);

    cout << "Sorted array: ";
    printArray(arr, n);

    return 0;
}
```

### Explanation of the Code

1. **`bubbleSort(int arr[], int n)`:**
   - This function implements the bubble sort algorithm.
   - The outer loop runs \( n-1 \) times (where \( n \) is the size of the array).
   - A flag `swapped` is used to check if any swap occurred in the inner loop. If no swap occurs, the array is already sorted, and the loop breaks early.
   - The inner loop compares adjacent elements and swaps them if the left element is greater than the right.

2. **`printArray(int arr[], int n)`:**
   - A helper function to print the array's elements.

3. **`main()`:**
   - Initializes an array of integers.
   - Calls `bubbleSort()` to sort the array.
   - Prints the original and sorted arrays.

### Optimizations

- **Early Termination:** The use of a `swapped` flag helps detect if the array is already sorted, potentially reducing the number of passes.
- **Reduced Comparisons:** The inner loop decreases its upper bound (`n - i - 1`) after every pass since the last `i` elements are already sorted.

### Example Output

For the input array: `{64, 34, 25, 12, 22, 11, 90}`

The output will be:

```
Original array: 64 34 25 12 22 11 90 
Sorted array: 11 12 22 25 34 64 90 
```

### Pros and Cons of Bubble Sort

**Pros:**
- Simple and easy to understand.
- Suitable for small data sets.
- In-place sorting (requires no additional memory).

**Cons:**
- Inefficient for large data sets due to its \( O(n^2) \) time complexity.
- Not suitable for real-world use when performance is a concern.

### When to Use Bubble Sort

Due to its simplicity, bubble sort is mainly used for educational purposes to illustrate the concept of sorting algorithms. It is not recommended for large or complex applications because of its inefficiency.