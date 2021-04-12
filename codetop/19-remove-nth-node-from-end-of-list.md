### 19. 删除链表的倒数第 N 个结点

> 题目

[链接](https://leetcode-cn.com/problems/remove-nth-node-from-end-of-list/)

> 思路

使用快慢指针，当快指针比慢指针快N步，当快指针走到终点，慢指针则是倒数第N个点

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
 * @param {number} n
 * @return {ListNode}
 */
var removeNthFromEnd = function (head, n) {
    let headTop = new ListNode();
    headTop.next = head;

    let i = 1;
    while (i < n) {
        head = head.next;
        i++;
    }
    let headFirst = headTop;

    while (head && head.next) {
        head = head.next;
        headFirst = headFirst.next;
    }
    headFirst.next = headFirst.next.next;

    return headTop.next;
};
```

> 复杂度分析

时间复杂度：O(L)。L 是链表长度

空间复杂度：O(1)。

> 执行

执行用时：84 ms, 在所有 JavaScript 提交中击败了83.02%的用户

内存消耗：39.2 MB, 在所有 JavaScript 提交中击败了49.46%的用户
