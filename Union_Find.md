## code
```cpp
int Find(int parent[], int i) {
  if (parent[i] != i)
      parent[i] = Find(parent, parent[i]);
  return parent[i];
}

void Union(int parent[], int rank[], int x, int y) {
  int xroot = Find(parent, x);
  int yroot = Find(parent, y);

  if (rank[xroot] < rank[yroot])
      parent[xroot] = yroot;
  else if (rank[xroot] > rank[yroot])
      parent[yroot] = xroot;
  else {
      parent[yroot] = xroot;
      rank[xroot]++;
  }
}

void KruskalMST(Edge edges[], int E, int V) {
  int weights[E], idx[E];
  for (int i = 0; i < E; i++) {
      weights[i] = edges[i].weight;
      idx[i] = i;
  }

  MergeSort(weights, idx, 0, E - 1);

  int parent[V], rank[V];
  for (int i = 0; i < V; i++) {
      parent[i] = i;
      rank[i] = 0;
  }

  Edge mst[V - 1];
  int mstSize = 0;

  for (int i = 0; i < E && mstSize < V - 1; i++) {
      Edge edge = edges[idx[i]];
      int x = Find(parent, edge.sr c);
      int y = Find(parent, edge.dest);

      if (x != y) {
          mst[mstSize++] = edge;
          Union(parent, rank, x, y);
      }
  }

  cout << "Edges in the Minimum Spanning Tree:\n";
  int cost = 0;
  for (int i = 0; i < mstSize; i++) {
      cout << mst[i].src << " -- " << mst[i].dest << " == " << mst[i].weight << endl;
      cost += mst[i].weight;
  }
  cout << "Cost = " << cost << endl;
}
```
