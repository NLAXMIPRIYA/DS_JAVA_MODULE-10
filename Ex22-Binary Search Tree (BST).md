# Ex22 Searching for a Book ID in a Binary Search Tree (BST)

## DATE: 19-09-2026

## AIM:
To design and implement a Java program that constructs a Binary Search Tree (BST) using given Book IDs and checks whether a specific Book ID exists in the BST.

## Algorithm

1. Read the number of Book IDs and insert each Book ID into the Binary Search Tree.
2. For each Book ID, compare it with the current node and insert it to the left if it is smaller or to the right if it is larger.
3. Read the Book ID to be searched.
4. Compare the search ID with each node and move left or right according to the BST property.
5. Display whether the given Book ID is found or not found in the BST.

## Program:

```java
/*
Program to construct a Binary Search Tree (BST) using given Book IDs
and search for a specific Book ID.
Developed by: N Laxmi Priya
RegisterNumber: 212225040196
*/

import java.util.*;

public class Main {

    // Node of the BST
    static class Node {
        int data;
        Node left;
        Node right;

        Node(int data) {
            this.data = data;
        }
    }

    // Function to insert a Book ID into the BST
    static Node insert(Node root, int data) {

        if (root == null) {
            return new Node(data);
        }

        if (data < root.data) {
            root.left = insert(root.left, data);
        } else if (data > root.data) {
            root.right = insert(root.right, data);
        }

        return root;
    }

    // Function to search for a Book ID
    static boolean search(Node root, int key) {

        if (root == null) {
            return false;
        }

        if (root.data == key) {
            return true;
        }

        if (key < root.data) {
            return search(root.left, key);
        } else {
            return search(root.right, key);
        }
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();

        Node root = null;

        // Insert Book IDs into the BST
        for (int i = 0; i < n; i++) {
            int bookId = sc.nextInt();
            root = insert(root, bookId);
        }

        // Read Book ID to search
        int key = sc.nextInt();

        if (search(root, key)) {
            System.out.println("Book ID " + key + " is found in the BST.");
        } else {
            System.out.println("Book ID " + key + " is not found in the BST.");
        }
    }
}
```

## Output:

<img width="371" height="194" alt="image" src="https://github.com/user-attachments/assets/229a3286-caf4-4a84-9277-cc5ed9361931" />


## Result:
The program has been successfully implemented and executed.
It constructs a Binary Search Tree from the given Book IDs and accurately determines whether a queried Book ID exists in the library system.
