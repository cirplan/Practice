### 剑指 Offer 36. 二叉搜索树与双向链表

> 题目

[链接](https://leetcode-cn.com/problems/er-cha-sou-suo-shu-yu-shuang-xiang-lian-biao-lcof/)

> 思路

使用中序遍历加递归

> 代码

```js
/**
 * // Definition for a Node.
 * function Node(val,left,right) {
 *    this.val = val;
 *    this.left = left;
 *    this.right = right;
 * };
 */
/**
 * @param {Node} root
 * @return {Node}
 */
var treeToDoublyList = function(root) {
    if (!root) {
        return;
    }
    let head = null;
    let pre = head;
    inorder(root);
    head.left = pre;
    pre.right = head;
    return head;
    
    function inorder(node) {
        if (!node) return;
        inorder(node.left, pre);

        if (!pre) {
            head = node;
        } else {
            pre.right = node;
        }
        node.left = pre;
        pre = node;

        inorder(node.right, pre);
    }
};

```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(N)。

> 执行

执行用时：104 ms, 在所有 JavaScript 提交中击败了13.16%的用户

内存消耗：39.7 MB, 在所有 JavaScript 提交中击败了5.12%的用户