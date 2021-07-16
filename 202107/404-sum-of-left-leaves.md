### 404. 左叶子之和

> 题目

[链接](https://leetcode-cn.com/problems/sum-of-left-leaves/)

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
 * @return {number}
 */
var sumOfLeftLeaves = function (root) {
    let sum = 0;

    function dfs(root) {
        if (!root) return;
        if (root.left && !root.left.left && !root.left.right) {
            sum += root.left.val;
        }

        dfs(root.left);
        dfs(root.right);
    }

    dfs(root);
    return sum;
};
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(N)。

> 执行

执行用时：72 ms, 在所有 JavaScript 提交中击败了96.24%的用户

内存消耗：39.8 MB, 在所有 JavaScript 提交中击败了22.43%的用户
