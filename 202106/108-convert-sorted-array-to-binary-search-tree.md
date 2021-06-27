### 108. 将有序数组转换为二叉搜索树

> 题目

[链接](https://leetcode-cn.com/problems/convert-sorted-array-to-binary-search-tree/)

> 思路

中序遍历

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
 * @param {number[]} nums
 * @return {TreeNode}
 */
const buildBST = (nums, start, end) => {
    if (start > end) { 
        return null;
    }

    const midIndex = (start + end) >>> 1; 
    const root = new TreeNode(nums[midIndex]); 

    root.left = buildBST(nums, start, midIndex - 1); 
    root.right = buildBST(nums, midIndex + 1, end); 

    return root;
};

var sortedArrayToBST = function (nums) {
    return buildBST(nums, 0, nums.length - 1); // 递归的入口
};
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(N)。

> 执行

执行用时：92 ms, 在所有 JavaScript 提交中击败了89.02%的用户

内存消耗：40.3 MB, 在所有 JavaScript 提交中击败了50.71%的用户
