---
title: Learn from leetcode
categories: Leetcode
tag:
    - leetcode
---

Some strategy learning from leetcode

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
