### 112. 路径总和

> 题目

[链接](https://leetcode-cn.com/problems/path-sum/)

> 思路

使用递归，把问题转换成 hasPathSum(root.left, targetSum - root.val) || hasPathSum(root.right, targetSum - root.val)

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
 * @param {number} targetSum
 * @return {boolean}
 */
var hasPathSum = function (root, targetSum) {
    if (!root) {
        return false;
    }

    if (!root.left && !root.right) {
        return root.val === targetSum;
    }

    return hasPathSum(root.left, targetSum - root.val) || hasPathSum(root.right, targetSum - root.val)
};
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(H)。H 为树的深度

> 执行

执行用时：100 ms, 在所有 JavaScript 提交中击败了47.85%的用户

内存消耗：41.4 MB, 在所有 JavaScript 提交中击败了79.71%的用户
