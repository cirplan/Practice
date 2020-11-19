### 148. 排序链表

> 题目

给你链表的头结点 head ，请将其按 升序 排列并返回 排序后的链表 。

进阶：

你可以在 O(n log n) 时间复杂度和常数级空间复杂度下，对链表进行排序吗？

示例 1：
```
输入：head = [4,2,1,3]
输出：[1,2,3,4]
```

示例 2：
```
输入：head = [-1,5,3,4,0]
输出：[-1,0,3,4,5]
```

示例 3：
```
输入：head = []
输出：[]
```

提示：
链表中节点的数目在范围 [0, 5 * 104] 内
-105 <= Node.val <= 105

> 思路

第一想法是用冒泡，但这样时间复杂度是 N^2，测试用例通不过。这里可以采用归并排序，先找到中点，对两部分数据递归的排序。当最后只剩一个节点的时候，再合并。

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
var sortList = function (head) {
    if (!head || !head.next) return head;

    let slow = head;
    let fast = head.next;
    while (fast && fast.next) {
        slow = slow.next;
        fast = fast.next.next;
    }

    let middle = slow.next;
    slow.next = null;

    let leftNodes = sortList(head);
    let rightNodes = sortList(middle);
    let result = new ListNode();
    let res = result;
    while (leftNodes && rightNodes) {
        if (leftNodes.val < rightNodes.val) {
            result.next = leftNodes;
            leftNodes = leftNodes.next;
        } else {
            result.next = rightNodes;
            rightNodes = rightNodes.next;
        }

        result = result.next;
    }

    result.next = leftNodes ? leftNodes : rightNodes;
    return res.next;
};
```

> 复杂度分析

时间复杂度：O(nlogn)。

空间复杂度：O(N)。

> 执行

执行用时：188 ms, 在所有 JavaScript 提交中击败了19.17%的用户

内存消耗：53.3 MB, 在所有 JavaScript 提交中击败了21.97%的用户