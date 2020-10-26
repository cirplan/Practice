### 83. 删除排序链表中的重复元素

> 题目

给定一个排序链表，删除所有重复的元素，使得每个元素只出现一次。

示例 1:
```
输入: 1->1->2
输出: 1->2
```

示例 2:
```
输入: 1->1->2->3->3
输出: 1->2->3
```

> 思路

链表，比较前后的元素值即可。但要注意边界的判断。

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
var deleteDuplicates = function (head) {
    if (!head || !head.next) return head;

    let tempList = new ListNode();
    tempList.next = head;

    while (head && head.next) {
        let tempNode = head;
        head = head.next;

        while (head && (tempNode.val === head.val)) {
            head = head.next;
        }

        tempNode.next = head;
    }

    return tempList.next;
};
```

> 复杂度分析

时间复杂度 : O(n)，需要循环遍历一次。

空间复杂度 : O(1)。

> 执行

执行用时：96 ms, 在所有 JavaScript 提交中击败了78.17%的用户。

内存消耗：39.7 MB, 在所有 JavaScript 提交中击败了9.89%的用户。

> 算法

