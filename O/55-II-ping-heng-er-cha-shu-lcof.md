### 剑指 Offer 55 - II. 平衡二叉树

> 题目

[链接](https://leetcode-cn.com/problems/ping-heng-er-cha-shu-lcof/)

> 思路

后序遍历，判断左右子数的层级差是否小于等于1。

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
 * @return {boolean}
 */
var isBalanced = function (root) {
    return recur(root) !== -1;

    function recur(root) {
        if (root == null) return 0;
        let left = recur(root.left);
        if (left == -1) return -1;
        let right = recur(root.right);
        if (right == -1) return -1;
        return Math.abs(left - right) < 2 ? Math.max(left, right) + 1 : -1;
    }
};
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(N)。

> 执行

执行用时：100 ms, 在所有 JavaScript 提交中击败了67.59%的用户

内存消耗：42 MB, 在所有 JavaScript 提交中击败了63.55%的用户
