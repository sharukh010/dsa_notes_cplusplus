### Notes on Insertion Sort in C++

**Insertion Sort Overview:**
Insertion Sort is a simple, comparison-based sorting algorithm that builds the final sorted array one element at a time. It is much like the process of sorting playing cards in your hands: each new card is placed in its correct position relative to the cards already sorted.

**Key Characteristics:**
- **In-Place Sorting:** Does not require extra storage; sorts the array within the given memory.
- **Stable:** Maintains the relative order of elements with equal keys.
- **Best Use:** Works well on small data sets or arrays that are nearly sorted.

### Algorithm Steps
1. **Assume the First Element is Sorted:** The first element in the array is considered as a sorted section.
2. **Insert Each Subsequent Element:** Pick the next element and insert it into the sorted section in the correct position.
3. **Shift Elements:** If the new element is smaller than the current elements in the sorted section, shift the larger elements one position to the right to make room for the new element.
4. **Repeat:** Continue this process for each element in the array.

### Code Explanation

Here's the C++ code for Insertion Sort:

```cpp
#include <iostream>
using namespace std;

// Function to perform insertion sort on arr[]
void insertionSort(int arr[], int n) {
    for (int i = 1; i < n; i++) {
        int key = arr[i];  // Store the current element to be inserted
        int j = i - 1;

        // Move elements of arr[0..i-1], that are greater than key,
        // to one position ahead of their current position
        while (j >= 0 && arr[j] > key) {
            arr[j + 1] = arr[j];
            j = j - 1;
        }

        // Insert the key at its correct position
        arr[j + 1] = key;
    }
}

// Utility function to print the array
void printArray(int arr[], int size) {
    for (int i = 0; i < size; i++)
        cout << arr[i] << " ";
    cout << endl;
}

// Driver code to test the insertion sort
int main() {
    int arr[] = {12, 11, 13, 5, 6};
    int n = sizeof(arr) / sizeof(arr[0]);

    cout << "Original array: ";
    printArray(arr, n);

    insertionSort(arr, n);

    cout << "Sorted array: ";
    printArray(arr, n);

    return 0;
}
```

### Code Breakdown

#### 1. **`insertionSort` Function:**
```cpp
void insertionSort(int arr[], int n) {
    for (int i = 1; i < n; i++) {
        int key = arr[i];  // The current element to be inserted into the sorted section
        int j = i - 1;

        // Shift elements of arr[0..i-1] that are greater than key to one position to the right
        while (j >= 0 && arr[j] > key) {
            arr[j + 1] = arr[j];
            j = j - 1;
        }

        // Insert the key into its correct sorted position
        arr[j + 1] = key;
    }
}
```
- **Key Variable:** `key` stores the element that is to be inserted into the sorted section of the array.
- **Inner Loop:** The `while` loop shifts elements that are larger than `key` to the right, making room for the `key` to be placed in its correct position.
- **Insertion:** After finding the correct spot, `key` is placed into the array (`arr[j + 1] = key;`).
- **Outer Loop:** The `for` loop iterates through each element in the array starting from the second element (`i = 1`), treating the first element as a pre-sorted section.

#### 2. **Utility Functions:**
- **`printArray`:** Prints the elements of the array to visually check the sorting.
- **`main`:** 
  - Initializes an array and calculates its size.
  - Calls `insertionSort` to sort the array.
  - Prints both the original and sorted arrays.

### How Insertion Sort Works
1. The algorithm starts with the second element (index `1`) and treats the first element as the sorted section.
2. It picks the next element (`key`), compares it with the elements in the sorted section, and shifts those elements to the right until it finds the correct position for the `key`.
3. Inserts the `key` into its correct position in the sorted section.
4. Repeats this process for each element in the array until the entire array is sorted.

### Example Walkthrough
For the array `{12, 11, 13, 5, 6}`:
1. **First Pass (`i = 1`):** `key = 11`
   - Compare `11` with `12`, shift `12` right.
   - Insert `11` at the first position: `{11, 12, 13, 5, 6}`
2. **Second Pass (`i = 2`):** `key = 13`
   - `13` is already in the correct position, so no changes.
3. **Third Pass (`i = 3`):** `key = 5`
   - Compare `5` with `13`, `12`, `11`, shift each one right.
   - Insert `5` at the first position: `{5, 11, 12, 13, 6}`
4. **Fourth Pass (`i = 4`):** `key = 6`
   - Compare `6` with `13`, `12`, `11`, shift each one right.
   - Insert `6` at the second position: `{5, 6, 11, 12, 13}`

### Complexity Analysis
- **Time Complexity:**
  - **Best Case:** \(O(n)\) when the array is already sorted.
  - **Average and Worst Case:** \(O(n^2)\) when the array is in reverse order.
- **Space Complexity:** \(O(1)\) because it is an in-place sorting algorithm (requires no additional storage for sorting).
- **Stable Sort:** Maintains the relative order of equal elements.

### Pros and Cons of Insertion Sort
#### Pros:
- Simple and easy to implement.
- Efficient for small or nearly sorted arrays.
- In-place sorting (does not require extra storage).
- Stable sort.

#### Cons:
- Inefficient for large unsorted arrays due to its \(O(n^2)\) time complexity.
- Not suitable for very large datasets.

### When to Use Insertion Sort
- Best used for small arrays or when the array is partially sorted.
- Useful as a building block in more advanced algorithms (e.g., hybrid sorting algorithms like TimSort).

This C++ implementation of insertion sort is a straightforward approach to sorting an array and illustrates how elements are shifted and inserted into their correct positions.