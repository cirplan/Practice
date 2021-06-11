### 523. 连续的子数组和

> 题目

[链接](https://leetcode-cn.com/problems/continuous-subarray-sum/)

> 思路

哈希表

> 代码

```js
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {boolean}
 */
var checkSubarraySum = function (nums, k) {
    const m = nums.length;
    if (m < 2) {
        return false;
    }
    const map = new Map();
    map.set(0, -1);
    let remainder = 0;
    for (let i = 0; i < m; i++) {
        remainder = (remainder + nums[i]) % k;
        if (map.has(remainder)) {
            const prevIndex = map.get(remainder);
            if (i - prevIndex >= 2) {
                return true;
            }
        } else {
            map.set(remainder, i);
        }
    }
    return false;
};
```

> 复杂度分析

时间复杂度：O(m)。其中 m 是数组 nums 的长度。

空间复杂度：O(min(m,k))。其中 m 是数组 nums 的长度。

> 执行

执行用时：168 ms, 在所有 JavaScript 提交中击败了13.20%的用户

内存消耗：53.5 MB, 在所有 JavaScript 提交中击败了39.25%的用户