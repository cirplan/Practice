### 116. 填充每个节点的下一个右侧节点指针

> 题目

给定一个 完美二叉树 ，其所有叶子节点都在同一层，每个父节点都有两个子节点。二叉树定义如下：

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

输入：root = [1,2,3,4,5,6,7]
输出：[1,#,2,3,#,4,5,6,7,#]
解释：给定二叉树如图 A 所示，你的函数应该填充它的每个 next 指针，以指向其下一个右侧节点，如图 B 所示。序列化的输出按层序遍历排列，同一层节点由 next 指针连接，'#' 标志着每一层的结束。

提示：

树中节点的数量少于 4096
-1000 <= node.val <= 1000

> 思路

因为是完全二叉树，左节点的 next 直接指向 右节点；右节点的 next 指向父节点 next 的左节点。如此递归即可。

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
    if (root === null) return root;

    if (root.left !== null) {
        root.left.next = root.right;
        root.right.next = root.next != null ? root.next.left : null;
        connect(root.left);
        connect(root.right);
    }

    return root;
};
```

> 复杂度分析

时间复杂度 : O(N)。N 为树的节点数。

空间复杂度 : O(1)。因为使用递归不算复杂度。

> 执行

执行用时：112 ms, 在所有 JavaScript 提交中击败了60.02%的用户

内存消耗：44 MB, 在所有 JavaScript 提交中击败了85.09%的用户

