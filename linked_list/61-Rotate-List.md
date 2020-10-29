### 61. 旋转链表

> 题目

给定一个链表，旋转链表，将链表每个节点向右移动 k 个位置，其中 k 是非负数。

示例 1:
```
输入: 1->2->3->4->5->NULL, k = 2
输出: 4->5->1->2->3->NULL
解释:
向右旋转 1 步: 5->1->2->3->4->NULL
向右旋转 2 步: 4->5->1->2->3->NULL
```

示例 2:
```
输入: 0->1->2->NULL, k = 4
输出: 2->0->1->NULL
解释:
向右旋转 1 步: 2->0->1->NULL
向右旋转 2 步: 1->2->0->NULL
向右旋转 3 步: 0->1->2->NULL
向右旋转 4 步: 2->0->1->NULL
```

> 思路

向右移 K 步，我们观察得知，当 K < N，我们只需要把节点 [N - K] 找出，此节点 next 指向 null；节点[N] 的 next 指向节点[1]即可。

其中 k 存在大于 N 的情况，先找出N的长度，再 K % N 就可以知道实际偏移量。

其中要注意边界，辅助节点的使用。

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
var rotateRight = function(head, k) {
    if (!head || k === 0) return head;
    let tempNode = new ListNode();
    tempNode.next = head;

    let len = 0;
    let temp = head;
    let firstNode = head;
    let lastNode;
    while(temp) {
        len++;
        lastNode = temp;
        temp = temp.next;
    }
    
    let step = k % len;
    if (step === 0) return head;
    step = len - step;
    let count = 1;
    while(count < step) {
        head = head.next;
        count++;
    }

    tempNode.next = head.next;
    head.next = null;
    lastNode.next = firstNode;

    return tempNode.next;
};
```

> 复杂度分析

时间复杂度 : O(N)。

空间复杂度 : O(1)。

> 执行

执行用时：96 ms, 在所有 JavaScript 提交中击败了75.12%的用户。

内存消耗：39.5 MB, 在所有 JavaScript 提交中击败了18.66%的用户。

> 算法

