### 111. 二叉树的最小深度

> 题目

给定一个二叉树，找出其最小深度。

最小深度是从根节点到最近叶子节点的最短路径上的节点数量。

说明：叶子节点是指没有子节点的节点。

示例 1：
```
输入：root = [3,9,20,null,null,15,7]
输出：2
```

示例 2：
```
输入：root = [2,null,3,null,4,null,5,null,6]
输出：5
```

提示：

树中节点数的范围在 [0, 105] 内
-1000 <= Node.val <= 1000

> 思路

使用递归的方法即可，但要考虑到根节点的情况。

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
 * @return {number}
 */
var minDepth = function (root) {
  if (!root) return 0;
  if (!root.left && !root.right) return 1;

  return (
    1 +
    Math.min(
      root.left ? minDepth(root.left) : Infinity,
      root.right ? minDepth(root.right) : Infinity
    )
  );
};
```

> 复杂度分析

时间复杂度 : O(N)。N 为树的节点数。

空间复杂度 : O(H)。因为使用递归，H为数的高度。

> 执行

执行用时：244 ms, 在所有 JavaScript 提交中击败了63.46%的用户

内存消耗：71.3 MB, 在所有 JavaScript 提交中击败了45.26%的用户
