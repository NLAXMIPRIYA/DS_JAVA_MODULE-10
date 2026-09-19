# Ex23 Breadth-First Search (BFS) Traversal of a City Junction Map

## DATE: 19-09-2026

## AIM:
To design and implement a Java program to perform Breadth-First Search (BFS) traversal on a city's junction map represented as a graph, and find all reachable locations from a given source junction.

## Algorithm

1. Read the number of junctions and roads, and create an adjacency list to represent the graph.
2. Add each road between two junctions to the adjacency list.
3. Read the source junction and create a queue and a visited array.
4. Mark the source as visited, insert it into the queue, and visit all its unvisited adjacent junctions.
5. Continue until the queue is empty and display all reachable junctions in BFS order.

## Program:

```java
/*
Program to perform Breadth-First Search (BFS) traversal on a
city's junction map represented as a graph.
Developed by: N Laxmi Priya
RegisterNumber: 212225040196
*/

import java.util.*;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        // Read number of junctions and roads
        int n = sc.nextInt();
        int m = sc.nextInt();

        // Create adjacency list
        ArrayList<ArrayList<Integer>> graph = new ArrayList<>();

        for (int i = 0; i < n; i++) {
            graph.add(new ArrayList<>());
        }

        // Read roads
        for (int i = 0; i < m; i++) {

            int u = sc.nextInt();
            int v = sc.nextInt();

            graph.get(u).add(v);
            graph.get(v).add(u);
        }

        // Read source junction
        int source = sc.nextInt();

        boolean[] visited = new boolean[n];

        Queue<Integer> queue = new LinkedList<>();

        // Start BFS
        visited[source] = true;
        queue.add(source);

        System.out.println("BFS Traversal:");

        while (!queue.isEmpty()) {

            int current = queue.poll();

            System.out.print(current + " ");

            // Visit adjacent junctions
            for (int next : graph.get(current)) {

                if (!visited[next]) {
                    visited[next] = true;
                    queue.add(next);
                }
            }
        }
    }
}
```

## Output:

![Uploading image.png…]()


## Result:
The program has been successfully implemented and executed.
It performs Breadth-First Search (BFS) traversal on a city junction map and correctly lists all reachable locations from the given source node.
