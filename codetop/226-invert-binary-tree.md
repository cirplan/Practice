### 226. 翻转二叉树

> 题目

[链接](https://leetcode-cn.com/problems/invert-binary-tree/)

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
 * @return {TreeNode}
 */
var invertTree = function (root) {
    if (!root) return null;

    let left = root.left;
    let right = root.right;
    root.right = invertTree(left);
    root.left = invertTree(right);

    return root;
};
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(N)。

> 执行

执行用时：80 ms, 在所有 JavaScript 提交中击败了84.21%的用户

内存消耗：38.9 MB, 在所有 JavaScript 提交中击败了78.88%的用户
