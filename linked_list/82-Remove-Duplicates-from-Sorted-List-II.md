### 82. 删除排序链表中的重复元素 II

> 题目

给定一个排序链表，删除所有含有重复数字的节点，只保留原始链表中 没有重复出现 的数字。

示例 1:
```
输入: 1->2->3->3->4->4->5
输出: 1->2->5
```

示例 2:
```
输入: 1->1->1->2->3
输出: 2->3
```

> 思路

使用辅助节点，判断当前节点是否与下一节点值重复。但要注意下下节点也可能重复。

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
 * @return {ListNode}
 */
var deleteDuplicates = function(head) {
    if (!head) return head;

    let firstNode = new ListNode();
    firstNode.next = head;

    let beforeNode = firstNode;
    while (head) {
        while (head && head.next && head.val === head.next.val) {
            let tempHead = head.next;
            while (tempHead.next && head.val === tempHead.next.val) {
                tempHead = tempHead.next;
            }

            head = tempHead.next;
        }
        
        beforeNode = beforeNode.next = head;
        head = head && head.next;
    }

    return firstNode.next;
};
```

> 复杂度分析

时间复杂度 : O(N)，只循环一次。

空间复杂度 : O(1)，常量级变量。

> 执行

执行用时：76 ms, 在所有 JavaScript 提交中击败了99.57%的用户.

内存消耗：39.2 MB, 在所有 JavaScript 提交中击败了27.15%的用户.

> 算法

