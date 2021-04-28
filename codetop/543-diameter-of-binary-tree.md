### 543. 二叉树的直径

> 题目

[链接](https://leetcode-cn.com/problems/diameter-of-binary-tree/)

> 思路

深度优先遍历

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
var diameterOfBinaryTree = function (root) {
    let ans;
    ans = 0;
    depth(root);
    return ans;

    function depth(node) {
        if (node == null) {
            return 0; // 访问到空节点了，返回0
        }
        let L = depth(node.left); // 左儿子为根的子树的深度
        let R = depth(node.right); // 右儿子为根的子树的深度
        ans = Math.max(ans, L + R); // 计算d_node即L+R+1 并更新ans
        return Math.max(L, R) + 1; // 返回该节点为根的子树的深度
    }
};

```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(h)。h 为树的深度

> 执行

执行用时：108 ms, 在所有 JavaScript 提交中击败了31.07%的用户

内存消耗：41.7 MB, 在所有 JavaScript 提交中击败了38.21%的用户

