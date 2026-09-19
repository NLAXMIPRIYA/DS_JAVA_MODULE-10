# Ex21 Count the Number of Nodes in the Left Subtree of a Binary Tree

## DATE: 19-09-2026

## AIM:
To design and implement a Java program that constructs a binary tree from given level order input and counts the number of nodes present in the left subtree of the root node.

## Algorithm

1. Read the number of nodes and the level order elements of the binary tree.
2. Construct the binary tree using a queue, assigning the next elements as left and right children.
3. Start from the left child of the root node.
4. Recursively count the nodes present in the left subtree.
5. Display the total number of nodes in the left subtree.

## Program:

```java
/*
Program to construct a binary tree from given level order input
and count the number of nodes in the left subtree.
Developed by: N Laxmi Priya
RegisterNumber: 212225040196
*/

import java.util.*;

public class Main {

    // Node of the binary tree
    static class Node {
        int data;
        Node left;
        Node right;

        Node(int data) {
            this.data = data;
        }
    }

    // Function to construct binary tree from level order
    static Node buildTree(int[] arr) {

        if (arr.length == 0) {
            return null;
        }

        Node root = new Node(arr[0]);

        Queue<Node> queue = new LinkedList<>();
        queue.add(root);

        int i = 1;

        while (i < arr.length) {

            Node current = queue.poll();

            // Create left child
            if (i < arr.length) {
                current.left = new Node(arr[i]);
                queue.add(current.left);
                i++;
            }

            // Create right child
            if (i < arr.length) {
                current.right = new Node(arr[i]);
                queue.add(current.right);
                i++;
            }
        }

        return root;
    }

    // Function to count nodes in a subtree
    static int countNodes(Node root) {

        if (root == null) {
            return 0;
        }

        return 1 + countNodes(root.left) + countNodes(root.right);
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();

        int[] arr = new int[n];

        for (int i = 0; i < n; i++) {
            arr[i] = sc.nextInt();
        }

        Node root = buildTree(arr);

        int count = countNodes(root.left);

        System.out.println("Number of nodes in the left subtree: " + count);
    }
}
```

## Output:

<img width="379" height="197" alt="image" src="https://github.com/user-attachments/assets/faea92da-fc88-4fbe-ab0e-a32eafb5cd64" />



## Result:
The program has been successfully implemented and executed.
It correctly constructs the binary tree from level order input and counts the number of nodes in the left subtree of the root node.
