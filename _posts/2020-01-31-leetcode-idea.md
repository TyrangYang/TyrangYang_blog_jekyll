---
title: Learn from leetCode
categories: LeetCode
tag:
    - leetCode
---

Some strategy learning from leetCode

## C++ 2d array

Better use a vector(don't need to consider allocator)

```cpp
int row = 10;
int col = 10;
int init = 1;
vector<vector <int>> memos(row, vector<int>(col, init)) // init can ignore
```

```cpp
int** a = new int*[rowCount];
for(int i = 0; i < rowCount; ++i)
    a[i] = new int[colCount];

delete ...
```

## Traverse a tree

The tree structure:

```cpp
struct TreeNode {
    int val;
    TreeNode *left;
    TreeNode *right;
    TreeNode(int x) : val(x), left(NULL), right(NULL) {}
};
```

### BFS DFS Pre-order In-order Post-order

Loop for BFS:

```cpp
void BFS(TreeNode *root){
    stack<TreeNode *> q;
    q.push(root);
    while(!q.empty()){
        TreeNode *temp = q.front();
        q.pop();
        // do something
        if(temp->left != NULL) q.push(temp -> left);
        if(temp->right != NULL) q.push(temp -> right);
    }
}
```

Loop for DFS:

```cpp
void DFS(TreeNode *root){
    stack<TreeNode *> s;
    s.push(root);
    while(!s.empty()){
        TreeNode *temp = s.top();
        s.pop();
        // do something
        if(temp->left != NULL) s.push(temp -> left);
        if(temp->right != NULL) s.push(temp -> right);
    }
}
```

Pre-order: (DFS is same)

```cpp
void preOrder(TreeNode *root){
    if(root == NULL) return;
    // root -> val do something
    preOrder(root -> left);
    preOrder(root -> right);
}
```

In-Order:

```cpp
void inOrder(TreeNode *root){
    if(root == NULL) return;

    inOrder(root -> left);
    // root -> val do something
    inOrder(root -> right);
}
```

Pre-Order: (Bottom-to-up)

```cpp
void postOrder(TreeNode *root){
    if(root == NULL) return;
    postOrder(root -> left);
    postOrder(root -> right);
    // root -> val do something
}
```

### BFS process level by level

```cpp
void BFS(TreeNode *root){
    stack<TreeNode *> q;
    q.push(root);
    while(!q.empty()){
        int levelSize = q.size();
        // get current level size so that BFS can process level by level
        for(int i=0; i<levelSize; ++i){
            TreeNode *temp = q.front();
            q.pop();
            // do something
            if(temp->left != NULL) q.push(temp -> left);
            if(temp->right != NULL) q.push(temp -> right);
        }
    }
}
```

## heap

Function `make_heap` can be used to arrange vector into a heap.

It is better to use adopter `priority_queue` as heap.

```cpp
#include <queue>

priority_queue<pair<char, int>, vector<pair<char, int>> , less<pair<char,int>> > pq;


```

## Faster io for C++

At this part at beginning.

Relative article: [Fast I/O for Competitive Programming - GeeksforGeeks](https://www.geeksforgeeks.org/fast-io-for-competitive-programming/)

```cpp
auto all=[](){
    ios::sync_with_stdio(false); // toggle off synchronization
    cin.tie(nullptr);
    return 0;
}();
```

## Binary search tree(BST) & In-order traversal

After In-order traverse a BST, the result is a sorted sequence.

Also you can use a sorted sequence to rebuild a balance BST.

LeetCode 109 [Convert Sorted List to Binary Search Tree](https://leetcode.com/problems/convert-sorted-list-to-binary-search-tree/)

## DFS & Backtracking

Example for DFS: [LeetCode200](https://leetcode.com/problems/number-of-islands/)

Example for Backtracking: [LeetCode46](https://leetcode.com/problems/permutations/)

The different between them is: **Backtracking will set the current state back after recursion.**

Since they all traverse a matrix, they both need to worry about recursive back. Like DFS goes from left to right and how to protect go back from right left. Of course, sometime it don't need to be considered.

## Word ladder problem

Give a begin word, an end word and a word dictionary.

Word Ladder: [leetCode 127](https://leetcode.com/problems/word-ladder/)

The idea to solve this question is to build a graph (or a State machine) and BFS the graph.

Minimum Genetic Mutation: [leetCode 433](https://leetcode.com/problems/minimum-genetic-mutation/)

Tis question don't have to build a graph since each char only have 4 options. We can just check the one word mutation is stay in dictionary or not.