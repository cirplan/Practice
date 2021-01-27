### 剑指 Offer 06. 从尾到头打印链表

> 题目

输入一个链表的头节点，从尾到头反过来返回每个节点的值（用数组返回）。

示例 1：
```
输入：head = [1,3,2]
输出：[2,3,1]
```

限制：

0 <= 链表长度 <= 10000

> 思路

使用栈的特性，先进后出。也可以用递归。

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
 * @return {number[]}
 */
var reversePrint = function(head) {
    let stack = [];

    while (head) {
        stack.push(head.val);
        head = head.next;
    }

    return stack.reverse();
};
```


> 复杂度分析

时间复杂度 : O(n)。

空间复杂度 : O(n)。

> 执行

执行用时：80 ms, 在所有 JavaScript 提交中击败了98.47%的用户

内存消耗：40 MB, 在所有 JavaScript 提交中击败了34.13%的用户