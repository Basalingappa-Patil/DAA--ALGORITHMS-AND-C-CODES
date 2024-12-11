## pseudo-code
```pseudo
// Sorts a given array using bubble sort  
// Input: An array A[0..n-1] of orderable  
// elements  
// Output: Array A[0...n-1] sorted in  
// ascending order  
for i<- 0 to n - 2 do  
for j <-0 to n - 2 - i do  
if A[j+1] < A[j]  
swap A[j] and A[j+1]
```

## code
```cpp
#include <iostream>  
using namespace std;  

void bubbleSort(int A[], int n) {  
    for (int i = 0; i < n - 1; i++) {  
        for (int j = 0; j < n - 1 - i; j++) {  
            if (A[j + 1] < A[j]) {  
                swap(A[j], A[j + 1]);  
            }  
        }  
    }  
}  
  
int main() {  
    int A[] = {64, 34, 25, 12, 22, 11, 90};  
    int n = sizeof(A) / sizeof(A[0]);   
    bubbleSort(A, n);  
    for (int i = 0; i < n; i++) {  
        cout << A[i] << " ";  
    }  
    return 0;  
}  

