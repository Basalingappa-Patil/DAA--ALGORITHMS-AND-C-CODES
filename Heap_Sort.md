## pesudo-code
```pseudo
void heapifyBottomUp(int H[], int n) {
    for (int i = n / 2; i >= 1; i--) {
        heapify(H, n, i);
    }
}

// Function to perform heap sort
void heapSort(int H[], int n) {
    // Step 1: Build a max heap
    heapifyBottomUp(H, n);

    // Step 2: Perform the sort
    for (int i = n; i >= 2; i--) {
        swap(H[1], H[i]); // Move current root to the end
        heapify(H, i - 1, 1); // Restore heap property for the reduced heap
    }
}
```

## code
```cpp
#include <iostream>
using namespace std;

// Function to maintain the max heap property
void heapify(int H[], int n, int i) {
    int largest = i;
    int left = 2 * i;
    int right = 2 * i + 1;

    if (left <= n && H[left] > H[largest])
        largest = left;

    if (right <= n && H[right] > H[largest])
        largest = right;

    if (largest != i) {
        swap(H[i], H[largest]);
        heapify(H, n, largest);
    }
}

// Function to build a max heap
void heapifyBottomUp(int H[], int n) {
    for (int i = n / 2; i >= 1; i--) {
        heapify(H, n, i);
    }
}

// Function to perform heap sort
void heapSort(int H[], int n) {
    heapifyBottomUp(H, n);
    for (int i = n; i >= 2; i--) {
        swap(H[1], H[i]); // Move current root to the end
        heapify(H, i - 1, 1); // Restore heap property for the reduced heap
    }
}

int main() {
    int H[] = {0, 12, 11, 13, 5, 6, 7}; // Index 0 is unused for 1-based heap
    int n = 6; // Number of elements in the array

    heapSort(H, n);

    cout << "Sorted array: ";
    for (int i = 1; i <= n; i++) {
        cout << H[i] << " ";
    }

    return 0;
}
