# Ex27 – Kruskal’s Algorithm

## DATE: 06-05-2025

---

## AIM:
To write a C program to implement Kruskal's Algorithm for finding the Minimum Cost Spanning Tree (MST).

---

## Algorithm

1. Input the number of vertices and edges.
2. Input all the edges with their corresponding weights.
3. Sort all edges in ascending order based on weight.
4. Initialize a parent array for disjoint-set.
5. For each edge (u, v):
   - Find the roots of u and v.
   - If they belong to different sets, include the edge in MST and union their sets.
6. Repeat until (n-1) edges are selected.
7. Display the selected edges and total cost.

---

## Program:
```c
/*
Program to implement Kruskal's Algorithm
Developed by: Vishwaraj G.
RegisterNumber: 212223220125
*/

#include <stdio.h>

#define MAX 100

int parent[MAX];

int find(int i) {
    while (parent[i])
        i = parent[i];
    return i;
}

int union_set(int i, int j) {
    if (i != j) {
        parent[j] = i;
        return 1;
    }
    return 0;
}

int main() {
    int n, edges, i, j, u, v, a, b;
    int cost[MAX][3], t[100][3], total = 0, count = 0;

    printf("Enter number of edges: ");
    scanf("%d", &edges);
    printf("Enter number of vertices: ");
    scanf("%d", &n);

    printf("Enter edges (u v weight):\n");
    for (i = 0; i < edges; i++) {
        scanf("%d%d%d", &cost[i][0], &cost[i][1], &cost[i][2]);
    }

    // Sorting edges by weight (simple bubble sort)
    for (i = 0; i < edges - 1; i++) {
        for (j = 0; j < edges - i - 1; j++) {
            if (cost[j][2] > cost[j + 1][2]) {
                int temp0 = cost[j][0];
                int temp1 = cost[j][1];
                int temp2 = cost[j][2];

                cost[j][0] = cost[j + 1][0];
                cost[j][1] = cost[j + 1][1];
                cost[j][2] = cost[j + 1][2];

                cost[j + 1][0] = temp0;
                cost[j + 1][1] = temp1;
                cost[j + 1][2] = temp2;
            }
        }
    }

    printf("\nEdges in MST using Kruskal's Algorithm:\n");
    for (i = 0; i < edges; i++) {
        u = cost[i][0];
        v = cost[i][1];

        a = find(u);
        b = find(v);

        if (union_set(a, b)) {
            t[count][0] = u;
            t[count][1] = v;
            t[count][2] = cost[i][2];
            total += cost[i][2];
            printf("Edge %d: (%d - %d) cost: %d\n", count + 1, u, v, cost[i][2]);
            count++;
            if (count == n - 1)
                break;
        }
    }

    printf("\nTotal cost of MST: %d\n", total);
    return 0;
}
```
## Output:
```
Enter number of edges: 5
Enter number of vertices: 4
Enter edges (u v weight):
0 1 10
0 2 6
0 3 5
1 3 15
2 3 4

Edges in MST using Kruskal's Algorithm:
Edge 1: (2 - 3) cost: 4
Edge 2: (0 - 3) cost: 5
Edge 3: (0 - 1) cost: 10

Total cost of MST: 19
```
## Result:
Thus, the C program to implement Kruskal's Algorithm for finding minimum cost is implemented successfully.
