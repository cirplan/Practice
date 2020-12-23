### 117. 填充每个节点的下一个右侧节点指针 II

> 题目

给定一个二叉树

struct Node {
  int val;
  Node *left;
  Node *right;
  Node *next;
}
填充它的每个 next 指针，让这个指针指向其下一个右侧节点。如果找不到下一个右侧节点，则将 next 指针设置为 NULL。

初始状态下，所有 next 指针都被设置为 NULL。

进阶：

你只能使用常量级额外空间。
使用递归解题也符合要求，本题中递归程序占用的栈空间不算做额外的空间复杂度。

示例：

输入：root = [1,2,3,4,5,null,7]
输出：[1,#,2,3,#,4,5,7,#]
解释：给定二叉树如图 A 所示，你的函数应该填充它的每个 next 指针，以指向其下一个右侧节点，如图 B 所示。

提示：

树中的节点数小于 6000
-100 <= node.val <= 100

> 思路

??

> 代码

```js
/**
 * // Definition for a Node.
 * function Node(val, left, right, next) {
 *    this.val = val === undefined ? null : val;
 *    this.left = left === undefined ? null : left;
 *    this.right = right === undefined ? null : right;
 *    this.next = next === undefined ? null : next;
 * };
 */

/**
 * @param {Node} root
 * @return {Node}
 */
var connect = function (root) {
    let cur = root;
    while (cur !== null) {
        let dummy = new Node();
        let tail = dummy;
        while (cur != null) {
            if (cur.left !== null) {
                tail.next = cur.left;
                tail = tail.next;
            }
            if (cur.right !== null) {
                tail.next = cur.right;
                tail = tail.next;
            }
            cur = cur.next;
        }
        cur = dummy.next;
    }
    return root;
};
```

> 复杂度分析

时间复杂度 : O(N)。

空间复杂度 : O(1)。

> 执行

执行用时：116 ms, 在所有 JavaScript 提交中击败了48.56%的用户

内存消耗：42.6 MB, 在所有 JavaScript 提交中击败了40.09%的用户