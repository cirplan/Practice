### 88. 合并两个有序数组

> 题目

给你两个有序整数数组 nums1 和 nums2，请你将 nums2 合并到 nums1 中，使 nums1 成为一个有序数组。

初始化 nums1 和 nums2 的元素数量分别为 m 和 n 。你可以假设 nums1 有足够的空间（空间大小等于 m + n）来保存 nums2 中的元素。

示例 1：
```
输入：nums1 = [1,2,3,0,0,0], m = 3, nums2 = [2,5,6], n = 3
输出：[1,2,2,3,5,6]
```

示例 2：
```
输入：nums1 = [1], m = 1, nums2 = [], n = 0
输出：[1]
```

提示：

0 <= m, n <= 200
1 <= m + n <= 200
nums1.length == m + n
nums2.length == n
-109 <= nums1[i], nums2[i] <= 109

> 思路

从后往前取值排序，但要注意 nums1 的排完序后，要把 num2 还没排的合并过来。

> 代码

```js
/**
 * @param {number[]} nums1
 * @param {number} m
 * @param {number[]} nums2
 * @param {number} n
 * @return {void} Do not return anything, modify nums1 in-place instead.
 */
var merge = function(nums1, m, nums2, n) {
    let len1 = m - 1;
    let len2 = n - 1;
    let len = m + n - 1;
    while(len1 >= 0 && len2 >= 0) {
        nums1[len--] = nums1[len1] > nums2[len2] ? nums1[len1--] : nums2[len2--];
    }

    if (len2 >= 0) {
        nums1.splice(0, len2 + 1, ...nums2.slice(0, len2 + 1));
    }
};
```

> 复杂度分析

时间复杂度：O(n + m)。

空间复杂度：O(1)。

> 执行

执行用时：76 ms, 在所有 JavaScript 提交中击败了91.87%的用户

内存消耗：37.7 MB, 在所有 JavaScript 提交中击败了85.49%的用户
