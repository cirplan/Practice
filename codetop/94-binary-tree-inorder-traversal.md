### 94. 二叉树的中序遍历

> 题目

[链接](https://leetcode-cn.com/problems/binary-tree-inorder-traversal/)

> 思路

中序遍历是，左节点，根节点，右节点。使用递归。

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
var inorderTraversal = function (root) {
    const res = [];
    const inorder = (root) => {
        if (!root) {
            return;
        }
        inorder(root.left);
        res.push(root.val);
        inorder(root.right);
    }
    inorder(root);
    return res;
};

```

> 复杂度分析

时间复杂度：O(N)。N为二叉树节点树

空间复杂度：O(N)。取决于二叉树递归深度

> 执行

执行用时：76 ms, 在所有 JavaScript 提交中击败了91.40%的用户

内存消耗：38 MB, 在所有 JavaScript 提交中击败了29.04%的用户
