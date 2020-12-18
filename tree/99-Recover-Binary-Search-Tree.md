### 99. 恢复二叉搜索树

> 题目

给你二叉搜索树的根节点 root ，该树中的两个节点被错误地交换。请在不改变其结构的情况下，恢复这棵树。

进阶：使用 O(n) 空间复杂度的解法很容易实现。你能想出一个只使用常数空间的解决方案吗？

示例 1：
```
输入：root = [1,3,null,null,2]
输出：[3,1,null,null,2]
解释：3 不能是 1 左孩子，因为 3 > 1 。交换 1 和 3 使二叉搜索树有效。
```

示例 2：
```
输入：root = [3,1,4,null,null,2]
输出：[2,1,4,null,null,3]
解释：2 不能在 3 的右子树中，因为 2 < 3 。交换 2 和 3 使二叉搜索树有效。
```
提示：

树上节点的数目在范围 [2, 1000] 内
-231 <= Node.val <= 231 - 1

> 思路

隐式中序遍历，只关心中序遍历的值序列中每个相邻的位置的大小关系是否满足条件，且错误交换后最多两个位置不满足条件。

> 代码

```js
/**
 * Definition for a binary tree node.
 * function TreeNode(val, left, right) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.left = (left===undefined ? null : left)
 *     this.right = (right===undefined ? null : right)
 * }
 */
/**
 * @param {TreeNode} root
 * @return {void} Do not return anything, modify root in-place instead.
 */

const swap = (x, y) => {
    const temp = x.val;
    x.val = y.val;
    y.val = temp;
}

var recoverTree = function (root) {
    const stack = [];
    let x = null;
    let y = null;
    let pred = null;

    while (stack.length || root !== null) {
        while (root !== null) {
            stack.push(root);
            root = root.left;
        }
        root = stack.pop();
        if (pred !== null && root.val < pred.val) {
            y = root;
            if (x === null) {
                x = pred;
            }
            else break;
        }
        pred = root;
        root = root.right;
    }
    swap(x, y);
};
```

> 复杂度分析

时间复杂度 : O(n)。

空间复杂度 : O(H)。H为树的高度。

> 执行

执行用时：184 ms, 在所有 JavaScript 提交中击败了34.09%的用户

内存消耗：46.7 MB, 在所有 JavaScript 提交中击败了74.81%的用户