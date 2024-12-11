## pseudo-code
```pseudo
ALGORITHM TowerOfHanoi(n, source, destination, auxiliary)
// Solves the Tower of Hanoi problem for n disks
// Input: n (number of disks), source (rod), destination (rod), auxiliary (rod)
// Output: Sequence of moves to transfer n disks from source to destination

if n = 1 then
    print "Move disk 1 from source to destination"
    return
end if

TowerOfHanoi(n - 1, source, auxiliary, destination)
print "Move disk n from source to destination"
TowerOfHanoi(n - 1, auxiliary, destination, source)

```

## code
```cpp
#include <iostream>
using namespace std;

// Recursive function to solve Tower of Hanoi
void towerOfHanoi(int n, char source, char destination, char auxiliary) {
    if (n == 1) {
        cout << "Move disk 1 from " << source << " to " << destination << endl;
        return;
    }
    // Move n-1 disks from source to auxiliary, using destination as a buffer
    towerOfHanoi(n - 1, source, auxiliary, destination);
    
    // Move the nth disk from source to destination
    cout << "Move disk " << n << " from " << source << " to " << destination << endl;

    // Move n-1 disks from auxiliary to destination, using source as a buffer
    towerOfHanoi(n - 1, auxiliary, destination, source);
}

int main() {
    int n; // Number of disks
    cout << "Enter the number of disks: ";
    cin >> n;

    cout << "The sequence of moves to solve the Tower of Hanoi is:" << endl;
    towerOfHanoi(n, 'A', 'C', 'B'); // A, B, and C are the names of the rods

    return 0;
}
```
