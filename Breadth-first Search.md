## pseudo-code
```pseudo
ALGORITHM BFS(m[0..v-1][0..v-1], v, source)
// Traverses a graph represented as an adjacency matrix using BFS
// Input: Adjacency matrix m[0..v-1][0..v-1], number of vertices v, and starting vertex source
// Output: Prints the vertices in the order they are visited during BFS

Initialize an empty queue
Initialize visited[0..v-1] <- 0
Enqueue source into the queue
visited[source] <- 1
print "The BFS Traversal is:"

while queue is not empty do
    u <- Dequeue an element from the queue
    print u
    for i <- 0 to v - 1 do
        if m[u][i] = 1 and visited[i] = 0 then
            visited[i] <- 1
            Enqueue i into the queue

```

## code
```cpp
#include <iostream>
using namespace std;

void bfs(int m[10][10], int v, int source) {
    int queue[20];
    int front = 0, rear = 0, u, i;
    int visited[10];

    for (i = 0; i < v; i++)
        visited[i] = 0;

    queue[rear] = source;
    visited[source] = 1;

    cout << "The BFS Traversal is... \n";

    while (front <= rear) {
        u = queue[front];
        cout << u << "\t";
        front++;

        for (i = 0; i < v; i++) {
            if (m[u][i] == 1 && visited[i] == 0) {
                visited[i] = 1;
                rear++;
                queue[rear] = i;
            }
        }
    }
}

int main() {
    int v = 5;
    int m[10][10] = {{0,1,1,0,0}, {1,0,0,1,1},
        {1,0,0,0,1}, {0,1,0,0,0}, {0,1,1,0,0}};

    int source;
    cout << "Enter the source vertex: ";
    cin >> source;

    bfs(m, v, source);

    return 0;
}
```
