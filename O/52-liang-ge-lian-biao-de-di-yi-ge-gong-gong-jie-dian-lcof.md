### 剑指 Offer 52. 两个链表的第一个公共节点

> 题目

[链接](https://leetcode-cn.com/problems/liang-ge-lian-biao-de-di-yi-ge-gong-gong-jie-dian-lcof/)

> 思路

分别从链表A，链表B出发，当A到尽头，就置为链表B；B到尽头，就置为A的起点，最后相遇的点就是第一个。

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
 * @param {ListNode} headA
 * @param {ListNode} headB
 * @return {ListNode}
 */
var getIntersectionNode = function (headA, headB) {
    let node1 = headA;
    let node2 = headB;

    while (node1 != node2) {
        node1 = node1 ? node1.next : headB;
        node2 = node2 ? node2.next : headA;
    }

    return node1
};
```

> 复杂度分析

时间复杂度：O(M+N)。

空间复杂度：O(1)。

> 执行

执行用时：120 ms, 在所有 JavaScript 提交中击败了47.95%的用户

内存消耗：45.2 MB, 在所有 JavaScript 提交中击败了49.13%的用户
