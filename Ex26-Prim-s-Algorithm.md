# Ex26 – Prim’s Algorithm

## DATE: 05-05-2025

---

## AIM:
To write a C program to implement Prim's Algorithm for finding the total cost of the Minimum Spanning Tree (MST).

---

## Algorithm

1. Create a cost matrix of the graph (adjacency matrix form).
2. Initialize the visited array with false (0).
3. Start from the first vertex and set it as visited.
4. Repeat until (number of vertices - 1) edges are selected:
   - Select the minimum edge (u, v) such that u is visited and v is not visited.
   - Add the cost of that edge to total cost and mark v as visited.
5. Display the edges selected and the total cost of the MST.

---

## Program:
```c
/*
Program to implement Prim's Algorithm
Developed by: Vishwaraj G.
RegisterNumber: 212223220125
*/

#include <stdio.h>
#define MAX 100
#define INF 9999

int main() {
    int cost[MAX][MAX], visited[MAX], n, i, j, min, u, v, total = 0, no_of_edges = 1;

    printf("Enter the number of vertices: ");
    scanf("%d", &n);

    printf("Enter the cost adjacency matrix (use 9999 for no connection):\n");
    for (i = 0; i < n; i++) {
        for (j = 0; j < n; j++) {
            scanf("%d", &cost[i][j]);
        }
        visited[i] = 0;
    }

    visited[0] = 1;

    printf("\nEdges in MST using Prim's Algorithm:\n");
    while (no_of_edges < n) {
        min = INF;

        for (i = 0; i < n; i++) {
            if (visited[i]) {
                for (j = 0; j < n; j++) {
                    if (!visited[j] && cost[i][j] < min) {
                        min = cost[i][j];
                        u = i;
                        v = j;
                    }
                }
            }
        }

        printf("Edge %d: (%d - %d) cost: %d\n", no_of_edges, u, v, min);
        total += min;
        visited[v] = 1;
        no_of_edges++;
    }

    printf("\nTotal cost of MST: %d\n", total);
    return 0;
}
```
## Output:
```
Enter the number of vertices: 4
Enter the cost adjacency matrix (use 9999 for no connection):
0 2 9999 6
2 0 3 8
9999 3 0 5
6 8 5 0

Edges in MST using Prim's Algorithm:
Edge 1: (0 - 1) cost: 2
Edge 2: (1 - 2) cost: 3
Edge 3: (2 - 3) cost: 5

Total cost of MST: 10
```
## Result:
Thus, the C program to implement Prim's Algorithm for finding Total Cost of the tree is implemented successfully.
