### 104. 二叉树的最大深度

> 题目

给定一个二叉树，找出其最大深度。

二叉树的深度为根节点到最远叶子节点的最长路径上的节点数。

说明: 叶子节点是指没有子节点的节点。

示例：
```
给定二叉树 [3,9,20,null,null,15,7]，

    3
   / \
  9  20
    /  \
   15   7
返回它的最大深度 3 。
```

> 思路

使用递归的方法，取左节点和右节点的最大深度。

> 代码

```js
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {TreeNode} root
 * @return {number}
 */
var maxDepth = function(root) {
    if (!root) return 0;

    return 1 + Math.max(maxDepth(root.left), maxDepth(root.right));
};
```

> 复杂度分析

时间复杂度：O(n)，n 为二叉树节点的个数。

空间复杂度：O(height)，其中 height 表示二叉树的高度。

> 执行

执行用时：84 ms, 在所有 JavaScript 提交中击败了71.14%的用户。

内存消耗：40.5 MB, 在所有 JavaScript 提交中击败了41.33%的用户。

