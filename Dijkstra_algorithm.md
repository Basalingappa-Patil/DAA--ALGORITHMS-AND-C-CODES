## code
```cpp
#include <iostream>
#define MAX 9999
using namespace std;

class dijkstra {
public:
    int dist[100];
    int path[100];
    int visited[100] = {0};
    int v;
    int src;

    void read(int cost[50][50]);
    void initialize(int cost[50][50]);
};

void dijkstra::initialize(int cost[50][50]) {
    for (int i = 0; i < v; i++) {
        path[i] = src;
        dist[i] = cost[src][i];
        visited[i] = 0;
    }
    visited[src] = 1;
}

void dijkstra::read(int cost[50][50])
 {
    cout << "Enter the cost matrix:" << endl;
    for (int i = 0; i < v; i++)
    {
        for (int j = 0; j < v; j++)
            {
            cin >> cost[i][j];

            }
    }
}


int main()
{
    int cost[50][50];
    dijkstra d;

    cout << "Enter the number of vertices: ";
    cin >> d.v;

    d.read(cost);

    cout << "Enter the source vertex: ";
    cin >> d.src;

    d.initialize(cost);


    cout << "Initialized distances from source: ";
    for (int i = 0; i < d.v; i++)
    {
        cout << d.dist[i] << " ";
    }
    cout << endl;

    return 0;
}
```
