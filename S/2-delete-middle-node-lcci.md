### 面试题 02.03. 删除中间节点

> 题目

[链接](https://leetcode-cn.com/problems/delete-middle-node-lcci/)

> 思路

往后删除一个即可

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
var deleteNode = function (node) {
    node.val = node.next.val;
    node.next = node.next.next;
};
```

> 复杂度分析

时间复杂度：O(1)。

空间复杂度：O(1)。

> 执行

执行用时：92 ms, 在所有 JavaScript 提交中击败了70.56%的用户

内存消耗：39.4 MB, 在所有 JavaScript 提交中击败了89.79%的用户
