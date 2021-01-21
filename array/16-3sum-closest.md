### 16. 最接近的三数之和

> 题目

给定一个包括 n 个整数的数组 nums 和 一个目标值 target。找出 nums 中的三个整数，使得它们的和与 target 最接近。返回这三个数的和。假定每组输入只存在唯一答案。

示例：
```
输入：nums = [-1,2,1,-4], target = 1
输出：2
解释：与 target 最接近的和是 2 (-1 + 2 + 1 = 2) 。
```

提示：

3 <= nums.length <= 10^3
-10^3 <= nums[i] <= 10^3
-10^4 <= target <= 10^4

> 思路

可以直接循环，暴力破解。但更优的方式是，先排序，再用双指针对比。

> 代码

```js
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number}
 */
var threeSumClosest = function (nums, target) {
  nums.sort((a, b) => a - b);
  let res = nums[0] + nums[1] + nums[nums.length - 1];

  for (let i = 0; i < nums.length - 2; i++) {
    const n1 = nums[i];
    let l = i + 1;
    let r = nums.length - 1;
    while (l < r) {
      const n2 = nums[l];
      const n3 = nums[r];
      const sum = n1 + n2 + n3;
      if (sum > target) {
        r--;
      } else {
        l++;
      }
      if (Math.abs(sum - target) < Math.abs(res - target)) {
        res = sum;
      }
    }
  }
  return res;
};
```

> 复杂度分析

时间复杂度：O(n ^ 2)。

空间复杂度：O(logn)。

> 执行

执行用时：84 ms, 在所有 JavaScript 提交中击败了95.90%的用户

内存消耗：39.7 MB, 在所有 JavaScript 提交中击败了24.96%的用户
