### 110. 平衡二叉树

> 题目

[链接](https://leetcode-cn.com/problems/balanced-binary-tree/)

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
 * @return {boolean}
 */
var isBalanced = function (root) {
    if (!root || (!root.left && !root.right)) return true;
    return Math.abs(dep(root.left) - dep(root.right)) <= 1 && isBalanced(root.left) && isBalanced(root.right);
};

function dep(root) {
    if (!root) return 0;
    if (!root.left && !root.right) return 1;

    return 1 + Math.max(dep(root.left), dep(root.right));
}
```

> 复杂度分析

时间复杂度：O(N ^ 2)。 N 是二叉树中的节点个数。

空间复杂度：O(1)。

> 执行

执行用时：76 ms, 在所有 JavaScript 提交中击败了99.96%的用户

内存消耗：41.5 MB, 在所有 JavaScript 提交中击败了99.66%的用户