# Ex29 – Travelling Salesman Problem

## DATE: 08-05-2025

---

## AIM:
To write a C Program to implement the Travelling Salesman Problem (TSP) for finding the shortest possible route that visits every city exactly once and returns to the starting point.

---

## Algorithm:
1. Input the number of cities and the cost adjacency matrix.
2. Use a backtracking approach to generate all permutations of the cities.
3. For each permutation, calculate the cost of visiting cities in that order and returning to the starting point.
4. Track the minimum cost path.
5. Output the minimum cost of traversal and the corresponding path.

---

## Program:
```c
/*
Program to implement Travelling Salesman Problem for finding shortest path
Developed by: Vishwaraj G.
RegisterNumber: 212223220125
*/

#include <stdio.h>
#include <limits.h>

#define MAX 10

int tsp(int graph[MAX][MAX], int visited[MAX], int pos, int n, int count, int cost, int start) {
    if (count == n && graph[pos][start]) {
        return cost + graph[pos][start];
    }

    int ans = INT_MAX;

    for (int i = 0; i < n; i++) {
        if (!visited[i] && graph[pos][i]) {
            visited[i] = 1;
            int temp = tsp(graph, visited, i, n, count + 1, cost + graph[pos][i], start);
            ans = (temp < ans) ? temp : ans;
            visited[i] = 0;
        }
    }
    return ans;
}

int main() {
    int graph[MAX][MAX], visited[MAX] = {0};
    int n;

    printf("Enter the number of cities: ");
    scanf("%d", &n);

    printf("Enter the cost matrix:\n");
    for (int i = 0; i < n; i++)
        for (int j = 0; j < n; j++)
            scanf("%d", &graph[i][j]);

    visited[0] = 1;  // start from city 0
    int result = tsp(graph, visited, 0, n, 1, 0, 0);

    printf("Minimum cost to visit all cities and return: %d\n", result);

    return 0;
}
```
## Output:
```
Enter the number of cities: 4
Enter the cost matrix:
0 10 15 20
10 0 35 25
15 35 0 30
20 25 30 0

Minimum cost to visit all cities and return: 80
```
## Result:
Thus, the C program to implement the Travelling Salesman Problem for finding the shortest path is implemented successfully.
