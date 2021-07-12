### 144. 二叉树的前序遍历

> 题目

[链接](https://leetcode-cn.com/problems/binary-tree-preorder-traversal/)

> 思路

递归

> 代码

```js
/**
 * Definition for a binary tree node.
 * function TreeNode(val, left, right) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.left = (left===undefined ? null : left)
 *     this.right = (right===undefined ? null : right)
 * }
 */
/**
 * @param {TreeNode} root
 * @return {number[]}
 */
var preorderTraversal = function (root) {
    let res = [];
    const dfs = function (root) {
        if (root === null) return;
        //先序遍历所以从父节点开始
        res.push(root.val);
        //递归左子树
        dfs(root.left);
        //递归右子树
        dfs(root.right);
    }
    dfs(root);
    return res;
};
```

> 复杂度分析

时间复杂度：O(n)。

空间复杂度：O(n)。

> 执行

执行用时：68 ms, 在所有 JavaScript 提交中击败了98.20%的用户

内存消耗：37.8 MB, 在所有 JavaScript 提交中击败了76.05%的用户
