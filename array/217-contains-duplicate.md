### 217. 存在重复元素

> 题目

给定一个整数数组，判断是否存在重复元素。

如果存在一值在数组中出现至少两次，函数返回 true 。如果数组中每个元素都不相同，则返回 false 。

示例 1:
```
输入: [1,2,3,1]
输出: true
```

示例 2:
```
输入: [1,2,3,4]
输出: false
```

示例 3:
```
输入: [1,1,1,3,3,4,3,2,4,2]
输出: true
```

> 思路

使用哈希表，空间换时间。

> 代码

```js
/**
 * @param {number[]} nums
 * @return {boolean}
 */
var containsDuplicate = function (nums) {
    let cache = new Set();
    for (let i = 0; i < nums.length; i++) {
        const num = nums[i];
        if (cache.has(num)) {
            return true;
        }

        cache.add(num);
    }

    return false;
};
```

> 复杂度分析

时间复杂度：O(n)。

空间复杂度：O(n)。

> 执行

执行用时：88 ms, 在所有 JavaScript 提交中击败了79.79%的用户

内存消耗：43.4 MB, 在所有 JavaScript 提交中击败了68.38%的用户
