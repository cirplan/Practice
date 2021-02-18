### 剑指 Offer 35. 复杂链表的复制

> 题目

[链接](https://leetcode-cn.com/problems/fu-za-lian-biao-de-fu-zhi-lcof/)

> 思路

使用Map，匹配random

> 代码

```js
/**
 * // Definition for a Node.
 * function Node(val, next, random) {
 *    this.val = val;
 *    this.next = next;
 *    this.random = random;
 * };
 */

/**
 * @param {Node} head
 * @return {Node}
 */
var copyRandomList = function(head) {
    if (!head) return null;

    let headTop = new Node();
    headTop.next = head;
    
    let headMap = new Map();
    while (head) {
        headMap.set(head, new Node(head.val));
        head = head.next;
    }

    head = headTop.next;
    let copyHead = new Node();
    let copyHeadTop = copyHead;
    while (head) {
        copyHead.next = headMap.get(head);
        copyHead.next.random = headMap.get(head.random);
        head = head.next;
        copyHead = copyHead.next;
    }

    return copyHeadTop.next;
};
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(N)。

> 执行

执行用时：84 ms, 在所有 JavaScript 提交中击败了70.02%的用户

内存消耗：39.3 MB, 在所有 JavaScript 提交中击败了51.30%的用户
