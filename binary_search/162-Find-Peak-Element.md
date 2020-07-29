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
var findPeakElement = function (nums) {
  if (!nums.length) return -1;
  else if (nums.length === 1) return 0;

  let low = 0;
  let height = nums.length - 1;

  while (low <= height) {
    const pos =
      low + Math.floor((height - low) / 2);
    const val = nums[pos];

    if (pos === 0) {
      if (val > nums[pos + 1]) {
        return pos;
      } else {
        low = pos + 1;
      }
    } else if (pos === nums.length - 1) {
      if (val > nums[pos - 1]) {
        return pos;
      } else {
        height = height - 1;
      }
    } else {
      if (val > nums[pos - 1]) {
        // 峰值
        if (val > nums[pos + 1]) {
          return pos;
        } else {
          low = pos + 1;
        }
      } else {
        height = pos - 1;
      }
    }
  }
};
```

> 复杂度分析

时间复杂度：O(logN)。

空间复杂度：O(1)。

> 执行

执行用时：88 ms, 在所有 JavaScript 提交中击败了14.55%的用户。

内存消耗：37.7 MB, 在所有 JavaScript 提交中击败了12.50%的用户。

> 算法

二分法