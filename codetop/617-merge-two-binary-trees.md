### 617. 合并二叉树

> 题目

[链接](https://leetcode-cn.com/problems/merge-two-binary-trees/)

> 思路

深度优先遍历，递归

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
 * @param {TreeNode} root1
 * @param {TreeNode} root2
 * @return {TreeNode}
 */
var mergeTrees = function(root1, root2) {
    if (!root1) {
        return root2;
    }

    if (!root2) {
        return root1;
    }

    const node = new TreeNode(root1.val + root2.val);

    node.left = mergeTrees(root1.left, root2.left);
    node.right = mergeTrees(root1.right, root2.right);

    return node;
};
```

> 复杂度分析

时间复杂度：O(min(nm))。

空间复杂度：O(min(nm))。

> 执行

执行用时：132 ms, 在所有 JavaScript 提交中击败了46.48%的用户

内存消耗：45 MB, 在所有 JavaScript 提交中击败了92.66%的用户
