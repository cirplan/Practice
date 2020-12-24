### 222. 完全二叉树的节点个数

> 题目

给出一个完全二叉树，求出该树的节点个数。

说明：

完全二叉树的定义如下：在完全二叉树中，除了最底层节点可能没填满外，其余每层节点数都达到最大值，并且最下面一层的节点都集中在该层最左边的若干位置。若最底层为第 h 层，则该层包含 1~ 2h 个节点。

示例:

输入: 
    1
   / \
  2   3
 / \  /
4  5 6

输出: 6

> 思路

直接递归，不讲物德。

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
var countNodes = function (root) {
    if (root === null) return root;
    if (root.left === null && root.right === null) return 1;

    const leftNum = countNodes(root.left);
    const rightNum = countNodes(root.right);

    return 1 + leftNum + rightNum;
};
```

> 复杂度分析

时间复杂度 : O(N)。

空间复杂度 : O(N)。

> 执行

执行用时：124 ms, 在所有 JavaScript 提交中击败了58.24%的用户

内存消耗：56.5 MB, 在所有 JavaScript 提交中击败了88.17%的用户