### 35. 搜索插入位置

> 题目

给定一个排序数组和一个目标值，在数组中找到目标值，并返回其索引。如果目标值不存在于数组中，返回它将会被按顺序插入的位置。

你可以假设数组中无重复元素。

示例 1:
```
输入: [1,3,5,6], 5
输出: 2
```

示例 2:
```
输入: [1,3,5,6], 2
输出: 1
```

示例 3:
```
输入: [1,3,5,6], 7
输出: 4
```

示例 4:
```
输入: [1,3,5,6], 0
输出: 0
```

> 思路

数组已经排序，暴力破解的方式则是直接对数组进行循环，拿每项和目标项相比较。但这样的时间复杂度是O(N)。

那有没有更高效的方法？有的，使用二分查找，但要注意查找不到要按顺序插入。

* 使用双指针，设置头 low 、尾 height 
* 当 low <= height 的时候执行循环
* 算出中心点 pos 下标，low + Math.floor((height - low) / 2)
* 判断中点项和目标项是否一致，是则直接返回中点。
* 如果中点项大于目标项，则 height = pos - 1
* 如果中点项小于目标项，则 low = pos + 1
* 最后返回 low，表示插入位置

> 代码

```js
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number}
 */
var searchInsert = function(nums, target) {
    // 针对nums 是空数组的情况
    if (!nums.length) return 0;

    let low = 0;
    let height = nums.length - 1;
    
    while (low <= height) {
        let pos = low + Math.floor((height - low) / 2);
        // 相等直接返回
        if (nums[pos] === target) {
            return pos;
        } else if (nums[pos] > target) {
            height = pos - 1;
        } else if (nums[pos] < target) {
            low = pos + 1;
        }
    }

    return low;
};
```

> 复杂度分析

时间复杂度 : O(logN)。

空间复杂度 : O(1)。

> 执行

执行用时：84 ms, 在所有 JavaScript 提交中击败了64.38%的用户

内存消耗：39 MB, 在所有 JavaScript 提交中击败了8.46%的用户
