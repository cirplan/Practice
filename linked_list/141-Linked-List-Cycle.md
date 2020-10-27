### 41. 环形链表

> 题目

给定一个链表，判断链表中是否有环。

如果链表中有某个节点，可以通过连续跟踪 next 指针再次到达，则链表中存在环。 为了表示给定链表中的环，我们使用整数 pos 来表示链表尾连接到链表中的位置（索引从 0 开始）。 如果 pos 是 -1，则在该链表中没有环。注意：pos 不作为参数进行传递，仅仅是为了标识链表的实际情况。

如果链表中存在环，则返回 true 。 否则，返回 false 。

进阶：

你能用 O(1)（即，常量）内存解决此问题吗？

示例 1：
```
输入：head = [3,2,0,-4], pos = 1
输出：true
解释：链表中有一个环，其尾部连接到第二个节点。
```

示例 2：
```
输入：head = [1,2], pos = 0
输出：true
解释：链表中有一个环，其尾部连接到第一个节点。
```

示例 3：
```
输入：head = [1], pos = -1
输出：false
解释：链表中没有环。
```

提示：
链表中节点的数目范围是 [0, 104]
-105 <= Node.val <= 105
pos 为 -1 或者链表中的一个 有效索引 。

> 思路

经典循环链表，用快慢指针对比即可。慢指针每次走一步，快指针每次走两步。如果师环形，内部节点数肯定是偶数，必然会相遇。

也可以用哈希表，把每个访问过的节点缓存，再判断新节点是否在哈希表里。

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
 * @return {boolean}
 */
var hasCycle = function (head) {
    if (!head || !head.next) return false;

    let slow = head.next;
    let fast = head.next.next;
    while (slow && slow.next && fast && fast.next) {
        if (slow === fast) {
            return true;
        } else {
            slow = slow.next;
            fast = fast.next.next;
        }
    }

    return false;
};
```

> 复杂度分析

时间复杂度 : O(N)，其中 N 是链表中的节点数。当链表中存在环形时，快指针先进入循环。在环里，每移动一次，快和慢指针的距离减1。最坏的情况下，快和慢之间的距离是环的长度。

空间复杂度 : O(1)，只使用两个额外指针。


> 执行

执行用时：92 ms, 在所有 JavaScript 提交中击败了76.47%的用户。

内存消耗：39.8 MB, 在所有 JavaScript 提交中击败了52.54%的用户。

> 算法

