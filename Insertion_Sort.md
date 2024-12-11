## pseudo-code
```pseudo
// Sorts a given array using insertion sort
// Input: An array A[0..n-1] of orderable elements
// Output: Array A[0..n-1] sorted in ascending order

for i <- 1 to n - 1 do
    v <- A[i]
    j <- i - 1
    while j >= 0 and A[j] > v do
        A[j + 1] <- A[j]
        j <- j - 1
    A[j + 1] <- v
```

## code
```cpp
#include <iostream>
using namespace std;

void insertionSort(int A[], int n) {
    for (int i = 1; i < n; i++) {
        int v = A[i];
        int j = i - 1;
        while (j >= 0 && A[j] > v) {
            A[j + 1] = A[j];
            j--;
        }
        A[j + 1] = v;
    }
}

int main() {
    int A[] = {12, 11, 13, 5, 6};
    int n = sizeof(A) / sizeof(A[0]);
    insertionSort(A, n);
    for (int i = 0; i < n; i++) {
        cout << A[i] << " ";
    }
    return 0;
}
