## pseudo-code
```pseudo
// Sorts a given array using selection sort
// Input: An array A[0..n-1] of orderable elements
// Output: Array A[0..n-1] sorted in ascending order

for i <- 0 to n - 2 do
    min <- i
    for j <- i + 1 to n - 1 do
        if A[j] < A[min] then
            min <- j
    swap A[i] and A[min]
```

## code
```cpp
#include <iostream>
using namespace std;

void selectionSort(int A[], int n) {
    for (int i = 0; i < n - 1; i++) {
        int min = i;
        for (int j = i + 1; j < n; j++) {
            if (A[j] < A[min]) {
                min = j;
            }
        }
        swap(A[i], A[min]);
    }
}

int main() {
    int A[] = {64, 25, 12, 22, 11};
    int n = sizeof(A) / sizeof(A[0]);
    selectionSort(A, n);
    for (int i = 0; i < n; i++) {
        cout << A[i] << " ";
    }
    return 0;
}
```
