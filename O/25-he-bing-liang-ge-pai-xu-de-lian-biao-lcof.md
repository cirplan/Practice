### 剑指 Offer 25. 合并两个排序的链表

> 题目

[链接](https://leetcode-cn.com/problems/he-bing-liang-ge-pai-xu-de-lian-biao-lcof/)

> 思路

链表已排序，分别判断头节点就好。

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
 * @param {ListNode} l1
 * @param {ListNode} l2
 * @return {ListNode}
 */
var mergeTwoLists = function(l1, l2) {
    if (!l1 || !l2) {
        return l1 || l2;
    }

    let head = new ListNode();
    let top = head;
    while (l1 && l2) {
        if (l1.val < l2.val) {
            head.next = l1;
            l1 = l1.next;
        } else {
            head.next = l2;
            l2 = l2.next;
        }

        head = head.next;
    }

    if (!l1 && l2) {
        head.next = l2;
    } else {
        head.next = l1;
    }

    return top.next;
};
```

> 复杂度分析

时间复杂度：O(N)。N 为 l1，l2 中较短的链表长度。

空间复杂度：O(1)。

> 执行

执行用时：104 ms, 在所有 JavaScript 提交中击败了87.10%的用户

内存消耗：42.4 MB, 在所有 JavaScript 提交中击败了78.29%的用户
