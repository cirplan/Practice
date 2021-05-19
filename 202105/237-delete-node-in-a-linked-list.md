### 237. 删除链表中的节点

> 题目

[链接](https://leetcode-cn.com/problems/delete-node-in-a-linked-list/)

> 思路

原地删除

> 代码

```js
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * @param {ListNode} node
 * @return {void} Do not return anything, modify node in-place instead.
 */
var deleteNode = function(node) {
    node.val = node.next.val;
    node.next = node.next.next;
};
```

> 复杂度分析

时间复杂度：O(1)。

空间复杂度：O(1)。

> 执行

执行用时：104 ms, 在所有 JavaScript 提交中击败了24.77%的用户

内存消耗：39.7 MB, 在所有 JavaScript 提交中击败了43.92%的用户
