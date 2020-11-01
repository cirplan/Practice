### 142. 环形链表 II

> 题目

给定一个链表，返回链表开始入环的第一个节点。 如果链表无环，则返回 null。

为了表示给定链表中的环，我们使用整数 pos 来表示链表尾连接到链表中的位置（索引从 0 开始）。 如果 pos 是 -1，则在该链表中没有环。注意，pos 仅仅是用于标识环的情况，并不会作为参数传递到函数中。

说明：不允许修改给定的链表。

进阶：

你是否可以使用 O(1) 空间解决此题？

示例 1：
```
输入：head = [3,2,0,-4], pos = 1
输出：返回索引为 1 的链表节点
解释：链表中有一个环，其尾部连接到第二个节点。
```

示例 2：
```
输入：head = [1,2], pos = 0
输出：返回索引为 0 的链表节点
解释：链表中有一个环，其尾部连接到第一个节点。
```

示例 3：
```
输入：head = [1], pos = -1
输出：返回 null
解释：链表中没有环。
```

提示：

链表中节点的数目范围在范围 [0, 104] 内
-105 <= Node.val <= 105
pos 的值为 -1 或者链表中的一个有效索引

> 思路

第一想法是用Set，轻松解决。但这样没啥算法技巧，也达不到 O(1) 空间。所以要通过推导公式。

设置快慢两个指针，慢指针每次走一步，快指针每次走两步。当快慢两个指针相遇时，代表这是一个环形链表。

当相遇的时候，把链表起点到入环的距离记为a，入环到相遇点的距离为b，相遇点到入环的距离为c，所以可以算出快指针走的距离：`a + (b + c)n + b = a + (n + 1)b + nc`。

由于快指针走的距离肯定是慢指针的两倍，所以 `2(a + b) = a + (n + 1)b + nc`，即：`a = c + (n - 1)(b + c)`。

所以当快慢指针相遇，从起点设置辅助指针，每次走一步，慢指针也每次走一步，最后会在入环处相遇。

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
var detectCycle = function (head) {
    if (!head) return head;

    let slow = head;
    let fast = head;

    while (fast && fast.next) {
        slow = slow.next;
        fast = fast.next.next;

        if (slow === fast) {
            while (head !== slow) {
                head = head.next;
                slow = slow.next;
            }
            return head;
        }
    }

    return null;
};
```

> 复杂度分析

时间复杂度 : O(N)。

空间复杂度 : O(1)。

> 执行

执行用时：100 ms, 在所有 JavaScript 提交中击败了56.51%的用户。

内存消耗：40.5 MB, 在所有 JavaScript 提交中击败了15.55%的用户。

> 算法

