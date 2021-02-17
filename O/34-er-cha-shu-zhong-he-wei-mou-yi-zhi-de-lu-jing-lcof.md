### 剑指 Offer 34. 二叉树中和为某一值的路径

> 题目

[链接](https://leetcode-cn.com/problems/er-cha-shu-zhong-he-wei-mou-yi-zhi-de-lu-jing-lcof/)

> 思路

使用递归，再使用栈的结构，不符合则弹出

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
 * @param {number} sum
 * @return {number[][]}
 */
var pathSum = function (root, sum) {
    if (!root) return [];

    let res = [];
    let path = [];
    let currentSum = 0;

    findPath(root, sum, path, currentSum);

    return res;

    function findPath(root, sum, path, currentSum) {
        const val = root.val;
        currentSum += val;
        path.push(val);

        const isLeaf = !root.left && !root.right;
        if (currentSum === sum && isLeaf) {
            res.push(path.slice());
        } else {
            if (root.left) {
                findPath(root.left, sum, path, currentSum);
            }

            if (root.right) {
                findPath(root.right, sum, path, currentSum);
            }
        }

        path.pop();
    }
};
```

> 复杂度分析

时间复杂度：O(N)。N是节点数。

空间复杂度：O(N)。

> 执行

执行用时：100 ms, 在所有 JavaScript 提交中击败了67.17%的用户

内存消耗：40.9 MB, 在所有 JavaScript 提交中击败了59.19%的用户