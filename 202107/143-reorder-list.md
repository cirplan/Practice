### 143. 重排链表

> 题目

[链接](https://leetcode-cn.com/problems/reorder-list/)

> 思路

找到中点，反转后半部分，再合并

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
 * @return {void} Do not return anything, modify head in-place instead.
 */
var reorderList = function (head) {
    const dummy = new ListNode(0)
    dummy.next = head

    let slow = dummy
    let quick = dummy

    while (quick && quick.next) {
        slow = slow.next
        quick = quick.next.next;
    }

    let right = slow.next
    slow.next = null
    let left = dummy.next

    right = reverseList(right)

    while (left && right) {
        let lNext = left.next
        let rNext = right.next
        right.next = left.next
        left.next = right
        left = lNext
        right = rNext
    }

    return dummy.next
}

var reverseList = (list) => {
    let prev = null
    let cur = list

    while (cur) {
        let next = cur.next
        cur.next = prev

        prev = cur
        cur = next
    }

    return prev
}

```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(N)。

> 执行

执行用时：96 ms, 在所有 JavaScript 提交中击败了99.08%的用户

内存消耗：46 MB, 在所有 JavaScript 提交中击败了24.31%的用户
