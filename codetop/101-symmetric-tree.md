### 101. 对称二叉树

> 题目

[链接](https://leetcode-cn.com/problems/symmetric-tree/)

> 思路

对称，则分别对比左右子树是否一致

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
const check = (p, q) => {
    if (!p && !q) return true;
    if (!p || !q) return false;
    return p.val === q.val && check(p.left, q.right) && check(p.right, q.left);
}

var isSymmetric = function (root) {
    return check(root.left, root.right);
};
```

> 复杂度分析

时间复杂度：O(N)。n 为节点。

空间复杂度：O(N)。

> 执行

执行用时：84 ms, 在所有 JavaScript 提交中击败了95.47%的用户

内存消耗：40 MB, 在所有 JavaScript 提交中击败了38.96%的用户
