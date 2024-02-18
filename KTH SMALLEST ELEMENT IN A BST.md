# KTH SMALLEST ELEMENT IN A BST

## Problem Statement
Given a binary search tree (BST) and an integer k, find the k-th smallest element.

### Input
There are two arguments in the input:
1. First one is the root of the BST
2. Second one is an integer k.

### Output
Return an integer, the k-th smallest element of the BST.

### Example
**Input:**
1 2 3 N N N N
3

**Output:**
3


## Code

```java
class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;
    TreeNode(int x) {
        val = x;
    }
}

public class Main {
    static int count;
    public static void main(String[] args) {
        TreeNode root = new TreeNode(2);
        root.left = new TreeNode(1);
        root.right = new TreeNode(3);
        int k = 3;   
        int result = kth(root, k);
        System.out.println(result);
    }

    public static int kth(TreeNode root, int k) {
        count = 0; 
        return inorderTraversal(root, k);
    }

    public static int inorderTraversal(TreeNode root, int k) {
        if (root == null) {
            return -1;
        }
        int left = inorderTraversal(root.left, k);
        if (left != -1) return left; 
        count++;
        if (count == k) return root.val; 
        return inorderTraversal(root.right, k);
    }
}
```
