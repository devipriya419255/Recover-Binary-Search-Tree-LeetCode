# Recover-Binary-Search-Tree-LeetCode

"C implementation of LeetCode #99: Recover Binary Search Tree. Utilizes Morris Inorder Traversal to achieve $O(1)$ space complexity, repairing the tree in-place."

## 🧩 LeetCode 99: Recover Binary Search Tree (C Solution)

A specialized algorithm designed to detect and correct exactly two nodes in a Binary Search Tree that have been swapped by mistake.

## 📖 Problem Description

In a given BST, exactly two nodes have swapped values. Your task is to recover the tree without changing its physical structure.

### Example
- **Input:** `root = [1,3,null,null,2]`
- **Output:** `[3,1,null,null,2]`
- **Reasoning:** In an inorder traversal, the values should be sorted. Identifying where the sort order breaks allows us to find the swapped nodes.

## 🛠️ Technical Approach

This solution implements **Morris Inorder Traversal**, which is the key to solving the problem in **constant space**:
1. **Threaded Binary Tree**: It temporarily modifies the tree by pointing the rightmost child of a left subtree back to the current node (creating a "thread").
2. **Finding Anomalies**: During traversal, we keep track of the `prev` node. If `prev->val > curr->val`, we've found a "drop" in the sorted order.
   - The **first** misplaced node is the `prev` node of the first drop.
   - The **second** misplaced node is the `curr` node of the last drop.
3. **Value Swap**: After the traversal completes and the tree structure is restored, the values of the two identified nodes are swapped.

## 📊 Complexity Analysis

- **Time Complexity:** $O(N)$ — Every edge is traversed at most twice.
- **Space Complexity:** $O(1)$ — No recursion stack or auxiliary stack used.

## 🚀 How to Run

1. Save the code as `recover_bst.c`.
2. Compile using gcc:
   ```bash
   gcc -O3 recover_bst.c -o recover_bst
