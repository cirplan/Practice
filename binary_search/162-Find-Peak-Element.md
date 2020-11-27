### 162. 寻找峰值

> 题目

峰值元素是指其值大于左右相邻值的元素。

给定一个输入数组 nums，其中 nums[i] ≠ nums[i+1]，找到峰值元素并返回其索引。

数组可能包含多个峰值，在这种情况下，返回任何一个峰值所在位置即可。

你可以假设 nums[-1] = nums[n] = -∞。

示例 1:
```
输入: nums = [1,2,3,1]
输出: 2
解释: 3 是峰值元素，你的函数应该返回其索引 2。
```

示例 2:
```
输入: nums = [1,2,1,3,5,6,4]
输出: 1 或 5 
解释: 你的函数可以返回索引 1，其峰值元素为 2；
     或者返回索引 5， 其峰值元素为 6。
```

说明:

你的解法应该是 O(logN) 时间复杂度的。

> 思路

寻找峰值，可能有多个，只有输出其中一个。时间复杂度是 O(logN)，直接用二分法就行。要注意在头和尾只需要判断一个方向就行。在中间的只需要判断一个方向的就好。

> 代码

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var findPeakElement = function(nums) {
    let n = nums.length;
    let l = 0, r = n - 1;
    while (l <= n) {
        let mid = l + Math.floor((r - l) / 2);
        let left = nums[mid - 1], right = nums[mid + 1];
        if (left === undefined) { left = -Infinity; }
        if (right === undefined) { right = -Infinity; }
        if (nums[mid] > left && nums[mid] > right) {
            return mid;
        }
        if (nums[mid] < left) {
            r = mid - 1;
        }
        else {
            l = mid + 1;
        }
    }
    return NaN;
};
```

> 复杂度分析

时间复杂度：O(logN)。

空间复杂度：O(1)。

> 执行

执行用时：80 ms, 在所有 JavaScript 提交中击败了76.57%的用户

内存消耗：38 MB, 在所有 JavaScript 提交中击败了24.76%的用户

> 算法

二分法