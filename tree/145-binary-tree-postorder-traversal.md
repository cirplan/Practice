### 145. 二叉树的后序遍历

> 题目

给定一个二叉树，返回它的 后序 遍历。

示例:

输入: [1,null,2,3]  
   1
    \
     2
    /
   3 

输出: [3,2,1]
进阶: 递归算法很简单，你可以通过迭代算法完成吗？

> 思路

后序遍历，先遍历左节点，再遍历右节点。

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
var postorderTraversal = function (root) {
    let stack = [];

    function reverse(root) {
        if (root === null) return root;
        reverse(root.left);
        reverse(root.right);
        stack.push(root);
    }

    reverse(root);
    return stack;
};
```

> 复杂度分析

时间复杂度 : O(N)。

空间复杂度 : O(N)。

> 执行

执行用时：80 ms, 在所有 JavaScript 提交中击败了80.77%的用户

内存消耗：38 MB, 在所有 JavaScript 提交中击败了33.19%的用户
