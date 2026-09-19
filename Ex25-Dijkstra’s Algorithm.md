# Ex25 Finding the Fastest Route to a Charging Station using Dijkstra’s Algorithm

## DATE: 19-09-2026

## AIM:
To design and implement a Java program that helps an electric vehicle (EV) find the shortest travel time from its current block to the nearest charging station using Dijkstra’s shortest path algorithm.

## Algorithm

1. Read the number of blocks, roads, and charging stations, and create a weighted graph using an adjacency list.
2. Read the travel time for each road and store the connected blocks with their weights.
3. Read the EV's starting block and the charging station blocks.
4. Apply Dijkstra’s algorithm from the starting block to calculate the minimum travel time to every reachable block.
5. Find and display the minimum travel time to any reachable charging station; if no station is reachable, display an appropriate message.

## Program:

```java
/*
Program to find the Fastest Route to a Charging Station using Dijkstra’s Algorithm
Developed by: N Laxmi Priya
RegisterNumber: 212225040196
*/

import java.util.*;

public class Main {

    // Edge class to store destination and travel time
    static class Edge {
        int node;
        int weight;

        Edge(int node, int weight) {
            this.node = node;
            this.weight = weight;
        }
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        // Read number of blocks, roads and charging stations
        int n = sc.nextInt();
        int m = sc.nextInt();
        int s = sc.nextInt();

        ArrayList<ArrayList<Edge>> graph = new ArrayList<>();

        for (int i = 0; i < n; i++) {
            graph.add(new ArrayList<>());
        }

        // Read roads
        for (int i = 0; i < m; i++) {

            int u = sc.nextInt();
            int v = sc.nextInt();
            int time = sc.nextInt();

            // Roads are bidirectional
            graph.get(u).add(new Edge(v, time));
            graph.get(v).add(new Edge(u, time));
        }

        // Read charging station blocks
        boolean[] station = new boolean[n];

        for (int i = 0; i < s; i++) {
            int stationNode = sc.nextInt();
            station[stationNode] = true;
        }

        // Read EV starting block
        int start = sc.nextInt();

        // Distance array
        int[] distance = new int[n];

        Arrays.fill(distance, Integer.MAX_VALUE);

        // Priority Queue stores {distance, node}
        PriorityQueue<int[]> pq =
                new PriorityQueue<>((a, b) -> Integer.compare(a[0], b[0]));

        distance[start] = 0;
        pq.add(new int[]{0, start});

        // Dijkstra's Algorithm
        while (!pq.isEmpty()) {

            int[] current = pq.poll();

            int currentDistance = current[0];
            int currentNode = current[1];

            // Ignore outdated entries
            if (currentDistance > distance[currentNode]) {
                continue;
            }

            for (Edge edge : graph.get(currentNode)) {

                int newDistance =
                        currentDistance + edge.weight;

                if (newDistance < distance[edge.node]) {

                    distance[edge.node] = newDistance;

                    pq.add(new int[]{
                        newDistance,
                        edge.node
                    });
                }
            }
        }

        // Find nearest reachable charging station
        int fastestTime = Integer.MAX_VALUE;
        int nearestStation = -1;

        for (int i = 0; i < n; i++) {

            if (station[i] && distance[i] < fastestTime) {
                fastestTime = distance[i];
                nearestStation = i;
            }
        }

        if (nearestStation == -1 ||
            fastestTime == Integer.MAX_VALUE) {

            System.out.println("No charging station is reachable.");

        } else {

            System.out.println(
                "Nearest charging station: " + nearestStation
            );

            System.out.println(
                "Shortest travel time: " + fastestTime
            );
        }
    }
}
```

## Output:

<img width="378" height="266" alt="image" src="https://github.com/user-attachments/assets/d669809b-cd7f-4479-99c7-4edf91ecfe2a" />


## Result:
The program has been successfully implemented and executed.
It uses Dijkstra’s algorithm to determine the shortest travel time from the EV’s current location to the nearest charging station and correctly handles cases where no station is reachable.
