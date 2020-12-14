### 100. 相同的树

> 题目

给定两个二叉树，编写一个函数来检验它们是否相同。

如果两个树在结构上相同，并且节点具有相同的值，则认为它们是相同的。

示例 1:
```
输入:       1         1
          / \       / \
         2   3     2   3

        [1,2,3],   [1,2,3]

输出: true
```

示例 2:
```
输入:      1          1
          /           \
         2             2

        [1,2],     [1,null,2]

输出: false
```

示例 3:
```
输入:       1         1
          / \       / \
         2   1     1   2

        [1,2,1],   [1,1,2]

输出: false
```

> 思路

先判断根节点，然后判断左节点，再判断右节点，这样深度优先，递归就行。

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
 * @param {TreeNode} p
 * @param {TreeNode} q
 * @return {boolean}
 */
var isSameTree = function(p, q) {
    if (!p || !q) {
      return p === q;
    }

    const topIsSame = p.val === q.val;
    if (!topIsSame) {
      return false;
    }
    const leftSame = isSameTree(p.left, q.left);
    if (!leftSame) {
      return false;
    }
    const rightSame = isSameTree(p.right, q.right);
    if (!rightSame) {
      return false;
    }

    return true;
};
```

> 复杂度分析

时间复杂度：O(min(m,n))，其中 m 和 n 分别是两个二叉树的节点数。

空间复杂度：O(min(m,n))，其中 m 和 n 分别是两个二叉树的节点数。空间复杂度取决于递归调用的层数，递归调用的层数不会超过较小的二叉树的最大高度，最坏情况下，二叉树的高度等于节点数。

> 执行

执行用时：88 ms, 在所有 JavaScript 提交中击败了30.64%的用户。

内存消耗：37.8 MB, 在所有 JavaScript 提交中击败了68.87%的用户。

> 算法

递归

深度优先搜索 与 广度优先搜索

