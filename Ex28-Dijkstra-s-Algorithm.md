# Ex28 – Dijkstra’s Algorithm

## DATE: 07-05-2025

---

## AIM:
To write a C Program to implement Dijkstra's Algorithm to find the shortest path from a source node to all other nodes in a graph.

---

## Algorithm:

1. Input the number of vertices and the graph as an adjacency matrix.
2. Choose a starting vertex (source).
3. Initialize the distance of source to 0 and all other vertices to infinity.
4. Mark all vertices as unvisited.
5. Repeat for all vertices:
   - Select the unvisited vertex with the smallest distance.
   - Update the distance of its adjacent vertices.
   - Mark the current vertex as visited.
6. Repeat until all vertices are visited.
7. Print the shortest distance from the source to each vertex.

---

## Program:
```c
/*
Program to implement Dijkstra's Algorithm 
Developed by: Vishwaraj G.
RegisterNumber: 212223220125
*/

#include <stdio.h>

#define INFINITY 9999
#define MAX 10

void dijkstra(int graph[MAX][MAX], int n, int start) {
    int distance[MAX], visited[MAX], count, mindistance, nextnode, i, j;

    // Initialize distances and visited array
    for (i = 0; i < n; i++) {
        distance[i] = graph[start][i];
        visited[i] = 0;
    }

    distance[start] = 0;
    visited[start] = 1;
    count = 1;

    while (count < n - 1) {
        mindistance = INFINITY;

        // Find the next node with minimum distance
        for (i = 0; i < n; i++) {
            if (distance[i] < mindistance && !visited[i]) {
                mindistance = distance[i];
                nextnode = i;
            }
        }

        visited[nextnode] = 1;

        // Update distance[]
        for (i = 0; i < n; i++) {
            if (!visited[i]) {
                if (mindistance + graph[nextnode][i] < distance[i]) {
                    distance[i] = mindistance + graph[nextnode][i];
                }
            }
        }
        count++;
    }

    // Display result
    printf("\nVertex\tDistance from Source\n");
    for (i = 0; i < n; i++) {
        printf("%d\t\t%d\n", i, distance[i]);
    }
}

int main() {
    int graph[MAX][MAX], i, j, n, u;

    printf("Enter number of vertices: ");
    scanf("%d", &n);

    printf("Enter the adjacency matrix (use 9999 for infinity):\n");
    for (i = 0; i < n; i++)
        for (j = 0; j < n; j++)
            scanf("%d", &graph[i][j]);

    printf("Enter the starting vertex: ");
    scanf("%d", &u);

    dijkstra(graph, n, u);

    return 0;
}
```
## Output:
```
Enter number of vertices: 4
Enter the adjacency matrix (use 9999 for infinity):
0 3 9999 7
3 0 1 9999
9999 1 0 2
7 9999 2 0
Enter the starting vertex: 0

Vertex  Distance from Source
0       0
1       3
2       4
3       6
```
## Result:
Thus, the Program to implement Dijkstra's Algorithm to find the shortest path is implemented successfully.
