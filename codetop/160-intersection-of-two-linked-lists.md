### 160. 相交链表

> 题目

[链接](https://leetcode-cn.com/problems/intersection-of-two-linked-lists/)

> 思路

使用双指针，当A走到终点，就指向B开头。当B走到终点，就指向A开头。如果相交，就会遇到。

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
    if (headA == null || headB == null) return null;
    let pA = headA;
    let pB = headB;
    while (pA != pB) {
        pA = pA == null ? headB : pA.next;
        pB = pB == null ? headA : pB.next;
    }
    return pA;
};
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(1)。

> 执行

执行用时：108 ms, 在所有 JavaScript 提交中击败了81.71%的用户

内存消耗：45 MB, 在所有 JavaScript 提交中击败了66.37%的用户
