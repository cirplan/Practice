### 350. 两个数组的交集 II

> 题目

[链接](https://leetcode-cn.com/problems/intersection-of-two-arrays-ii/)

> 思路

可以暴力，也可以先排序再用双指针对比

> 代码

```js
/**
 * @param {number[]} nums1
 * @param {number[]} nums2
 * @return {number[]}
 */
var intersect = function (nums1, nums2) {
    nums1.sort((a, b) => a - b);
    nums2.sort((a, b) => a - b);
    let l = 0, r = 0, ans = [];
    while (l < nums1.length && r < nums2.length) {
        if (nums1[l] === nums2[r]) {
            ans.push(nums1[l]);
            l++;
            r++;
        } else nums1[l] < nums2[r] ? l++ : r++;
    }
    return ans;
};
```

> 复杂度分析

时间复杂度：O(nlogn)。

空间复杂度：O(1)。

> 执行

执行用时：84 ms, 在所有 JavaScript 提交中击败了85.56%的用户

内存消耗：39.8 MB, 在所有 JavaScript 提交中击败了32.96%的用户
