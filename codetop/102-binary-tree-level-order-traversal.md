### 102. 二叉树的层序遍历

> 题目

[链接](https://leetcode-cn.com/problems/binary-tree-level-order-traversal/)

> 思路

使用广度优先的思路

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
 * @return {number[][]}
 */
var levelOrder = function(root) {
    const res = [];
    if (!root) {
        return res;
    }

    const q = [];
    q.push(root); 
    while (q.length) {
        const currentLevelSize = q.length;
        res.push([]);
        for (let i = 0; i <currentLevelSize; i++) {
            const node = q.shift();
            res[res.length - 1].push(node.val);
            node.left && q.push(node.left);
            node.right && q.push(node.right);
        }
    }

    return res;
};
```

> 复杂度分析

时间复杂度：O(n)。

空间复杂度：O(n)。

> 执行

执行用时：96 ms, 在所有 JavaScript 提交中击败了36.31%的用户

内存消耗：39.2 MB, 在所有 JavaScript 提交中击败了96.65%的用户