### 220. 存在重复元素 III

> 题目

在整数数组 nums 中，是否存在两个下标 i 和 j，使得 nums [i] 和 nums [j] 的差的绝对值小于等于 t ，且满足 i 和 j 的差的绝对值也小于等于 ķ 。

如果存在则返回 true，不存在返回 false。

示例 1:
```
输入: nums = [1,2,3,1], k = 3, t = 0
输出: true
```

示例 2:
```
输入: nums = [1,0,1,1], k = 1, t = 2
输出: true
```

示例 3:
```
输入: nums = [1,5,9,1,5,9], k = 2, t = 3
输出: false
```

> 思路

暴力破解

> 代码

```js
/**
 * @param {number[]} nums
 * @param {number} k
 * @param {number} t
 * @return {boolean}
 */
var containsNearbyAlmostDuplicate = function (nums, k, t) {
    const len = nums.length;
    for (let i = 0; i < len; i++) {
        for (let j = i + 1; j < Math.min(len, i + k + 1); j++) {
            if (Math.abs(nums[i] - nums[j]) <= t) {
                return true;
            }
        }
    }

    return false;
};
```

> 复杂度分析

时间复杂度：双重循环，为O(nmin(k,n))。

空间复杂度：O(1)。

> 执行

执行用时：884 ms, 在所有 JavaScript 提交中击败了25.54%的用户

内存消耗：38.5 MB, 在所有 JavaScript 提交中击败了68.44%的用户