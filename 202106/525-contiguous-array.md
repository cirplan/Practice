### 525. 连续数组

> 题目

[链接](https://leetcode-cn.com/problems/contiguous-array/)

> 思路

前序和 + 哈希表

> 代码

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var findMaxLength = function (nums) {
    let maxLength = 0;
    const map = new Map();
    let counter = 0;
    map.set(counter, -1);
    const n = nums.length;
    for (let i = 0; i < n; i++) {
        const num = nums[i];
        if (num == 1) {
            counter++;
        } else {
            counter--;
        }
        if (map.has(counter)) {
            const prevIndex = map.get(counter);
            maxLength = Math.max(maxLength, i - prevIndex);
        } else {
            map.set(counter, i);
        }
    }
    return maxLength;
};
```

> 复杂度分析

时间复杂度：O(n)。

空间复杂度：O(n)。

> 执行

执行用时：128 ms, 在所有 JavaScript 提交中击败了74.51%的用户

内存消耗：46.3 MB, 在所有 JavaScript 提交中击败了28.22%的用户
