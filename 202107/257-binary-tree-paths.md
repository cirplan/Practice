### 257. 二叉树的所有路径

> 题目

[链接](https://leetcode-cn.com/problems/binary-tree-paths/)

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
 * @return {string[]}
 */
var binaryTreePaths = function (root) {
    let list = [];
    function dfs(root, str) {
        if (!root) return;
        str += '' + root.val;
        if (!root.left && !root.right) {
            list.push(str);
        } else {
            str += '->';
            dfs(root.left, str);
            dfs(root.right, str);
        }
    }

    dfs(root, '');
    return list
};
```

> 复杂度分析

时间复杂度：O(N ^ 2)。

空间复杂度：O(N ^ 2)。

> 执行

执行用时：64 ms, 在所有 JavaScript 提交中击败了99.40%的用户

内存消耗：39.3 MB, 在所有 JavaScript 提交中击败了52.18%的用户
