### 剑指 Offer 24. 反转链表

> 题目

[链接](https://leetcode-cn.com/problems/fan-zhuan-lian-biao-lcof/)

> 思路

使用两个指针，分别指向前一个节点和后一个节点。

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
 * @param {ListNode} head
 * @return {ListNode}
 */
var reverseList = function (head) {
    if (!head) return null;

    let prev = null;
    let next = null;

    while (head) {
        next = head.next;
        head.next = prev;
        prev = head;
        head = next;
    }

    return prev;
};
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(1)。

> 执行

执行用时：88 ms, 在所有 JavaScript 提交中击败了65.12%的用户

内存消耗：39.8 MB, 在所有 JavaScript 提交中击败了23.41%的用户
