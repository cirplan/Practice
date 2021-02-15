### 剑指 Offer 32 - I. 从上到下打印二叉树

> 题目

[链接](https://leetcode-cn.com/problems/cong-shang-dao-xia-da-yin-er-cha-shu-lcof/)

> 思路

使用辅助队列。

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
 * @param {TreeNode} root
 * @return {number[]}
 */
var levelOrder = function(root) {
    if (!root) return [];

    const data = [];
    const queue = [root];
    while (queue.length) {
        const first = queue.shift();
        data.push(first.val);
        first.left && queue.push(first.left);
        first.right && queue.push(first.right);
    }

    return data;
};
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(N)。


> 执行

执行用时：92 ms, 在所有 JavaScript 提交中击败了45.35%的用户

内存消耗：39.4 MB, 在所有 JavaScript 提交中击败了84.63%的用户