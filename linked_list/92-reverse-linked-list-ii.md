### 92. 反转链表 II

> 题目

反转从位置 m 到 n 的链表。请使用一趟扫描完成反转。

说明:
1 ≤ m ≤ n ≤ 链表长度。

示例:
```
输入: 1->2->3->4->5->NULL, m = 2, n = 4
输出: 1->4->3->2->5->NULL
```

> 思路

反转链表，扫描的过程中记录好关键节点即可。关键节点如下：

* 节点[m - 1] ，可能 m 是1，则需要用辅助哨兵节点
* 节点[m]，此节点的 next 要指向节点[n + 1]
* 反转过程中，用两个节点辅助，prev 和 next。把 next 指向 prev，再往后移，`temp = next; prev = next; next = temp.next;`
* 最后节点[m - 1] 指向 prev ，节点[m] 指向 next

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
 * @param {number} m
 * @param {number} n
 * @return {ListNode}
 */
var reverseBetween = function(head, m, n) {
    let tempNode = new ListNode();
    tempNode.next = head;
    
    let beforeReverseeNode = tempNode;
    let step = 1;
    while (step < m) {
        beforeReverseeNode = beforeReverseeNode.next;
        step++;
    }

    if (m < n) {
        let changeFirstNode = beforeReverseeNode.next;
        let prevNode = changeFirstNode;
        let nextNode = prevNode.next;
        while (step < n) {
            let tempNode = nextNode.next;
            nextNode.next = prevNode;
            prevNode = nextNode;
            nextNode = tempNode;
            step++;
        }

        beforeReverseeNode.next = prevNode;
        changeFirstNode.next = nextNode;
    }

    return tempNode.next;
};
```

> 复杂度分析

时间复杂度 : O(N)。

空间复杂度 : O(1)。

> 执行

执行用时：84 ms, 在所有 JavaScript 提交中击败了67.95%的用户。

内存消耗：38 MB, 在所有 JavaScript 提交中击败了10.74%的用户。

> 算法

