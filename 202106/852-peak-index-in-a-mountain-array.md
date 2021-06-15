### 852. 山脉数组的峰顶索引

> 题目

[链接](https://leetcode-cn.com/problems/peak-index-in-a-mountain-array/)

> 思路

枚举或二分

> 代码

```js
/**
 * @param {number[]} arr
 * @return {number}
 */
var peakIndexInMountainArray = function(arr) {
    const n = arr.length;
    let ans = -1;

    for (let i = 1; i < n - 1; ++i) {
        if (arr[i] > arr[i + 1]) {
            ans = i;
            break;
        }
    }
    return ans;
};
```

> 复杂度分析

时间复杂度：O(n)。

空间复杂度：O(1)。

> 执行

执行用时：84 ms, 在所有 JavaScript 提交中击败了67.13%的用户

内存消耗：39 MB, 在所有 JavaScript 提交中击败了98.33%的用户
