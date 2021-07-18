### 414. 第三大的数

> 题目

[链接](https://leetcode-cn.com/problems/third-maximum-number/)

> 思路

排序取第三

> 代码

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var thirdMax = function (nums) {
    if (nums.length < 3) return Math.max(...nums)
    let a = [...new Set([...nums])].sort((a, b) => a - b)
    return a.length < 3 ? Math.max(...a) : a[a.length - 3]
};
```

> 复杂度分析

时间复杂度：O(logn)。

空间复杂度：O(n)。

> 执行

执行用时：64 ms, 在所有 JavaScript 提交中击败了99.68%的用户

内存消耗：39.4 MB, 在所有 JavaScript 提交中击败了61.24%的用户
