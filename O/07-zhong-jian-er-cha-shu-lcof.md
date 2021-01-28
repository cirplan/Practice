### 剑指 Offer 07. 重建二叉树

> 题目

输入某二叉树的前序遍历和中序遍历的结果，请重建该二叉树。假设输入的前序遍历和中序遍历的结果中都不含重复的数字。

例如，给出
```
前序遍历 preorder = [3,9,20,15,7]
中序遍历 inorder = [9,3,15,20,7]
返回如下的二叉树：

    3
   / \
  9  20
    /  \
   15   7
```

限制：

0 <= 节点个数 <= 5000

> 思路

前序第一个点是根节点，在中序里，根节点前的是左节点，根节点右边的为右节点。如此递归即可。

> 代码

```js
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {number[]} preorder
 * @param {number[]} inorder
 * @return {TreeNode}
 */
var buildTree = function (preorder, inorder) {
    if (!preorder.length) {
        return null;
    }

    const rootVal = preorder[0];
    const node = new TreeNode(rootVal);

    let i = 0;
    for (; i < inorder.length; ++i) {
        if (inorder[i] === rootVal) {
            break;
        }
    }

    node.left = buildTree(preorder.slice(1, i + 1), inorder.slice(0, i));
    node.right = buildTree(preorder.slice(i + 1), inorder.slice(i + 1));
    return node;
};
```

> 复杂度分析

时间复杂度 : O(n)。

空间复杂度 : O(n)。

> 执行

执行用时：204 ms, 在所有 JavaScript 提交中击败了30.74%的用户

内存消耗：110.8 MB, 在所有 JavaScript 提交中击败了14.90%的用户
