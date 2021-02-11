### 剑指 Offer 27. 二叉树的镜像

> 题目

[链接](https://leetcode-cn.com/problems/er-cha-shu-de-jing-xiang-lcof/)

> 思路

递归即可。

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
 * @return {TreeNode}
 */
var mirrorTree = function(root) {
    if (!root) return null;

    let temp = root.left;
    root.left = root.right;
    root.right = temp;

    mirrorTree(root.left);
    mirrorTree(root.right);

    return root;
};
```

> 复杂度分析

时间复杂度：O(N)。N为二叉树节点数。

空间复杂度：O(N)。

> 执行

执行用时：88 ms, 在所有 JavaScript 提交中击败了43.83%的用户

内存消耗：38.7 MB, 在所有 JavaScript 提交中击败了89.22%的用户