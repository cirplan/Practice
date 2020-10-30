### 86. 分隔链表

> 题目

给定一个链表和一个特定值 x，对链表进行分隔，使得所有小于 x 的节点都在大于或等于 x 的节点之前。

你应当保留两个分区中每个节点的初始相对位置。

示例:
```
输入: head = 1->4->3->2->5->2, x = 3
输出: 1->2->2->4->3->5
```

> 思路

类似于一个数组里归类两组数，第一想法是直接用两个数组分别存储两类节点。然后再分别合并两个数组，但这样就需要循环两次。对于链表这种数据结构，能不能有更优的解法呢？有的，我们可以使用两个链表，然后只循环一次。

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
 * @param {number} x
 * @return {ListNode}
 */
var partition = function(head, x) {
    if (!head) return head;

    let beforeNode = new ListNode();
    let afterNode = new ListNode();
    let tempBefore = beforeNode;
    let tempAfter = afterNode;
    while (head) {
        if (head.val < x) {
            tempBefore = tempBefore.next = head;
        } else {
            tempAfter = tempAfter.next = head;
        }
        head = head.next;
    }

    tempBefore.next = afterNode.next;
    tempAfter.next = null;

    return beforeNode.next;
};
```

> 复杂度分析

时间复杂度 : O(N)，只循环一次。

空间复杂度 : O(1)，常量级变量。

> 执行

执行用时：84 ms, 在所有 JavaScript 提交中击败了90.25%的用户。

内存消耗：39 MB, 在所有 JavaScript 提交中击败了26.66%的用户。

> 算法

