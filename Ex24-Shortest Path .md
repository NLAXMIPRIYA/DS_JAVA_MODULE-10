# Ex24 Shortest Path and Reachability in a Heritage Town using BFS

## DATE: 19-09-2026

## AIM:
To design and implement a Java program that, given a map of attractions in a heritage town connected by walking paths, determines the shortest number of paths (minimum hops) from a starting attraction to a target attraction and finds the number of reachable attractions from the same starting point using Breadth-First Search (BFS).

## Algorithm

1. Read the number of attractions and walking paths, and create an adjacency list to represent the graph.
2. Add each walking path between two attractions to the adjacency list.
3. Read the starting attraction and target attraction, then perform BFS from the starting attraction while storing the distance of each visited attraction.
4. Count all attractions visited during BFS and obtain the shortest distance to the target attraction.
5. Display the shortest number of paths between the two attractions and the total number of reachable attractions.

## Program:

```java
/*
Program to determine Shortest Path and Reachability
in a Heritage Town using BFS.
Developed by: N Laxmi Priya
RegisterNumber: 212225040196
*/

import java.util.*;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        // Read number of attractions and paths
        int n = sc.nextInt();
        int m = sc.nextInt();

        // Create adjacency list
        ArrayList<ArrayList<Integer>> graph = new ArrayList<>();

        for (int i = 0; i < n; i++) {
            graph.add(new ArrayList<>());
        }

        // Read walking paths
        for (int i = 0; i < m; i++) {

            int u = sc.nextInt();
            int v = sc.nextInt();

            graph.get(u).add(v);
            graph.get(v).add(u);
        }

        // Read starting and target attractions
        int start = sc.nextInt();
        int target = sc.nextInt();

        boolean[] visited = new boolean[n];
        int[] distance = new int[n];

        Queue<Integer> queue = new LinkedList<>();

        // Start BFS
        visited[start] = true;
        distance[start] = 0;
        queue.add(start);

        int reachableCount = 0;

        while (!queue.isEmpty()) {

            int current = queue.poll();

            reachableCount++;

            // Visit adjacent attractions
            for (int next : graph.get(current)) {

                if (!visited[next]) {

                    visited[next] = true;
                    distance[next] = distance[current] + 1;

                    queue.add(next);
                }
            }
        }

        // Display shortest path
        if (visited[target]) {
            System.out.println("Shortest number of paths: " + distance[target]);
        } else {
            System.out.println("Target attraction is not reachable.");
        }

        // Display reachable attractions
        System.out.println("Number of reachable attractions: " + reachableCount);
    }
}
```

## Output:

<img width="377" height="241" alt="image" src="https://github.com/user-attachments/assets/3dcfb81f-1ae7-4ae7-b383-77a5cd10adfe" />



## Result:
The program has been successfully implemented and executed.
It correctly computes:
The shortest number of paths (minimum hops) between two attractions.
The total number of reachable attractions from a given starting point using BFS traversal.
