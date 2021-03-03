### 剑指 Offer 55 - I. 二叉树的深度

> 题目

[链接](https://leetcode-cn.com/problems/er-cha-shu-de-shen-du-lcof/)

> 思路

递归取左、右子树的深度。

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

    const leftDepth = maxDepth(root.left);
    const rightDepth = maxDepth(root.right);

    return Math.max(leftDepth, rightDepth) + 1;
};
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(N)。

> 执行

执行用时：80 ms, 在所有 JavaScript 提交中击败了96.85%的用户

内存消耗：40.6 MB, 在所有 JavaScript 提交中击败了44.85%的用户
