### 剑指 Offer 18. 删除链表的节点

> 题目

给定单向链表的头指针和一个要删除的节点的值，定义一个函数删除该节点。

返回删除后的链表的头节点。

注意：此题对比原题有改动

示例 1:
```
输入: head = [4,5,1,9], val = 5
输出: [4,1,9]
解释: 给定你链表中值为 5 的第二个节点，那么在调用了你的函数之后，该链表应变为 4 -> 1 -> 9.
```

示例 2:
```
输入: head = [4,5,1,9], val = 1
输出: [4,5,9]
解释: 给定你链表中值为 1 的第三个节点，那么在调用了你的函数之后，该链表应变为 4 -> 5 -> 9.
```

说明：

题目保证链表中节点的值互不相同
若使用 C 或 C++ 语言，你不需要 free 或 delete 被删除的节点

> 思路

使用辅助节点，删除即可。

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
 * @param {number} val
 * @return {ListNode}
 */
var deleteNode = function(head, val) {
    let tempNode = new ListNode();
    tempNode.next = head;
    let prevNode = tempNode;

    while (head.val !== val) {
        prevNode = head;
        head = head.next;
    }

    prevNode.next = head.next;
    return tempNode.next;
};
```

> 复杂度分析

时间复杂度 : O(n)。

空间复杂度 : O(1)。

> 执行

执行用时：84 ms, 在所有 JavaScript 提交中击败了94.61%的用户

内存消耗：39.7 MB, 在所有 JavaScript 提交中击败了38.68%的用户
