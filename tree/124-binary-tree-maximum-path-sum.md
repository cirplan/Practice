### 124. 二叉树中的最大路径和

> 题目

给定一个非空二叉树，返回其最大路径和。

本题中，路径被定义为一条从树中任意节点出发，沿父节点-子节点连接，达到任意节点的序列。该路径至少包含一个节点，且不一定经过根节点。

示例 1：
```
输入：[1,2,3]

       1
      / \
     2   3

输出：6
```

示例 2：
```
输入：[-10,9,20,null,null,15,7]

   -10
   / \
  9  20
    /  \
   15   7

输出：42
```

> 思路

求最大路径和，分三种情况，根节点最大，根节点 + 左节点最大，根节点 + 右节点最大。我们可以使用递归的方式，设置全局最大变量。

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
var maxPathSum = function (root) {
    let max = -Infinity;

    function maxSum(root) {
        if (!root) return null;
        const val = root.val;
        const left = Math.max(maxSum(root.left), 0);
        const right = Math.max(maxSum(root.right), 0);
        const thirdSum = val + left + right;
        const sideSum = val + Math.max(left, right);
        max = Math.max(max, thirdSum)
        return sideSum;
    }

    maxSum(root);
    return max;
};

```

> 复杂度分析

时间复杂度 : O(N)。

空间复杂度 : O(N)。

> 执行

执行用时：112 ms, 在所有 JavaScript 提交中击败了41.52%的用户

内存消耗：47.3 MB, 在所有 JavaScript 提交中击败了24.09%的用户