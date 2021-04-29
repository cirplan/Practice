### 448. 找到所有数组中消失的数字

> 题目

[链接](https://leetcode-cn.com/problems/find-all-numbers-disappeared-in-an-array/)

> 思路

使用nums作为记录

> 代码

```js
/**
 * @param {number[]} nums
 * @return {number[]}
 */
var findDisappearedNumbers = function(nums) {
 const n = nums.length;
    for (const num of nums) {
        const x = (num - 1) % n;
        nums[x] += n;
    }
    const ret = [];
    for (const [i, num] of nums.entries()) {
        if (num <= n) {
            ret.push(i + 1);
        }
    }
    return ret;
};
```

> 复杂度分析

时间复杂度：O(n)。

空间复杂度：O(1)。

> 执行

执行用时：148 ms, 在所有 JavaScript 提交中击败了46.01%的用户

内存消耗：49.2 MB, 在所有 JavaScript 提交中击败了16.21%的用户
