## pseudo-code
```pseudo
ALGORITHM QuickSort(A[l...r])
// Sorts a subarray by quicksort
// Input: A subarray A[l...r] of A[0...n-1], defined by its left and right indices l and r
// Output: Subarray A[l...r] sorted in nondecreasing order
if l < r
s  Partition(A[l...r])
QuickSort(A[l...s - 1])
QuickSort(A[s + 1...r])

ALGORITHM Partition(A[l...r])
// Partitions a subarray by using its first element as a pivot
// Input: A subarray A[l...r] of A[0...n-1], defined by its left and right indices l and r (l < r)
// Output: Subarray A[l...r], with split position returned as this functions value
p  A[l]
i  l
j  r + 1
repeat
repeat i  i + 1 until A[i] >= p
repeat j  j – 1 until A[j] <= p
swap(A[i] and A[j])
until i >= j
swap (A[i], A[j])
swap (A[l], A[j])
return j
```

## code
```cpp
#include <iostream>
using namespace std;

int partition(int A[], int l, int r) {
    int p = A[l];
    int i = l, j = r + 1;

    while (true) {
        do {
            i++;
        } while (i <= r && A[i] < p);

        do {
            j--;
        } while (A[j] > p);

        if (i >= j)
            break;

        swap(A[i], A[j]);
    }

    swap(A[l], A[j]);
    return j;
}

void quickSort(int A[], int l, int r) {
    if (l < r) {
        int s = partition(A, l, r);
        quickSort(A, l, s - 1);
        quickSort(A, s + 1, r);
    }
}

int main() {
    int A[] = {12, 7, 14, 9, 10, 11};
    int n = sizeof(A) / sizeof(A[0]);
    quickSort(A, 0, n - 1);
    for (int i = 0; i < n; i++) {
        cout << A[i] << " ";
    }
    return 0;
}

```
