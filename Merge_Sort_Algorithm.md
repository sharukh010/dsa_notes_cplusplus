### Notes on Merge Sort in C++

**Merge Sort Overview:**
Merge Sort is a stable, comparison-based, divide-and-conquer sorting algorithm. It divides the array into two halves, recursively sorts each half, and then merges the two sorted halves to produce the sorted array. This process ensures that each step maintains sorted order, resulting in a fully sorted array.

**Key Concepts:**

1. **Divide:** Split the array into two halves.
2. **Conquer:** Recursively sort the two halves using the merge sort algorithm.
3. **Combine:** Merge the two sorted halves into a single sorted array.

### Algorithm Steps

1. **Base Case:** If the array has one or zero elements, it is already sorted.
2. **Divide:** Find the middle point to divide the array into two halves.
3. **Recursively Sort:** Call merge sort on each half.
4. **Merge:** Combine the two sorted halves to form a single sorted array.

### Merge Sort Code Explanation (Without Pointers)

Here's the code for Merge Sort using arrays without pointers or dynamic memory allocation:

```cpp
#include <iostream>
using namespace std;

// Function to merge two halves into a sorted array
void merge(int arr[], int left, int mid, int right) {
    // Sizes of the two subarrays
    int n1 = mid - left + 1;
    int n2 = right - mid;

    // Temporary arrays to hold the elements of the two halves
    int leftArray[n1], rightArray[n2];

    // Copy data to temporary arrays leftArray[] and rightArray[]
    for (int i = 0; i < n1; i++)
        leftArray[i] = arr[left + i];
    for (int j = 0; j < n2; j++)
        rightArray[j] = arr[mid + 1 + j];

    // Merge the temporary arrays back into arr[left..right]
    int i = 0;   // Initial index of leftArray
    int j = 0;   // Initial index of rightArray
    int k = left; // Initial index of merged subarray

    while (i < n1 && j < n2) {
        if (leftArray[i] <= rightArray[j]) {
            arr[k] = leftArray[i];
            i++;
        } else {
            arr[k] = rightArray[j];
            j++;
        }
        k++;
    }

    // Copy the remaining elements of leftArray[], if there are any
    while (i < n1) {
        arr[k] = leftArray[i];
        i++;
        k++;
    }

    // Copy the remaining elements of rightArray[], if there are any
    while (j < n2) {
        arr[k] = rightArray[j];
        j++;
        k++;
    }
}

// Function to implement merge sort
void mergeSort(int arr[], int left, int right) {
    if (left < right) {
        // Find the middle point to divide the array into two halves
        int mid = left + (right - left) / 2;

        // Recursively sort the first and second halves
        mergeSort(arr, left, mid);
        mergeSort(arr, mid + 1, right);

        // Merge the sorted halves
        merge(arr, left, mid, right);
    }
}

// Utility function to print the array
void printArray(int arr[], int size) {
    for (int i = 0; i < size; i++)
        cout << arr[i] << " ";
    cout << endl;
}

// Driver code to test the merge sort
int main() {
    int arr[] = {12, 11, 13, 5, 6, 7};
    int arrSize = sizeof(arr) / sizeof(arr[0]);

    cout << "Original array: ";
    printArray(arr, arrSize);

    mergeSort(arr, 0, arrSize - 1);

    cout << "Sorted array: ";
    printArray(arr, arrSize);

    return 0;
}
```

### Code Explanation

1. **Merge Function:**

   ```cpp
   void merge(int arr[], int left, int mid, int right) {
       int n1 = mid - left + 1;
       int n2 = right - mid;

       int leftArray[n1], rightArray[n2];

       for (int i = 0; i < n1; i++)
           leftArray[i] = arr[left + i];
       for (int j = 0; j < n2; j++)
           rightArray[j] = arr[mid + 1 + j];

       int i = 0, j = 0, k = left;

       while (i < n1 && j < n2) {
           if (leftArray[i] <= rightArray[j]) {
               arr[k] = leftArray[i];
               i++;
           } else {
               arr[k] = rightArray[j];
               j++;
           }
           k++;
       }

       while (i < n1) {
           arr[k] = leftArray[i];
           i++;
           k++;
       }

       while (j < n2) {
           arr[k] = rightArray[j];
           j++;
           k++;
       }
   }
   ```

   - **Input Parameters:** This function takes the main array `arr[]` and the indices `left`, `mid`, and `right` to merge the two halves.
   - **Temporary Arrays:** Two temporary arrays `leftArray` and `rightArray` are created to hold the elements of the two halves of `arr[]`.
   - **Merging:** The function compares the elements of the two subarrays and places the smaller one into the original array, thus merging them in sorted order.
   - **Handling Remaining Elements:** Any leftover elements in `leftArray` or `rightArray` are copied to the main array.

2. **Merge Sort Function:**

   ```cpp
   void mergeSort(int arr[], int left, int right) {
       if (left < right) {
           int mid = left + (right - left) / 2;
           mergeSort(arr, left, mid);
           mergeSort(arr, mid + 1, right);
           merge(arr, left, mid, right);
       }
   }
   ```

   - **Base Case:** The recursion stops when `left` is not less than `right`, meaning the sub-array has one or no elements.
   - **Recursive Sorting:** The array is split into two halves (`left` to `mid` and `mid + 1` to `right`), and `mergeSort` is called recursively on both.
   - **Merging:** The `merge` function is called to combine the two sorted halves.

3. **Utility Functions:**
   - **`printArray`:** Prints the elements of the array for visual verification.
   - **`main`:** Initializes an array, prints it, sorts it using `mergeSort`, and prints the sorted array.

### Key Points:

1. **Divide and Conquer:** Merge sort recursively divides the array until each sub-array contains one element.
2. **Merging:** Combines sorted sub-arrays into a larger sorted array.
3. **Space Complexity:** Uses additional space proportional to the size of the array (`O(n)`) for the temporary arrays in the `merge` function.
4. **Time Complexity:**
   - **Best, Average, and Worst Case:** All have a time complexity of \(O(n \log n)\) because the array is always split in half and merged.
5. **Stability:** Maintains the relative order of equal elements in the sorted output.

### Edge Cases:

- Arrays with one or zero elements are inherently sorted.
- Handles duplicates efficiently because of the stable nature of the algorithm.

This implementation uses fixed-size arrays for simplicity and avoids pointers and dynamic memory allocation (`new` and `delete`).
