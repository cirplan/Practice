### 24. 两两交换链表中的节点

> 题目

[链接](https://leetcode-cn.com/problems/swap-nodes-in-pairs/)

> 思路

递归

> 代码

```js
/**
 * Definition for singly-linked list.
 * function ListNode(val, next) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.next = (next===undefined ? null : next)
 * }
 */
/**
 * @param {ListNode} head
 * @return {ListNode}
 */
var swapPairs = function (head) {
    if (head === null || head.next === null) {
        return head;
    }
    const newHead = head.next;
    head.next = swapPairs(newHead.next);
    newHead.next = head;
    return newHead;
};
```

> 复杂度分析

时间复杂度：O(n)。

空间复杂度：O(n)。

> 执行

执行用时：84 ms, 在所有 JavaScript 提交中击败了64.65%的用户

内存消耗：38.2 MB, 在所有 JavaScript 提交中击败了21.57%的用户
