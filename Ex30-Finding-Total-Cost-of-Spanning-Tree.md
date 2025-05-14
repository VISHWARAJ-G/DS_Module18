# Ex30 – Finding Total Cost of Spanning Tree

## DATE: 09-05-2025

---

## AIM:
To write a C Program to implement Prim's Algorithm for finding the Total Cost of a Minimum Spanning Tree (MST).

---

## Algorithm:
1. Start with a graph represented using a cost adjacency matrix.
2. Choose any vertex as the starting point and mark it as visited.
3. Find the smallest edge connecting a visited and an unvisited vertex.
4. Add the edge to the MST and mark the connected unvisited vertex as visited.
5. Repeat steps 3–4 until all vertices are included in the MST.
6. Calculate and print the total cost of the spanning tree.

---

## Program:
```c
/*
Program to implement Prim's Algorithm for finding Total Cost of spanning tree
Developed by: Vishwaraj G.
RegisterNumber: 212223220125
*/

#include <stdio.h>

#define MAX 10
#define INF 9999

int main() {
    int cost[MAX][MAX], visited[MAX] = {0};
    int n, i, j, edges = 0;
    int min, u = 0, v = 0, totalCost = 0;

    printf("Enter number of vertices: ");
    scanf("%d", &n);

    printf("Enter the cost adjacency matrix (use 9999 for no edge):\n");
    for (i = 0; i < n; i++)
        for (j = 0; j < n; j++)
            scanf("%d", &cost[i][j]);

    visited[0] = 1;

    printf("\nEdges in the Minimum Spanning Tree:\n");

    while (edges < n - 1) {
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

        visited[v] = 1;
        printf("%d - %d : %d\n", u, v, min);
        totalCost += min;
        edges++;
    }

    printf("Total Cost of the Spanning Tree: %d\n", totalCost);

    return 0;
}
```
## Output:
```
Enter number of vertices: 4
Enter the cost adjacency matrix (use 9999 for no edge):
0 5 10 9999
5 0 3 2
10 3 0 6
9999 2 6 0

Edges in the Minimum Spanning Tree:
0 - 1 : 5
1 - 3 : 2
1 - 2 : 3
Total Cost of the Spanning Tree: 10
```
## Result:
Thus, the C program to implement Prim's Algorithm for finding the Total Cost of a Spanning Tree is implemented successfully.
