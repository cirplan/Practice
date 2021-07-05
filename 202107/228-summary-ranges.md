### 228. 汇总区间

> 题目

[链接](https://leetcode-cn.com/problems/summary-ranges/)

> 思路

遍历

> 代码

```js
/**
 * @param {number[]} nums
 * @return {string[]}
 */
var summaryRanges = function (nums) {
    const ret = [];
    let i = 0;
    const n = nums.length;
    while (i < n) {
        const low = i;
        i++;
        while (i < n && nums[i] === nums[i - 1] + 1) {
            i++;
        }
        const high = i - 1;
        const temp = ['' + nums[low]];
        if (low < high) {
            temp.push('->');
            temp.push('' + nums[high]);
        }
        ret.push(temp.join(''));
    }
    return ret;
};
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(1)。

> 执行

执行用时：84 ms, 在所有 JavaScript 提交中击败了52.48%的用户

内存消耗：37.9 MB, 在所有 JavaScript 提交中击败了18.57%的用户