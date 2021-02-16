### 剑指 Offer 33. 二叉搜索树的后序遍历序列

> 题目

[链接](https://leetcode-cn.com/problems/er-cha-sou-suo-shu-de-hou-xu-bian-li-xu-lie-lcof/)

> 思路

使用递归即可。

> 代码

```js
/**
 * @param {number[]} postorder
 * @return {boolean}
 */
var verifyPostorder = function (postorder) {
    if (!postorder.length) return true;

    const root = postorder[postorder.length - 1];
    let i = 0;
    while (i < postorder.length - 1 && postorder[i] < root) {
        i++;
    }

    const left = postorder.slice(0, i);
    const right = postorder.slice(i, postorder.length - 1);
    for (let i = 0; i < right.length; i++) {
        if (right[i] < root) {
            return false;
        }
    }

    let leftValid = true;
    if (left.length) {
        leftValid = verifyPostorder(left);
    }

    let rightValid = true;
    if (right.length) {
        rightValid = verifyPostorder(right);
    }

    return leftValid && rightValid;
};
```

> 复杂度分析

时间复杂度：O(N ^ 2)。

空间复杂度：O(N)。

> 执行


执行用时：88 ms, 在所有 JavaScript 提交中击败了40.39%的用户

内存消耗：39.3 MB, 在所有 JavaScript 提交中击败了33.87%的用户