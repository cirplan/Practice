### 33. 搜索旋转排序数组

> 题目

升序排列的整数数组 nums 在预先未知的某个点上进行了旋转（例如， [0,1,2,4,5,6,7] 经旋转后可能变为 [4,5,6,7,0,1,2] ）。

请你在数组中搜索 target ，如果数组中存在这个目标值，则返回它的索引，否则返回 -1 。

示例 1：
```
输入：nums = [4,5,6,7,0,1,2], target = 0
输出：4
```

示例 2：
```
输入：nums = [4,5,6,7,0,1,2], target = 3
输出：-1
```

示例 3：
```
输入：nums = [1], target = 0
输出：-1
```
 
提示：

1 <= nums.length <= 5000
-10^4 <= nums[i] <= 10^4
nums 中的每个值都 独一无二
nums 肯定会在某个点上旋转
-10^4 <= target <= 10^4

> 思路

要注意是排序的数组，然后肯定翻转一次。所以可以用二分法逼近。

先取 mid，当 mid > target， right > mid，则在左侧找。若 mid < target，left < mid，则在右侧找。

> 代码

```js
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number}
 */
var search = function (nums, target) {
    let left = 0;
    let right = nums.length - 1;

    while (left <= right) {
        const mid = left + Math.floor((right - left) / 2);
        
        if (nums[mid] === target) {
            return mid;
        } else if (nums[mid] > target) {
            if (nums[right] > nums[mid]) {
                right = mid - 1;
            } else {
                if (nums[right] === target) {
                    return right;
                } else {
                    right--;
                }
            }
        } else {
            if (nums[left] < nums[mid]) {
                left = mid + 1;
            } else {
                if (nums[left] === target) {
                    return left;
                } else {
                    left++;
                }
            }
        }
    }

    return -1;
};
```

> 复杂度分析

时间复杂度：O(n)。最坏情况下为

空间复杂度：O(1)。

> 执行

执行用时：76 ms, 在所有 JavaScript 提交中击败了93.51%的用户

内存消耗：38.9 MB, 在所有 JavaScript 提交中击败了58.57%的用户