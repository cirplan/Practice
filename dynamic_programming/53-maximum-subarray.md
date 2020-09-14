### 53. 最大子序和

> 题目

给定一个整数数组 nums ，找到一个具有最大和的连续子数组（子数组最少包含一个元素），返回其最大和。

示例:
```
输入: [-2,1,-3,4,-1,2,1,-5,4]
输出: 6
解释: 连续子数组 [4,-1,2,1] 的和最大，为 6。
```

进阶:

如果你已经实现复杂度为 O(n) 的解法，尝试使用更为精妙的分治法求解。

> 思路

使用贪心算法，设置两个变量，当前和、最大和。对数组的每一项，比较当前项与当前和的大小，取最大为当前和。再判断当前和与最大和大小，取最大的最大和。

> 代码

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var maxSubArray = function(nums) {
    if (nums.length === 1) return nums[0];
    
    let prevSum = nums[0];
    let maxSum = prevSum;
    for (let i = 1; i < nums.length; i++) {
        const num = nums[i];
        if (prevSum < 0) {
            prevSum = num;
        } else {
            prevSum += num;
        }
        if (prevSum > maxSum) {
            maxSum = prevSum;
        }
    }

    return maxSum;
};
```

> 复杂度分析

时间复杂度：遍历一次，O(N)。

空间复杂度：O(1)。

> 执行

执行用时：84 ms, 在所有 JavaScript 提交中击败了72.10%的用户。

内存消耗：39.5 MB, 在所有 JavaScript 提交中击败了38.08%的用户。

> 算法

贪心

---

> 思路2:

也可以使用动态规划的方法，当前一个元素的值大于0，则加到当前元素，最后取数组的最大值。

> 代码2:

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var maxSubArray = function(nums) {
    if (nums.length === 1) {
        return nums[0];
    }
    for (let i = 1; i < nums.length; i++) {
        if (nums[i-1] > 0) {
            nums[i] = nums[i - 1] + nums[i];
        }
    }

    return Math.max.apply(null, nums);
};
```

> 复杂度分析

时间复杂度：遍历一次，O(N)。

空间复杂度：O(1)。

> 执行

执行用时：72 ms, 在所有 JavaScript 提交中击败了95.89%的用户。

内存消耗：39.3 MB, 在所有 JavaScript 提交中击败了44.34%的用户。

> 算法

动态规划