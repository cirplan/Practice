### 剑指 Offer 40. 最小的k个数

> 题目

[链接](https://leetcode-cn.com/problems/zui-xiao-de-kge-shu-lcof/)

> 思路

先排序，取前面的K个数。

> 代码

```js
/**
 * @param {number[]} arr
 * @param {number} k
 * @return {number[]}
 */
var getLeastNumbers = function (arr, k) {
    if (k === 0) return [];
    arr.sort((a, b) => a - b);
    return arr.slice(0, k);
};
```

> 复杂度分析

时间复杂度：O(nlogn)。

空间复杂度：O(logn)。

> 执行

执行用时：140 ms, 在所有 JavaScript 提交中击败了36.98%的用户

内存消耗：42.4 MB, 在所有 JavaScript 提交中击败了44.72%的用户