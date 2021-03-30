### 206. 反转链表

> 题目

[链接](https://leetcode-cn.com/problems/reverse-linked-list/)

> 思路

使用迭代，把当前节点指向前一个节点

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
var reverseList = function(head) {
    if (!head) return null;
    let prevNode = null;

    while (head) {
        let nextNode = head.next;
        head.next = prevNode;
        prevNode = head;
        head = nextNode;
    }

    return prevNode;
};
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(1)。

> 执行

执行用时：88 ms, 在所有 JavaScript 提交中击败了68.53%的用户

内存消耗：39.4 MB, 在所有 JavaScript 提交中击败了93.23%的用户
