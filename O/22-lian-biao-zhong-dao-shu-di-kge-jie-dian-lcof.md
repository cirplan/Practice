### 剑指 Offer 22. 链表中倒数第k个节点

> 题目

[链接](https://leetcode-cn.com/problems/lian-biao-zhong-dao-shu-di-kge-jie-dian-lcof/)

> 思路

使用两个指针，第一个指针走了K步，则第二个指针指向第一位，当第一个指针走到终点，第二个指针则是第K个节点。

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
 * @param {number} k
 * @return {ListNode}
 */
var getKthFromEnd = function(head, k) {
    if (!head || !k) return null;
    const top = head;
    let p1 = 1;
    let p2;
    while (head) {
        head = head.next;
        if (p1 === k) {
            p2 = top;
        } else if (p2) {
            p2 = p2.next;
        }

        p1++;
    }

    return p2;
};
```

> 复杂度分析


时间复杂度：O(N)。

空间复杂度：O(1)。

> 执行

执行用时：88 ms, 在所有 JavaScript 提交中击败了58.00%的用户

内存消耗：39 MB, 在所有 JavaScript 提交中击败了90.93%的用户
