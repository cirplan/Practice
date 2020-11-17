### 349. 两个数组的交集

> 题目

给定两个数组，编写一个函数来计算它们的交集。

示例 1：
```
输入：nums1 = [1,2,2,1], nums2 = [2,2]
输出：[2]
```

示例 2：
```
输入：nums1 = [4,9,5], nums2 = [9,4,9,8,4]
输出：[9,4]
```

说明：

输出结果中的每个元素一定是唯一的。
我们可以不考虑输出结果的顺序。

> 思路

使用哈希表，对数组1循环，并把值添加到哈希里面。然后对于数组2，分别判断是否在哈希表内，在则输出。其中每个值只记录一次。

> 代码

```js
/**
 * @param {number[]} nums1
 * @param {number[]} nums2
 * @return {number[]}
 */
var intersection = function(nums1, nums2) {
  let numsMap = {};
  for (let i = 0; i < nums1.length; i++) {
    const num = nums1[i];
    numsMap[num] = 1;
  }

  let result = [];
  for (let i = 0; i < nums2.length; i++) {
    const num = nums2[i];
    if (numsMap[num]) {
      numsMap[num]--;
      result.push(num);
    }
  }

  return result;
};
```

> 复杂度分析

时间复杂度：O(m + n)。m，n 分别是两个数组的长度。

空间复杂度：O(m)。

> 执行

执行用时：84 ms, 在所有 JavaScript 提交中击败了79.60%的用户

内存消耗：39.2 MB, 在所有 JavaScript 提交中击败了40.61%的用户
