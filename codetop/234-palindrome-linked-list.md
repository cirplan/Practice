### 234. 回文链表

> 题目

[链接](https://leetcode-cn.com/problems/palindrome-linked-list/)

> 思路

使用数组存储对比

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
 * @return {boolean}
 */
var isPalindrome = function(head) {
    let arr = [];
    while (head) {
        arr.push(head.val);
        head = head.next;
    }
    
    return arr.toString() === arr.reverse().toString();
};
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(N)。

> 执行

执行用时：304 ms, 在所有 JavaScript 提交中击败了11.53%的用户

内存消耗：70 MB, 在所有 JavaScript 提交中击败了9.66%的用户
