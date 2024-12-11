## pseudo-code
```pseudo
ALGORITHM MergeSort(A[0..n-1])
// Sorts a given A[0..n-1] by recursive mergesort
// Input: An array A[0..n-1] of orderable elements
// Output: Array A[0...n-1] sorted in nondecreasing order
if n > 1
copy A[0...|_n/2_| - 1 ] to B[0...|_n/2_| - 1]
copy A[ |_n/2_| ... n - 1 ] to C[0......| ̄ n/2  ̄| - 1]
MergeSort(B[0...|_n/2_| - 1] )
MergeSort(C[0......| ̄ n/2  ̄| - 1] )
Merge(B,C, A)

ALGORITHM Merge(B[0...p-1], C[0...q-1], A[0...p+q-1])
// Merges two sorted arrays into one sorted array
// Input: Arrays B[0...p-1] and C[0...q-1] both sorted
// Output: Sorted array A[0...p+q-1]of the elements of B and C
i  0
j  0
k 0
while i < p and j < q do
if B[i] <= C[j]
A[k] B[i]
i  i + 1
else
A[k]  C[j]
j  j + 1
k  k + 1
if i = p
copy C[j...q - 1] to A[k...p + q - 1]
else
copy B[i...p - 1] to A[k...p + q - 1]
```

## code
```cpp
#include <iostream>
#include <vector>
using namespace std;

void merge(vector<int>& A, int left, int mid, int right) {
    int n1 = mid - left + 1;
    int n2 = right - mid;

    vector<int> B(n1), C(n2);
    for (int i = 0; i < n1; i++) B[i] = A[left + i];
    for (int i = 0; i < n2; i++) C[i] = A[mid + 1 + i];

    int i = 0, j = 0, k = left;
    while (i < n1 && j < n2) {
        if (B[i] <= C[j]) {
            A[k] = B[i];
            i++;
        } else {
            A[k] = C[j];
            j++;
        }
        k++;
    }

    while (i < n1) {
        A[k] = B[i];
        i++;
        k++;
    }
    while (j < n2) {
        A[k] = C[j];
        j++;
        k++;
    }
}

void mergeSort(vector<int>& A, int left, int right) {
    if (left < right) {
        int mid = left + (right - left) / 2;
        mergeSort(A, left, mid);
        mergeSort(A, mid + 1, right);
        merge(A, left, mid, right);
    }
}

int main() {
    vector<int> A = {12, 11, 13, 5, 6, 7};
    int n = A.size();
    mergeSort(A, 0, n - 1);
    for (int i = 0; i < n; i++) {
        cout << A[i] << " ";
    }
    return 0;
}

