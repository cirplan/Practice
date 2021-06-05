### 203. 移除链表元素

> 题目

[链接](https://leetcode-cn.com/problems/remove-linked-list-elements/)

> 思路

循环

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
 * @param {number} val
 * @return {ListNode}
 */
var removeElements = function (head, val) {
    let first = new ListNode();
    let firstCopy = first;
    while (head) {
        if (head.val !== val) {
            first = first.next = new ListNode(head.val);
        }

        head = head.next;
    }

    return firstCopy.next;
};
```

> 复杂度分析

时间复杂度：O(n)。

空间复杂度：O(n)。

> 执行

行用时：96 ms, 在所有 JavaScript 提交中击败了93.13%的用户

内存消耗：42.2 MB, 在所有 JavaScript 提交中击败了83.42%的用户

